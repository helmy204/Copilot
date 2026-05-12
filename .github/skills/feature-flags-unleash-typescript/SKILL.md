---
name: feature-flags-unleash-typescript
description: Feature flag patterns using Unleash. Use when adding, modifying, or testing feature flags, or when working with on-premise vs hosted feature differences.
---

# Feature Flags

This project uses Unleash for feature toggles in the hosted service. The
on-premise (Cockpit) build has no Unleash -- flags are resolved locally.

## Using Flags

Import `useFlag` from `@/Utilities/useGetEnvironment`:

```tsx
import { useFlag } from '@/Utilities/useGetEnvironment';

const isEnabled = useFlag('image-builder.my-feature');
```

`useFlag` is a **compile-time conditional export**:
- **Hosted build**: resolves to the real Unleash `useFlag` hook
- **Cockpit build**: resolves to `onPremFlag`, a local function that returns `false` by default

### Naming Convention

All flags use the `image-builder.` prefix with dot-separated names:

```
image-builder.service-unavailable
image-builder.layered-repos.enabled
```

## Ephemeral / QA Environments

Use `useFlagWithEphemDefault` when a flag should default to `true` in
QA/ephemeral environments where Unleash flags may not be configured:

```tsx
import { useFlagWithEphemDefault } from '@/Utilities/useGetEnvironment';

const isEnabled = useFlagWithEphemDefault('image-builder.my-feature');
// Returns true in QA environments (even if flag isn't set in Unleash)
// Returns the actual flag value in prod/stage
// Returns false on-premise
```

## On-Premise (Cockpit)

Unleash is not available on-premise. To enable a flag for the Cockpit build,
add a case to the `onPremFlag` switch statement in
`src/Utilities/useGetEnvironment.ts`:

```tsx
const onPremFlag = (flag: string): boolean => {
  switch (flag) {
    case 'image-builder.my-feature':
      return true;
    default:
      return false;
  }
};
```

Do not import directly from `@unleash/proxy-client-react` in components.
Always use the `useFlag` wrapper from `useGetEnvironment` so the on-premise
build path works correctly.

## Testing

Flags are mocked globally in `src/test/setup.ts`. All flags return `false`
by default. To enable a flag in the global mock, add a case to the switch
statement:

```tsx
vi.mock('@unleash/proxy-client-react', () => ({
  useUnleashContext: () => vi.fn(),
  useFlag: vi.fn((flag) => {
    switch (flag) {
      case 'image-builder.my-feature':
        return true;
      default:
        return false;
    }
  }),
}));
```

To override a flag per-test:

```tsx
import { useFlag } from '@/Utilities/useGetEnvironment';

vi.mocked(useFlag).mockReturnValue(true);
```

When a feature is behind a flag, test both the enabled and disabled code paths.
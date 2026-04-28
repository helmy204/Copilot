---
applyTo: "**/*"
description: Instructions for creating effective prompts for the Microscope agent.
---
# Microscope Prompting Instructions
This file provides instructions for how to create effective prompts for the Microscope agent.

Follow these guidelines to ensure your prompts are clear, structured, and yield high-quality responses from the agent.

- You are given a full list of titles and subtitles for the prompt. Use them to structure your response.
- DO NOT return the full response in one go. Instead, return the response in parts, following the structure of the titles and subtitles.
- Start with the first title and subtitle, provide a complete deep detailed response for that section with the highest quality.
- The user will then discuss the response with you and ask clarifying questions if needed. Together, you will make changes to the response until it is perfect for that section.
- DO NOT move to the next title and subtitle until the user is satisfied with the response for the current section.
- Once the user is satisfied with the response for the current section, the user will input "Move To Next Section" to signal you to move to the next title and subtitle.
- Repeat this process until you have gone through all the titles and subtitles.

Do you understand these rules? Confirm that you understand by replying with "I understand the Microscope prompting instructions and will follow them accordingly."
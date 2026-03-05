---
name: review-screenshot
description: Analyzes the latest screenshot from the Windows Screenshots directory (accessible via WSL) and answers questions about it in the context of the current session.
---

# Review Screenshot

This skill automatically finds and analyzes the most recent screenshot from your system's default screenshots directory, helping you review and understand visual content within the context of your current work.

## What This Skill Does

When you invoke this skill, it will:

1. **Detect your platform** (Windows, WSL, Linux, or macOS)
2. **Locate the latest screenshot** from the appropriate directory for your platform
3. **Load and analyze the image** to understand its visual content
4. **Answer questions about the screenshot** in the context of your current session
5. **Provide insights** about what's shown in the image

## How to Use This Skill

### Option 1: Using the Slash Command
```
/review screenshot
```

### Option 2: Calling as a Named Skill
```
skill: "review screenshot"
```

After invoking the skill, you can then ask questions about the screenshot, such as:
- "What's shown in this screenshot?"
- "Can you find the button labeled X?"
- "What errors or warnings are visible?"
- "Describe what you see in detail"

## Workflow

The skill executes the following process:

1. **Detect Platform**: Identifies the operating system and environment (Windows, WSL, Linux, or macOS)
2. **Locate Screenshot Directory**: Accesses the appropriate screenshots directory based on your platform:
   - **Windows**: `%USERPROFILE%\Pictures\Screenshots` (current user's screenshot folder)
   - **WSL**: `/mnt/c/Users/<username>/Pictures/Screenshots` (Windows user's screenshot directory via WSL mount)
   - **Linux**: `~/Pictures/Screenshots` or `~/.local/share/screenshots` (standard Linux screenshot locations)
   - **macOS**: Detects the configured screenshot location (typically `~/Desktop`, `~/Pictures`, or `~/Library/CloudStorage/...`)
3. **Find Latest File**: Scans the detected directory to identify the most recently modified image file
4. **Load Image**: Loads the latest screenshot into memory
5. **Analyze Content**: Examines the image to understand its visual elements
6. **Answer Questions**: Responds to your questions about the screenshot content, considering the context of your current session

## When to Use This Skill

Use this skill when you want to:
- Review the latest screenshot quickly without manual file navigation
- Get AI analysis of what's shown in your screenshots
- Ask questions about visual content in context
- Troubleshoot UI issues or visual problems
- Document or discuss what's displayed on your screen

## Example Interaction

```
User: /review-screenshot
User: What error messages are visible?

Copilot:
1. Locates the latest screenshot from your Screenshots folder
2. Loads and analyzes the image
3. Identifies any error messages visible in the screenshot
4. Describes the errors and their context
```

## Important Notes

- The skill automatically detects your operating system and environment (Windows, WSL, Linux, or macOS)
- It accesses the appropriate screenshot directory for your platform without requiring manual configuration
- For WSL, it correctly resolves Windows user paths via the `/mnt/c/` mount point
- For macOS, it detects your system's configured screenshot storage location
- For Linux, it checks standard screenshot directories (`~/Pictures/Screenshots`, `~/.local/share/screenshots`, etc.)
- File modification times are used to determine the "latest" screenshot
- The analysis respects your current session context when answering questions

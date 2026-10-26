---
name: open
description: Open a Markdown document in the graphical GPEditor alongside Claude Code.
argument-hint: "<path.md or path.markdown>"
---

Open $ARGUMENTS with gpdoc_open_editor using the exact authorized workspace path and surface preview in Claude Code Desktop, embedded in Codex. If no path is provided, ask which document to open. Open the returned previewUrl in Claude Desktop Preview using the available preview/browser capability. Do not edit the document merely to open it. Report unavailable preview support instead of claiming it opened. Claude native file-path clicks remain controlled by Claude.

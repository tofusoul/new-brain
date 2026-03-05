---
Type: Resource
tags: [resource, terminal, configuration, ghostty]
---

# Ghostty Configuration

**Last Updated:** 2025-09-27

## Overview
Configuration settings for Ghostty terminal emulator.

## Configuration File
Location: `~/.config/ghostty/config`

## Current Settings

```bash
theme = GruvboxDarkHard
cursor-style = bar
cursor-color = #ffe135  # Banana yellow
adjust-cursor-thickness = 3
window-padding-x = 10
window-padding-y = 0
command = zsh
font-family = Fira
```

## Configuration Details

### Cursor
- **Style:** Bar (beam-style cursor)
- **Color:** Banana yellow (#ffe135) - previously hot pink (#ff69b4)
- **Thickness:** 3px wide

### Window Padding
- **Horizontal:** 10px (left and right)
- **Vertical:** 0px (no top and bottom padding)

### Font
- **Family:** Fira

### Shell
- **Default:** zsh

### Theme
- **Current:** GruvboxDarkHard

## Notes
- All changes require restarting Ghostty to take effect
- Cursor is more visible with banana yellow color and increased thickness
- Balanced padding improves readability

## Related Notes
- [[Terminal]] - Terminal emulator alternatives
- [[kitty-terminal]] - Another terminal emulator option

---
*Last updated: 2025-02-01*

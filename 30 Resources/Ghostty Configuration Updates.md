# Ghostty Configuration Updates

**Date:** 2025-09-27

## Changes Made

Updated Ghostty terminal configuration with the following settings:

### Cursor Settings
- **Style:** Bar (beam-style cursor)
- **Color:** Hot pink (#ff69b4)
- **Thickness:** 3px wide
- **Updated to:** Banana yellow

### Window Padding
- **Horizontal:** 10px (left and right)
- **Vertical:** 0px (no top and bottom padding)

### Font
- **Changed to:** Fira

### Shell
- **Default shell:** zsh

## Configuration File
Location: `~/.config/ghostty/config`

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

## Notes
- All changes require restarting Ghostty to take effect
- Cursor is now more visible with banana yellow color and increased thickness
- Improved readability with Fira font and balanced padding
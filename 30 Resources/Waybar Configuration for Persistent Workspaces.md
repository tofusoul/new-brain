# Waybar Configuration for Persistent Workspaces

## Overview
Configure Waybar to show persistent workspaces 1-5 with dimmed empty workspaces, matching the monitor-specific workspace setup.

## Key Files
- `~/.config/waybar/config.jsonc` - Main configuration
- `~/.config/waybar/style.css` - CSS styling

## Implementation

### 1. Configure Workspaces Module
In `~/.config/waybar/config.jsonc`:

```json
"hyprland/workspaces": {
  "disable-scroll": true,
  "active-only": false,
  "all-output": false,
  "on-click": "activate",
  "format": "{icon}",
  "format-icons": {
    "default": "",
    "1": "1",
    "2": "2",
    "3": "3",
    "4": "4",
    "5": "5",
    "6": "6",
    "7": "7",
    "8": "8",
    "9": "9",
    "active": "󱓻"
  },
  "persistent-workspaces": {
    "1": [],
    "2": [],
    "3": [],
    "4": [],
    "5": []
  }
}
```

### 2. Style Empty Workspaces
In `~/.config/waybar/style.css`:

```css
/* Dim empty workspaces */
#workspaces button.empty {
  opacity: 0.5;
  color: #666;
}

/* Style active workspace */
#workspaces button.active {
  background-color: #7aa2f7;
  color: #1a1b26;
  border-radius: 4px;
}

/* Style persistent workspaces */
#workspaces button.persistent {
  min-width: 20px;
  padding: 0 8px;
}

/* Hover effects */
#workspaces button:hover {
  background-color: #3d59a1;
  color: #c0caf5;
}
```

## Configuration Details

### Key Settings Explained
- `persistent-workspaces`: Shows workspaces 1-5 even when empty
- `all-output: false`: Shows workspaces only on current monitor
- `on-click: "activate"`: Click to switch to workspace
- `format-icons`: Custom icons for each workspace

### Module Position
```json
"modules-left": ["custom/omarchy", "hyprland/workspaces"],
```

## Testing
1. Workspaces 1-5 should always be visible
2. Empty workspaces should appear dimmed
3. Click workspaces to switch between them
4. Active workspace should be highlighted

## Troubleshooting
- Restart Waybar after config changes: `pkill waybar; waybar &`
- Check config syntax: `waybar --config ~/.config/waybar/config.jsonc --check`
- Verify Hyprland IPC is working: `hyprctl monitors`

## Integration with Hyprland
- Works seamlessly with monitor-specific workspace script
- Automatically updates when workspaces are created/destroyed
- Respects workspace monitor assignments from Hyprland
# Hyprland Monitor and Workspace Configuration

## Overview
Configure monitor-specific workspaces in Hyprland where SUPER+1/2 go to laptop (eDP-1) and SUPER+3/4/5 go to external monitor (HDMI-A-1).

## Key Files
- `~/.config/hypr/bindings.conf` - Key bindings for workspace switching
- `~/.config/hypr/workspace-switch.sh` - Script to enforce monitor-specific workspace rules

## Implementation

### 1. Create Workspace Switching Script
```bash
#!/bin/bash
# ~/.config/hypr/workspace-switch.sh

WORKSPACE=$1

case $WORKSPACE in
    1|2)
        hyprctl dispatch workspace "$WORKSPACE"
        hyprctl dispatch moveworkspacetomonitor "$WORKSPACE" eDP-1
        ;;
    3|4|5)
        hyprctl dispatch workspace "$WORKSPACE"
        hyprctl dispatch moveworkspacetomonitor "$WORKSPACE" HDMI-A-1
        ;;
    *)
        hyprctl dispatch workspace "$WORKSPACE"
        ;;
esac
```

Make executable: `chmod +x ~/.config/hypr/workspace-switch.sh`

### 2. Configure Key Bindings
In `~/.config/hypr/bindings.conf`:

```bash
# Unbind default workspace keys
unbind = SUPER, code:10
unbind = SUPER, code:11
unbind = SUPER, code:12
unbind = SUPER, code:13
unbind = SUPER, code:14
unbind = SUPER, code:15
unbind = SUPER, code:16
unbind = SUPER, code:17
unbind = SUPER, code:18
unbind = SUPER, code:19

# Monitor-specific workspace bindings
bind = SUPER, 1, exec, ~/.config/hypr/workspace-switch.sh 1
bind = SUPER, 2, exec, ~/.config/hypr/workspace-switch.sh 2
bind = SUPER, 3, exec, ~/.config/hypr/workspace-switch.sh 3
bind = SUPER, 4, exec, ~/.config/hypr/workspace-switch.sh 4
bind = SUPER, 5, exec, ~/.config/hypr/workspace-switch.sh 5
```

### 3. Launch Applications on Specific Workspaces
In your Hyprland autostart config:
```bash
# Launch terminal on workspace 1 (laptop)
exec-once = [workspace 1] uwsm app -- $TERMINAL

# Launch browser on workspace 3 (external monitor)
exec-once = [workspace 3] uwsm app -- $browser

# Launch Spotify on workspace 4 (external monitor)
exec-once = [workspace 4] uwsm app -- spotify
```

## Monitor Compatibility
- Handles monitor disconnection/reconnection automatically
- If HDMI-A-1 is disconnected, workspaces 3-5 will default to available monitor
- Script gracefully handles missing monitors

## Testing
1. Press SUPER+1/2 - should go to laptop screen
2. Press SUPER+3/4/5 - should go to external monitor
3. Disconnect external monitor - workspaces should adapt automatically

## Troubleshooting
- Ensure script is executable
- Check monitor names with `hyprctl monitors`
- Verify key bindings with `hyprctl binds`

## Current setup 
	- w1 is general terminal/ sysmon 
	- w2 is general browser
	- w3 is notes
	- w4 is programming work
	- w5 is browser and Gui Apps for work
	- this should work on a single monitor setup too, once I am used to it. 
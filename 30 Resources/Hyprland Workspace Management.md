---
Type: Resource
tags: [Hyprland, Linux, Window Manager, Workspaces]
---

# Hyprland Workspace Management

## Overview
Comprehensive guide to managing workspaces in Hyprland, the dynamic tiling Wayland compositor.

**Created**: 2025-10-09

## Basic Workspace Commands

### List & Switch Workspaces
```bash
# List all workspaces (JSON format)
hyprctl workspaces -j

# Switch to workspace
hyprctl dispatch workspace 1

# Get current workspace info
hyprctl activeworkspace -j

# Move workspace to specific monitor
hyprctl dispatch moveworkspacetomonitor 1 eDP-1
```

### Workspace Configuration
**Location**: `~/.config/hypr/workspaces.conf`

**Format**: `workspace=id,monitor:monitorName,persistent:boolean,default:boolean`

**Examples:**
```bash
workspace=1,monitor:eDP-1,persistent:true,default:true
workspace=2,monitor:eDP-1,persistent:true
workspace=3,monitor:HDMI-A-1,persistent:true,default:true
```

## Workspace Properties

### Key Attributes
- **id**: Workspace number (1-10, etc.)
- **monitor**: Which monitor displays the workspace
- **persistent**: Workspace exists even when empty
- **default**: Default workspace for the monitor
- **windows**: Number of windows on the workspace

### Detection & Query Functions
```bash
# Check if workspace has windows
workspace_has_windows() {
    local workspace="$1"
    local count=$(hyprctl clients -j | jq -r --arg ws "$workspace" \
        '[.[] | select(.workspace.id == ($ws | tonumber))] | length')
    [[ "$count" -gt 0 ]]
}

# Get workspace monitor binding
hyprctl workspaces -j | jq -r '.[] | select(.id == 2) | .monitor'

# Find windows on specific workspace
hyprctl clients -j | jq -r '.[] | select(.workspace.id == 1) | .class'

# Check if app class is running
is_app_running() {
    local app_class="$1"
    local count=$(hyprctl clients -j | jq -r --arg class "$app_class" \
        '[.[] | select(.class == $class)] | length')
    [[ "$count" -gt 0 ]]
}
```

## Advanced Operations

### Silent Operations
Prevent visual disruption when automating workspace changes.

```bash
# Switch workspace without animation/focus
hyprctl dispatch workspace 1 >/dev/null 2>&1

# Move window silently to workspace
hyprctl dispatch movetoworkspacesilent 2, class:brave-browser
```

### Client/Window Management
```bash
# List all clients/windows
hyprctl clients -j

# Query client properties
hyprctl clients -j | jq '.[] | {class, title, workspace}'
```

## Best Practices

### 1. Use Persistent Workspaces
Persistent workspaces prevent "disappearing" workspaces when windows are closed. Always set `persistent:true` for regularly-used workspaces.

### 2. Explicit Monitor Binding
Bind workspaces to specific monitors to prevent them from jumping between displays in multi-monitor setups.

### 3. Silent Operations for Automation
Use `silent` operations (`/dev/null 2>&1`) when scripting to avoid visual disruptions.

### 4. JSON Parsing for Reliability
Always parse JSON output with `jq` for reliable scripting. Text output formats can change.

### 5. Global Workspace IDs
Workspace IDs are global across all monitors, not per-monitor. Use unique IDs for each workspace.

## Common Pitfalls

### 1. Workspace Switching Without Monitor Binding
**Problem**: Workspaces jump between monitors unpredictably.
**Solution**: Always bind workspaces to specific monitors in config.

### 2. Non-Persistent Workspaces
**Problem**: Workspaces disappear when empty, confusing users.
**Solution**: Set `persistent:true` for regularly-used workspaces.

### 3. Focus Stealing
**Problem**: Automated workspace changes steal focus from active windows.
**Solution**: Use silent operations and redirect output to `/dev/null`.

### 4. Race Conditions
**Problem**: Apps not ready when workspace operations execute.
**Solution**: Add small delays (`sleep 0.1`) when launching apps before workspace operations.

## Related Notes
- [[Hyprland Monitor Configuration Basics]]
- [[Multi-Monitor Workspace Strategies]]
- [[Hyprland App Launching and Window Rules]]
- [[Hyprland Layout Management]]
- [[Omarchy]] - Hyprland-based distribution

---
*Last updated: 2026-01-31*

---
Type: Project
started: true
start_date: 2026-02-01
status: active
---

# Hyprland Multi-Monitor Workspace Setup

## Overview
Configure Hyprland to handle external monitors like GNOME — workspaces stay tied to their monitor instead of moving around when you switch.

**Current Setup**: Omarchy with auto-scaling (GDK_SCALE,2), no workspace rules defined

**Problem**: Default Hyprland behavior sends windows to workspace defined on currently focused monitor. When switching monitors, windows don't follow.

**Goal**: When you're on HDMI-A-1 → workspace 1 stays on HDMI-A-1. When on DP-2 → workspace 2 stays on DP-2. Like GNOME.

## Solution

### Approach 1: Use split-monitor-workspaces Plugin (Recommended)

This is a small Hyprland plugin designed exactly for your use case.

#### Step 1: Clone the Plugin
```bash
cd ~/.config/hyprland/
git clone https://github.com/Duckonaut/split-monitor-workspaces
```

#### Step 2: Create Configuration File
Edit or create `~/.config/hyprland/per-monitor-workspaces.conf`:

```conf
# Per-monitor workspaces (like GNOME)
plugin {
    split-monitor-workspaces {
        # How many monitors?
        monitor_count = 2

        # Create workspaces for each monitor
        # Workspace numbers 1-10 for monitor 1
        # Workspace numbers 11-20 for monitor 2
        # Workspace numbers 21-30 for monitor 3
        # And so on...

        # Make workspaces persistent (stay on their monitor)
        persistent_workspaces = true

        # Send window to workspace on its monitor
        dispatch_to_monitor = true

        # Notifications
        enable_notifications = true
    }
}
```

#### Step 3: Restart Hyprland
```bash
# Kill all waybars, statusbars, etc. (or just log out and back in)
killall Hyprland

# Or use systemctl restart if using systemd
systemctl restart --user hyprland.service
```

### Approach 2: Manual Workspace Rules (Alternative)

If you prefer not to use a plugin, add these rules to `monitors.conf`:

```conf
# Per-monitor workspace rules
plugin {
    split-monitor-workspaces {
        monitor_count = 2

        # Workspace 1 stays on monitor 1
        workspace 1 {
            name = 1
            monitor = "HDMI-A-1"
        }

        # Workspace 2 stays on monitor 2
        workspace 2 {
            name = 2
            monitor = "DP-2"
        }
    }
}
```

### Workspace Naming Strategy
- **Workspace 1**: Name it `Home` (for daily use on HDMI)
- **Workspace 2**: Name it `Work` (for external monitor work)

### Verification

After restarting, test that it works:

1. Open a window on HDMI-A-1 (workspace 1)
2. Switch to DP-2 (focus moves to monitor 2)
3. Open another window → should go to workspace 2
4. Switch back to HDMI-A-1 → should go back to workspace 1

## Current Monitor Configuration

Your current setup (`~/.config/hypr/monitors.conf`):

```conf
# Your monitors (from monitors.conf)
# Monitor 1: HDMI-A-1, auto, 2x scale
# Monitor 2: DP-2, auto, 1.75x scale
env = GDK_SCALE,2
```

## Why This Works Like GNOME

**GNOME behavior**: Each monitor has its own set of workspaces. When you switch monitors, GNOME remembers which monitor you were using and restores the appropriate workspace.

**This setup**: By defining workspaces PER MONITOR, Hyprland will know:
- "Hey, Andrew's looking at DP-2" → Show workspace 2
- "Andrew switched to HDMI-A-1" → Show workspace 1

**Result**: Workspaces stay put. No window shuffling when you switch monitors.

## Installation Steps

1. **Clone split-monitor-workspaces plugin** (if using Approach 1)
2. **Create config file** (`~/.config/hyprland/per-monitor-workspaces.conf`)
3. **Restart Hyprland**
4. **Test switching behavior**

## Alternative: Single "Main" Workspace

If you want something even simpler, define ONE workspace that spans all monitors:

```conf
# Single workspace across all monitors
workspace = name:Main {
    monitor = all
    persistent = true
}

# But you'll need to move windows manually when switching monitors
# This is simpler but less GNOME-like
```

## Customization Options

You can adjust:

- **Workspace names** (in the config): Change `1`, `2` to `Home`, `Work`, etc.
- **Monitor IDs**: Update to match your actual monitor names
- **Scaling**: Adjust if GDK_SCALE doesn't work for your setup
- **Window rules**: Add specific rules for certain apps

## Troubleshooting

If workspaces still move around:

1. **Check plugin is loaded**:
   ```bash
   hyprctl version
   ```
   Look for `split-monitor-workspaces` in output

2. **Check config syntax**:
   ```bash
   hyprctl config reload
   ```

3. **Verify monitor detection**:
   ```bash
   hyprctl monitors
   ```

## Related Notes

- [[30 Resources/Hyprland Monitor and Workspace Configuration]] — Technical reference
- [[20 Areas/Productivity]] — Workspace switching as workflow
- [[10 Projects/Dotfiles Overhaul - fresh-tofu]] — Your dotfile management

## Next Steps

- [ ] Test the chosen approach
- [ ] Document which approach you prefer
- [ ] Update any window rules or bindings if needed
- [ ] Archive this project once working

---
**Started**: 2026-02-01
**Status**: Configured, ready to test
**Estimated Time**: 30-45 minutes to test and refine

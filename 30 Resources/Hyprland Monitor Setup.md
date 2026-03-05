# Hyprland Multi-Monitor Mastery: Bridging the Gap from GNOME's World

The journey from a familiar desktop environment like GNOME Shell to the highly customizable realm of Hyprland, a dynamic tiling Wayland compositor, is often paved with excitement for its potential and, initially, a degree of confusion, especially when ingrained workflows meet new paradigms. One of the most significant points of departure for new Hyprland users, particularly those with multi-monitor setups, is the fundamental difference in how workspaces are conceptualized and managed. If you've grown accustomed to GNOME Shell's approach where switching a workspace seamlessly transitions all your connected displays to that new collective workspace, Hyprland's default behavior can seem, at best, unintuitive and, at worst, disruptive to your established productivity flow. This guide aims to demystify Hyprland's workspace and monitor relationship, providing a comprehensive understanding and a practical roadmap to configuring a triple monitor setup that aligns with a "sensible" workflow, even one that mimics the global workspace nature of GNOME if so desired. We will navigate Hyprland's configuration intricacies, explore the rationale behind its design choices, and introduce tools that can help bridge the gap between these two distinct philosophies, empowering you to tailor Hyprland precisely to your multi-monitor needs. The core of this exploration will address the central question: how do workspaces relate to monitors in Hyprland, especially when contrasted with the more monolithic workspace view of GNOME Shell, and how can we leverage this understanding to create an efficient and personalized environment?

## Decoding Hyprland's Workspace Philosophy: A Departure from GNOME's Monolith

To effectively configure a multi-monitor setup in Hyprland that feels "sensible," especially when transitioning from GNOME Shell, it's crucial to first understand the fundamental philosophical differences in how each environment handles workspaces across multiple displays. Your experience with GNOME Shell, where changing a workspace updates all three monitors simultaneously to reflect that new workspace, is rooted in a concept we can refer to as "global workspaces" or, more accurately in GNOME's default case, "workspaces span displays." In this model, a workspace is essentially a single, expansive canvas that can be viewed across all your monitors. When you switch from Workspace 1 to Workspace 2, every monitor you have changes its view to show the contents of Workspace 2. If you have an application open on Workspace 1 on your left monitor, and you switch to Workspace 2, that application disappears from all monitors, replaced by whatever you have on Workspace 2. This creates a unified, single-context environment where all your displays act as windows into the same active workspace. While GNOME does offer an option (often via GNOME Tweaks or `gsettings`) to have "Workspaces on primary display only" or separate workspaces per monitor, the default behavior for many users is this spanning approach, which fosters a sense of all monitors moving together as a unit [[31](https://askubuntu.com/questions/1059479/dual-monitor-workspaces-in-ubuntu-18-04)]. This means that when you invoke the workspace switcher (e.g., via the Activities overview or a keyboard shortcut), you are selecting a single state for your entire desktop environment, and all monitors adjust to show that state. Applications within a workspace can be positioned on any of the monitors that comprise that workspace, but the workspace itself is the overarching entity. This can be particularly appealing for users who want to completely segregate different tasks or projects onto different workspaces, ensuring that only the relevant applications for the current task are visible across their entire desktop.

Hyprland, by stark contrast, adopts a "per-monitor workspace" model as its default behavior [[2](https://wiki.hypr.land/Configuring/Monitors)]. This means that each monitor connected to your system maintains its own independent set of workspaces. If you have three monitors, let's call them Monitor A, Monitor B, and Monitor C, Monitor A could be viewing Workspace 1, Monitor B could be viewing Workspace 2, and Monitor C could be viewing Workspace 3, all at the same time. When you switch workspaces on Monitor A (e.g., from Workspace 1 to Workspace 4), Monitors B and C remain entirely unaffected, continuing to display Workspaces 2 and 3 respectively. This design choice is common among many tiling window managers and offers a different kind of flexibility. It allows you to dedicate specific monitors to specific tasks or types of applications and maintain those contexts while you switch through different tasks on other monitors. For example, you might have your email client and communication tools always visible on Monitor A on its dedicated workspace, your code editor on Monitor B on its workspace, and a web browser for documentation on Monitor C on yet another workspace. You could then switch the web browser's monitor (Monitor C) through various research workspaces without ever disturbing your email or code. This compartmentalization can lead to highly efficient workflows for users who thrive on having multiple persistent contexts available simultaneously. The initial confusion you mentioned, "I don't understand how workspaces relate to monitors," is a very common sentiment for those moving from a global or spanning workspace model like GNOME's default to Hyprland's per-monitor approach. The key takeaway is this: in Hyprland, a workspace is intrinsically linked to a *single* monitor at any given time. When you create a new workspace, it appears on the currently focused monitor. When you switch to an existing workspace, that workspace is brought to the forefront on the currently focused monitor, replacing whatever workspace was previously active there. Other monitors continue to display their own, independently selected workspaces. This behavior is documented in the Hyprland wiki, which explicitly states, "Workspaces are, by default, per-monitor. This means that every monitor has its own set of workspaces. When you switch workspaces on one monitor, the others are unaffected" [[2](https://wiki.hypr.land/Configuring/Monitors)]. This fundamental difference is why your expectation of a workspace change affecting all monitors isn't met by default; Hyprland is designed to give each monitor its own workspace "brain."

The implications of this per-monitor workspace model are significant for workflow design. It allows for a much more granular control over what is displayed where, at the cost of the "all-or-nothing" workspace switching familiar to GNOME users. For instance, you could have a "gaming" workspace on your primary monitor with a game running, while your secondary monitor stays on a "chat" workspace with Discord, and your tertiary monitor remains on a "system monitor" workspace. Switching to a "work" workspace on your primary monitor would not disturb your chat or system monitoring. This powerful feature, however, requires a shift in thinking. Instead of "I am now on Workspace 5," the thought process becomes "My left monitor is now on Workspace 5," while acknowledging that your other monitors are likely on different, stable workspaces. This can initially feel like you're managing more "things" (the individual workspace states of each monitor), but for many, this increased control becomes a significant productivity booster. The challenge, and the focus of much of this guide, is how to configure this system so it feels "sensible" to *you*. If your ideal workflow is indeed one where all monitors change together, Hyprland's flexibility and extensible nature (through scripting and plugins) can accommodate this, but it requires understanding the underlying mechanics to build upon them. The default behavior, however, is firmly in the camp of independent monitor workspaces, a design choice that prioritizes per-monitor context persistence over a unified, global workspace state. This distinction is the bedrock upon which all Hyprland multi-monitor configurations are built, and mastering it is the first step to creating a truly personalized and efficient desktop environment. The rest of this guide will explore how to configure the physical layout, manage these per-monitor workspaces effectively, and ultimately, if you choose, simulate a global workspace environment that more closely mirrors your GNOME experience.

## Laying the Foundation: Physically Configuring Your Triple Monitor Setup in Hyprland

Before delving into the nuances of workspace management across your three monitors, the first practical step in Hyprland is to ensure the physical layout of your displays is correctly configured. This involves telling Hyprland the names of your monitors, their resolutions, refresh rates, and crucially, their relative positioning in your virtual desktop space. Hyprland's flexibility allows for precise control over this, ensuring your mouse cursor moves naturally between screens and windows are positioned as you expect. All monitor configurations are typically handled within your `~/.config/hypr/hyprland.conf` file using `monitor` directives. The general syntax for a monitor rule is `monitor = name, resolution, position, scale` [[2](https://wiki.hypr.land/Configuring/Monitors)]. Let's break down each component.

First, you need to identify the "name" of each monitor. Hyprland uses identifiers like `DP-1`, `HDMI-A-1`, or `eDP-1` (for laptop panels). To find the names of your connected monitors, open a terminal and run the command `hyprctl monitors all`. This will list all detected monitors along with their current configurations. For example, you might see output indicating `Monitor DP-1 (ID 0):`, `Monitor HDMI-A-1 (ID 1):`, and `Monitor DP-2 (ID 2):`. These `DP-1`, `HDMI-A-1`, and `DP-2` are the names you'll use in your configuration file. It's also possible to use a monitor's description for more robust rule matching, especially if port names change. For instance, if `hyprctl monitors` shows a description like `description: Chimei Innolux Corporation 0x150C (eDP-1)`, you could use `desc:Chimei Innolux Corporation 0x150C` as the name in your rule, remembering to omit the port name part in parentheses [[2](https://wiki.hypr.land/Configuring/Monitors)].

Next is the "resolution." This is typically specified as `WIDTHxHEIGHT@REFRESHRATE` (e.g., `1920x1080@144` for a Full HD display at 144Hz). Hyprland also accepts special values like `preferred` (to use the display's preferred resolution and refresh rate), `highres` (highest supported resolution), `highrr` (highest supported refresh rate), and `maxwidth` (widest supported resolution) [[2](https://wiki.hypr.land/Configuring/Monitors)]. For most standard setups, explicitly defining the resolution and refresh rate is recommended for consistency. For example, `monitor = DP-1, 1920x1080@60, 0x0, 1` configures the monitor named `DP-1` to a resolution of 1920x1080 at 60Hz.

The "position" is arguably the most critical part for a sensible multi-monitor layout. It defines the monitor's placement in the virtual coordinate system, calculated from the top-left corner. The position is given as `XxY` (e.g., `0x0`, `1920x0`, `0x1080`). If you have three 1920x1080 monitors and want them arranged horizontally from left to right, you would configure them as follows:
```ini
monitor = DP-1, 1920x1080@60, 0x0, 1      # Left monitor
monitor = HDMI-A-1, 1920x1080@60, 1920x0, 1 # Middle monitor, to the right of DP-1
monitor = DP-2, 1920x1080@60, 3840x0, 1    # Right monitor, to the right of HDMI-A-1
```
Here, `DP-1` is at the origin (`0x0`). `HDMI-A-1` starts at `1920x0`, meaning its left edge is flush with the right edge of `DP-1`. `DP-2` starts at `3840x0` (1920 + 1920), placing it to the right of `HDMI-A-1`. Hyprland uses an inverse Y cartesian system, so a negative Y value places a monitor higher, and a positive Y value places it lower. For example, to place `DP-2` above `DP-1`, you could use `monitor = DP-2, 1920x1080@60, 0x-1080, 1` [[2](https://wiki.hypr.land/Configuring/Monitors)]. Hyprland also provides convenient `auto` keywords for positioning: `auto` (places new monitors to the right of existing ones), `auto-right`, `auto-left`, `auto-up`, `auto-down`, `auto-center-right`, `auto-center-left`, `auto-center-up`, and `auto-center-down` [[2](https://wiki.hypr.land/Configuring/Monitors)]. These can simplify configuration, especially for dynamic setups, but manual positioning offers the most control for a fixed triple monitor array. The position is calculated using the *scaled* resolution, so if you have a 4K monitor (3840x2160) with a scale of 2, its effective width for positioning purposes is 1920 pixels.

Finally, "scale" is a floating-point number (or integer) used for HiDPI support. A scale of 1 means no scaling. A scale of 2 on a 4K monitor makes UI elements appear roughly the same physical size as they would on a 1080p monitor with a scale of 1. You can also use `auto` for scale to let Hyprland decide based on the monitor's PPI [[2](https://wiki.hypr.land/Configuring/Monitors)]. A recommended fallback rule for any monitor not explicitly defined is `monitor = , preferred, auto, 1`, which will automatically place any unrecognized monitor to the right of others with its preferred resolution and a scale of 1 [[2](https://wiki.hypr.land/Configuring/Monitors)].

Let's consider a concrete example for a triple monitor setup. Suppose your `hyprctl monitors all` output identifies your monitors as `DP-1`, `DP-2`, and `HDMI-A-1`. You want `DP-1` as your primary monitor on the left, `DP-2` to its right, and `HDMI-A-1` below `DP-1`. All are 1920x1080@60Hz. Your `hyprland.conf` entries might look like this:
```ini
# Monitor 1: Left (Primary)
monitor = DP-1, 1920x1080@60, 0x0, 1

# Monitor 2: Right of Monitor 1
monitor = DP-2, 1920x1080@60, 1920x0, 1

# Monitor 3: Below Monitor 1
monitor = HDMI-A-1, 1920x1080@60, 0x1080, 1
```
After adding or modifying these lines in your `hyprland.conf`, you'll need to reload Hyprland (e.g., by logging out and back in, or using `hyprctl reload` if your setup supports it gracefully for monitor changes). Your mouse should now move seamlessly between these arranged screens. If a monitor is misconfigured or you need to remove it from the layout temporarily (perhaps it's disconnected), you can use `monitor = name, disable`. Disabling a monitor moves all its windows and workspaces to the remaining monitors [[3](https://wiki.hyprland.org/0.41.2/Configuring/Monitors)]. This physical arrangement is the canvas upon which Hyprland's per-monitor workspaces will operate. Getting this right is essential before tackling more complex workspace behaviors, as it defines the spatial relationship your applications and workspaces will inhabit. Once your monitors are correctly positioned, you can proceed to customize how workspaces behave on this newly defined desktop landscape.

## Navigating Hyprland's Per-Monitor Workspaces: Default Behaviors and Initial Customization

With your three monitors physically arranged in Hyprland, the next step is to understand and begin customizing how workspaces function on this setup. As established, Hyprland's default is per-monitor workspaces [[2](https://wiki.hypr.land/Configuring/Monitors)]. This means each of your three monitors independently maintains its own current workspace. If you start Hyprland, all monitors might default to workspace "1" (or another specified default), but as soon as you change the workspace on one monitor, they diverge. For example, if you press your keybinding to switch to workspace 2 while focusing on your left monitor, only the left monitor will change to workspace 2; your middle and right monitors will remain on workspace 1. This allows each monitor to act as an independent viewport into different sets of applications. This behavior is often what users coming from GNOME find most disorienting initially, as their muscle memory expects all screens to change together.

Workspace switching in Hyprland is typically handled via keybindings defined in your `hyprland.conf` using the `bind` keyword and the `workspace` dispatcher. The basic syntax for switching to a specific numbered workspace on the currently focused monitor is `bind = MODIFIER, KEY, workspace, number`. For instance, `bind = SUPER, 1, workspace, 1` would switch the focused monitor to workspace 1 when you press Super+1. Similarly, `bind = SUPER, 2, workspace, 2` would switch to workspace 2, and so on. If you press Super+1 while your left monitor is focused, it goes to workspace 1 on the left monitor. If you then focus your middle monitor (perhaps by moving your mouse over it or using a focus keybinding) and press Super+2, your middle monitor will switch to workspace 2, while your left monitor remains on workspace 1. This independent control is core to Hyprland's design. You can also switch to workspaces relatively: `workspace r+1` (next workspace), `workspace r-1` (previous workspace), or to the next/previous *empty* workspace: `workspace e+1`, `workspace e-1` [[2](https://wiki.hypr.land/Configuring/Monitors)]. For example, `bind = SUPER, right, workspace, r+1` would cycle to the next workspace on the focused monitor.

While this per-monitor independence is powerful, Hyprland offers mechanisms to guide workspace creation and placement. One such feature is the ability to bind a specific workspace to a specific monitor. This is done using `workspace` rules in your `hyprland.conf`. The syntax is `workspace = name, monitor:monitor_name`. For example, if you always want workspace "5" to appear on your monitor named `DP-2` (perhaps your central monitor), you would add `workspace = 5, monitor:DP-2`. When you switch to workspace 5, regardless of which monitor is currently focused, Hyprland will ensure workspace 5 is displayed on `DP-2`, and `DP-2` will become the focused monitor. If you also want this workspace to be the default when `DP-2` first becomes active (e.g., on startup or when enabled), you can use the `monitor` rule with a `workspace` sub-rule: `monitor = DP-2, 1920x1080@60, 1920x0, 1, workspace, 5` [[2](https://wiki.hypr.land/Configuring/Monitors)]. This combination ensures `DP-2` uses its specified resolution and position, and that workspace 5 is its default. For a triple monitor setup, you might decide to dedicate certain workspace numbers to specific monitors for consistency. For instance:
```ini
# Assuming monitors DP-1 (left), HDMI-A-1 (middle), DP-2 (right)
# Bind workspace 1 to always be on DP-1
workspace = 1, monitor:DP-1
# Bind workspace 2 to always be on HDMI-A-1
workspace = 2, monitor:HDMI-A-1
# Bind workspace 3 to always be on DP-2
workspace = 3, monitor:DP-2
```
With these rules, pressing Super+1 will always take you to workspace 1 on your left monitor, Super+2 to workspace 2 on your middle monitor, and Super+3 to workspace 3 on your right monitor. This provides a degree of predictability, anchoring specific workspaces to specific screens. Workspaces without such rules will behave according to the default: appearing on the currently focused monitor when switched to.

Another important aspect is the "default workspace" for a monitor. If you want a particular monitor to always start on a specific workspace when Hyprland initializes or when the monitor is connected, you can specify this within the `monitor` rule itself. As touched upon above, this is done by appending `, workspace, <name>` to your monitor configuration line. For example, to have your middle monitor (`HDMI-A-1`) automatically start on workspace "10" when Hyprland loads:
```ini
monitor = HDMI-A-1, 1920x1080@60, 1920x0, 1, workspace, 10
```
This ensures that whenever this monitor is active, it will initially display workspace 10. This is useful for designating primary task areas for specific screens. You might have your main coding workspace always be the default for your central, largest monitor.

Understanding these default behaviors and initial customization options is key to feeling in control. The independence of per-monitor workspaces allows for highly specialized setups. For example, you could have:
*   **Left Monitor (DP-1):** Dedicated to communication (Workspace 1: Email, Slack) and reference materials (Workspace 4: Documentation, PDFs).
*   **Middle Monitor (HDMI-A-1):** Your primary task area (Workspace 2: Code Editor, Terminal; Workspace 5: Design Tool).
*   **Right Monitor (DP-2):** Secondary tasks or monitoring (Workspace 3: Web Browser for testing; Workspace 6: System Monitor, Music Player).

You could switch between workspaces 2 and 5 on your middle monitor for different coding/design phases, while your communication tools on the left monitor (workspace 1) and your system monitor on the right (workspace 6) remain undisturbed. This is the power of Hyprland's per-monitor model. However, if your goal is to replicate the GNOME behavior where all monitors switch in unison, these default settings will not achieve that. The next sections will explore how to manage windows across these independent workspaces and then delve into strategies and tools, like `hyprnome`, to achieve a more global workspace switching experience if that remains your preference. For now, mastering these fundamentals is crucial. Experiment with creating workspaces on different monitors, using the `workspace` dispatcher with relative and absolute indices, and observe how each monitor maintains its own state. This hands-on experience is the best way to internalize Hyprland's workspace paradigm.

## Orchestrating Windows Across Independent Workspaces: Movement and Management Rules

Once you're comfortable with the concept of per-monitor workspaces in Hyprland, the next logical step in crafting a "sensible" triple monitor setup is mastering how to move windows between these independent workspaces and monitors. Hyprland provides robust mechanisms for this, primarily through keybindings using the `movetoworkspace` and `movetoworkspacesilent` dispatchers, and through `window rules` for more automated behavior. These tools are essential for tailoring the environment to your workflow, allowing you to quickly organize applications across your expansive desktop real estate.

The most direct way to move the currently focused window to a different workspace is with the `movetoworkspace` dispatcher. Its basic syntax is `bind = MODIFIER, KEY, movetoworkspace, workspace_name_or_id`. For example, if you want to move the active window to workspace 3 on the currently focused monitor, you could use a keybinding like `bind = SUPER_SHIFT, 3, movetoworkspace, 3`. This will move the window and, by default, follow it to that workspace (i.e., switch the monitor to that workspace). If you want to move the window to a workspace on a *specific* monitor, you can append the monitor name, similar to the `workspace` dispatcher: `movetoworkspace, workspace_name_or_id, monitor_name`. For instance, `bind = SUPER_SHIFT, 1, movetoworkspace, 1, DP-1` would move the active window to workspace 1 on the monitor named `DP-1`, regardless of which monitor currently has focus. This is incredibly useful for directing applications to designated screens and workspaces. For example, you might decide that all your web browser instances should be moved to workspace "web" on your right monitor (`DP-2`).

Sometimes, you want to move a window to another workspace without immediately switching your focus to that workspace. For this, `movetoworkspacesilent` is used. The syntax is identical to `movetoworkspace`: `bind = MODIFIER, KEY, movetoworkspacesilent, workspace_name_or_id` or `bind = MODIFIER, KEY, movetoworkspacesilent, workspace_name_or_id, monitor_name`. For example, `bind = SUPER_CONTROL_SHIFT, 2, movetoworkspacesilent, 2` would move the active window to workspace 2 on the current monitor, but your view would remain on the current workspace. This is perfect for stashing an application away on a different workspace without interrupting your current task. You could then switch to that workspace later when needed. Combining these with monitor targeting allows for powerful window management: `bind = SUPER_CONTROL_SHIFT, 3, movetoworkspacesilent, 3, HDMI-A-1` would silently move the window to workspace 3 on your middle monitor.

Beyond manual keybindings, Hyprland's `window rules` offer a powerful way to automate window behavior based on their properties (like class, title, or initial workspace). These are defined in `hyprland.conf` using the `windowrule` or `windowrulev2` keywords. `windowrulev2` is generally recommended as it's more powerful and explicit. The syntax for moving a window to a specific workspace and monitor is `windowrulev2 = workspace <workspace_id> [,<monitor_name>], <criteria>`. The `<criteria>` can match window properties like `class` (application class), `title` (window title), `floating`, etc. For example, if you always want your Spotify application (class "Spotify") to open on workspace "10" of your right monitor (`DP-2`), you could add:
```ini
windowrulev2 = workspace 10, DP-2, class:Spotify
```
Or, if you want your terminal emulator (e.g., Alacritty, class "Alacritty") to always open on workspace "term" on your primary monitor (`DP-1`):
```ini
windowrulev2 = workspace term, DP-1, class:Alacritty
```
(You'd need to ensure "term" is a valid workspace name or you'd use a number). You can also make a window float, set its size, and assign it to a workspace in one rule:
```ini
windowrulev2 = float, size 800 600, workspace 5, class:SomeFloatingApp
```
This would make "SomeFloatingApp" start floating, with an 800x600 size, on workspace 5 of the currently active monitor (or a specific monitor if added). To find the `class` or `title` of an application, you can use `hyprctl clients` while the application is running. This will list all open windows and their properties, which you can then use in your rules. For a triple monitor setup, you can create a highly automated environment where your most-used applications always appear on your preferred monitor and workspace without manual intervention. For instance:
*   **Development:** `windowrulev2 = workspace 2, DP-1, class:Code` (Your IDE on the left monitor, workspace 2)
*   **Communication:** `windowrulev2 = workspace 1, DP-2, class:Slack` (Slack on the right monitor, workspace 1)
*   **Browsing:** `windowrulev2 = workspace 3, HDMI-A-1, class:firefox` (Firefox on the middle monitor, workspace 3)

This automation significantly reduces the time spent arranging windows, allowing you to dive straight into your tasks. Understanding and utilizing these movement dispatchers and window rules is fundamental to transforming Hyprland from a basic tiling manager into a bespoke environment that anticipates your needs and streamlines your multi-monitor workflow. It's about defining not just where your monitors are, but how your applications should inhabit and interact with the various workspaces across those monitors. This level of control is a hallmark of Hyprland's configurability. While this still operates within the per-monitor workspace paradigm, it lays the groundwork for more complex behaviors, including those that might simulate a global workspace environment, by precisely controlling where windows reside and how they are moved.

## Emulating GNOME's Global Workspace Switching in Hyprland: Introducing `hyprnome`

If, after exploring Hyprland's powerful per-monitor workspace capabilities, you still find yourself yearning for the simplicity of GNOME's global workspace switching—where a single command changes the workspace on all monitors simultaneously—then the `hyprnome` utility is likely the solution you're looking for. `hyprnome` is an external program, written in Rust, designed specifically to provide GNOME-like workspace switching behavior within Hyprland [[11](https://github.com/donovanglover/hyprnome), [12](https://donovan.is/hyprnome)]. It addresses the cognitive load some users experience with numbered workspaces and, importantly for your use case, aims to manage multi-monitor setups in a way that you "don't have to worry about which monitor a workspace is on" [[11](https://github.com/donovanglover/hyprnome)]. This suggests it abstracts away Hyprland's default per-monitor independence, moving towards a more unified view.

The core philosophy of `hyprnome` is to allow switching workspaces forward and backward through a linear sequence of workspaces, rather than directly jumping to a specific numbered workspace (e.g., Super+4 for workspace 4). Instead, you'd have a keybinding for "next workspace" and another for "previous workspace" [[12](https://donovan.is/hyprnome)]. This dynamic approach means you don't need to pre-define or remember which workspace numbers are in use or what they contain; you simply cycle through them. When you reach the end of your existing workspaces, `hyprnome` can create a new empty workspace for you, ensuring you always have somewhere to go. This is different from Hyprland's built-in `workspace r+1` or `r-1` dispatchers, which might wrap around or behave differently with empty workspaces [[12](https://donovan.is/hyprnome)]. The key feature for you, however, is how it handles multiple monitors. While its documentation doesn't explicitly state "it makes all monitors switch to the same workspace in the way GNOME does," its promise of "Use multiple monitors without worrying about which monitor a workspace is on" [[11](https://github.com/donovanglover/hyprnome)] strongly implies that it manages workspaces in a more global fashion, likely by ensuring that a workspace, when activated, becomes the one you interact with across your entire setup, or by moving windows to maintain a consistent active workspace context. It likely achieves this by interacting with Hyprland via `hyprctl` commands under the hood, potentially coordinating workspace changes across all connected monitors when you issue a `hyprnome` command.

To get started with `hyprnome`, you'll first need to install it. Installation methods vary by distribution:
*   **NixOS (Recommended by the author):** Add `hyprnome` to your `systemPackages` and rebuild [[11](https://github.com/donovanglover/hyprnome)].
    ```nix
    { pkgs, ... }:
    {
      environment.systemPackages = with pkgs; [
        hyprnome
      ];
    }
    ```
*   **Arch Linux (AUR):** Use an AUR helper like `yay`: `yay -S hyprnome` [[11](https://github.com/donovanglover/hyprnome)].
*   **Fedora (Copr):** Enable the solopasha/hyprland Copr repository and install: `sudo dnf copr enable solopasha/hyprland && sudo dnf install hyprnome` [[11](https://github.com/donovanglover/hyprnome)].
*   **Other distributions (via Cargo):** Ensure you have Rust installed, then use cargo to install from the GitHub repository: `cargo install --git https://github.com/donovanglover/hyprnome --tag 0.3.1` (check for the latest tag) [[11](https://github.com/donovanglover/hyprnome)].

Once installed, you integrate `hyprnome` into your Hyprland setup by modifying your keybindings in `~/.config/hypr/hyprland.conf`. You would replace your existing `workspace` keybindings with `exec` calls to `hyprnome`. A typical configuration might look like this:
```ini
# Switch to previous workspace
bind = SUPER, Left, exec, hyprnome --previous
# Switch to next workspace
bind = SUPER, Right, exec, hyprnome
# Move active window to previous workspace
bind = SUPER_SHIFT, Left, exec, hyprnome --previous --move
# Move active window to next workspace
bind = SUPER_SHIFT, Right, exec, hyprnome --move
```
Here, `hyprnome` (without arguments) moves to the next workspace, and `hyprnome --previous` moves to the previous one. The `--move` flag moves the currently active window along with the workspace switch. Other useful flags include `--no-empty` (don't create empty workspaces in the given direction) and `--cycle` (cycle between existing workspaces instead of creating new ones) [[11](https://github.com/donovanglover/hyprnome)]. The author of `hyprnome` also suggests starting Hyprland on a very high-numbered workspace if you want to be able to create new workspaces in both directions (previous and next) without hitting a lower limit (like workspace 1). This can be done with `exec-once = hyprctl dispatch workspace 5000000` in your `hyprland.conf` [[12](https://donovan.is/hyprnome)].

By using `hyprnome`, when you press your designated "next workspace" key (e.g., Super+Right), `hyprnome` will calculate what the "next" workspace is (either an existing one with a higher ID or a new one) and then, through Hyprland's IPC, command all monitors to switch to this new active workspace. This effectively simulates the global workspace behavior you're accustomed to from GNOME. Your triple monitor setup will now, when you invoke a workspace switch via `hyprnome`, change all three displays to reflect that new, singular workspace context. This allows you to maintain the workflow you're comfortable with while still benefiting from Hyprland's performance, tiling capabilities, and overall flexibility. It's important to note that `hyprnome` is an external tool; it's not part of core Hyprland. This means it relies on Hyprland's IPC (Inter-Process Communication) mechanism (`hyprctl`), and there might be slight variations in behavior or edge cases depending on Hyprland versions or specific configurations. However, for achieving the specific goal of GNOME-like, multi-monitor workspace switching, it provides a dedicated and well-regarded solution. This approach allows you to leverage Hyprland's strengths while adapting its workspace paradigm to match your ingrained habits from GNOME, making the transition smoother and your new setup feel "sensible" much more quickly.

## Beyond `hyprnome`: Alternative Strategies for Global Workspace Feel

While `hyprnome` provides an excellent, purpose-built solution for achieving GNOME-like workspace switching in Hyprland, understanding alternative strategies, including scripting and leveraging Hyprland's own dispatchers more directly, can offer deeper customization or serve as a fallback. These methods generally involve creating custom scripts or more complex keybinding sequences that explicitly command each monitor to switch to the desired workspace whenever a workspace change is initiated. This approach relies heavily on the `workspace <id>,<monitor>` syntax for the `workspace` dispatcher, which allows targeting a specific monitor for a workspace change [[2](https://wiki.hypr.land/Configuring/Monitors)].

The fundamental idea behind a manual implementation of global workspaces is that when you decide to switch to, say, workspace "N", you need to send a command to Hyprland to switch monitor 1 to workspace N, monitor 2 to workspace N, and monitor 3 to workspace N. This would typically be encapsulated in a script that takes the target workspace ID as an argument. Let's imagine you have three monitors: `DP-1`, `HDMI-A-1`, and `DP-2`. You could create a shell script, perhaps named `global_workspace.sh`:
```bash
#!/bin/bash

TARGET_WORKSPACE=$1

if [ -z "$TARGET_WORKSPACE" ]; then
  echo "Usage: $0 <workspace_id>"
  exit 1
fi

hyprctl dispatch workspace "$TARGET_WORKSPACE,DP-1"
hyprctl dispatch workspace "$TARGET_WORKSPACE,HDMI-A-1"
hyprctl dispatch workspace "$TARGET_WORKSPACE,DP-2"
```
This script takes one argument, the workspace ID you want to switch to. It then issues three `hyprctl dispatch workspace` commands, one for each monitor, instructing them all to switch to the specified `TARGET_WORKSPACE`. You would make this script executable (`chmod +x global_workspace.sh`) and place it somewhere in your PATH. Then, in your `hyprland.conf`, you could set up keybindings like this:
```ini
bind = SUPER, 1, exec, global_workspace.sh 1
bind = SUPER, 2, exec, global_workspace.sh 2
bind = SUPER, 3, exec, global_workspace.sh 3
# ... and so on for other workspaces
```
Now, when you press Super+1, the script `global_workspace.sh 1` is executed, which in turn tells all three monitors to switch to workspace 1. This achieves the core functionality of having all monitors change to the same workspace. However, this basic script has limitations. It doesn't handle relative workspace switching (e.g., "next" or "previous" workspace) as elegantly as `hyprnome`. To implement relative switching, your script would need to first query Hyprland for the current workspace on the focused monitor (using `hyprctl activeworkspace` and parsing its output), perform an arithmetic operation to determine the target workspace (e.g., current + 1 or current - 1), and then issue the `hyprctl dispatch workspace` commands for all monitors with this new target. This becomes more complex, especially handling edge cases like wrapping around or creating new workspaces if they don't exist.

Furthermore, this direct scripting approach doesn't inherently manage the "state" of your global workspaces in the same way `hyprnome` might. For instance, if you want to move a window to a different global workspace, you'd need another script or more complex keybindings that use `movetoworkspace <target_workspace>,<target_monitor>` for each monitor, which can get cumbersome. `hyprnome`'s `--move` flag abstracts this complexity. The advantage of the manual script approach is that it's transparent and relies only on core Hyprland functionality. You have full control over the logic. However, it requires more effort to implement robustly and to match the polish and features (like dynamic workspace creation or cycling) that `hyprnome` already provides. For users comfortable with shell scripting and who want to minimize external dependencies, this can be a viable path. It also serves as a good educational exercise in understanding how Hyprland's IPC (`hyprctl`) can be used to automate complex behaviors.

Another, more advanced Hyprland-native concept related to persistent applications across workspace switches is "special workspaces." Special workspaces (e.g., `special` or `special:name`) are workspaces that are sticky; windows on a special workspace will remain visible on their monitor even when you switch to other, non-special workspaces on that monitor. While not directly a solution for making *all* regular workspaces global, they can be used to create persistent elements (like a status bar, a notepad, or a music player widget) that you always want visible, regardless of which regular workspace you're viewing on a given monitor. This is a different kind of workflow but can be combined with other strategies. For example, you could have your main application workspaces managed by a global-switching mechanism (like `hyprnome` or a script), while using a special workspace for a persistent terminal or notification center on one of your monitors. The command to toggle a special workspace is `togglespecialworkspace` [[2](https://wiki.hypr.land/Configuring/Monitors)].

In summary, while `hyprnome` is likely the most straightforward and feature-complete way to get GNOME-like global workspace switching, the underlying Hyprland dispatchers provide the building blocks for custom solutions. These require more manual setup and scripting but offer ultimate transparency and control. For most users seeking the specific behavior described in the prompt, `hyprnome` strikes the best balance between ease of use and effective emulation of the desired global workspace paradigm. However, knowing that these lower-level mechanisms exist is valuable for troubleshooting or for those who wish to delve deeper into Hyprland's automation capabilities. The choice often comes down to whether you prefer a pre-packaged, dedicated tool (`hyprnome`) or are willing to build and maintain your own scripts using Hyprland's native commands. Given the goal of a "sensible" setup that mirrors GNOME, `hyprnome` is generally the recommended starting point due to its specific design for this purpose.

## Crafting Your Sensible Triple Monitor Hyprland Environment: A Synthesis and Practical Guide

Now that we've explored Hyprland's default per-monitor workspace model, the tools for managing windows, and the `hyprnome` utility for emulating global workspaces, let's synthesize this into a practical guide for setting up your "sensible" triple monitor environment. This guide will focus on achieving the GNOME-like behavior where switching a workspace changes all three monitors, as that was the core of your request.

**Step 1: Identify and Configure Your Monitors**

First, ensure your three monitors are correctly identified and positioned in your `~/.config/hypr/hyprland.conf`.
1.  Run `hyprctl monitors all` in a terminal to get the names of your monitors (e.g., `DP-1`, `HDMI-A-1`, `DP-2`).
2.  Decide on their physical arrangement (e.g., left to right: `DP-1`, `HDMI-A-1`, `DP-2`).
3.  Add `monitor` rules to your `hyprland.conf`. Example for three 1920x1080 monitors arranged horizontally:
    ```ini
    # Monitor DP-1 (Left)
    monitor = DP-1, 1920x1080@60, 0x0, 1
    # Monitor HDMI-A-1 (Middle)
    monitor = HDMI-A-1, 1920x1080@60, 1920x0, 1
    # Monitor DP-2 (Right)
    monitor = DP-2, 1920x1080@60, 3840x0, 1
    ```
    Adjust resolutions, refresh rates, and positions according to your specific hardware and desired layout. Reload Hyprland (log out/in or `hyprctl reload`) for these changes to take effect. Verify your mouse moves correctly between screens.

**Step 2: Install `hyprnome`**

Follow the installation instructions for `hyprnome` as detailed previously. For example, on an Arch-based system using an AUR helper:
```bash
yay -S hyprnome
```
Or for other systems, using Cargo:
```bash
cargo install --git https://github.com/donovanglover/hyprnome --tag 0.3.1 # Check for latest version
```

**Step 3: Configure `hyprnome` Keybindings for Global Workspace Switching**

Modify your `~/.config/hypr/hyprland.conf` to use `hyprnome` for workspace navigation. You will likely want to replace or comment out any existing `workspace` keybindings that switch to specific numbered workspaces on the current monitor.
Add keybindings for `hyprnome`. A common setup uses keys for "next" and "previous" workspace, and their "move window" counterparts:
```ini
# GNOME-like workspace switching with hyprnome
# Switch to previous workspace (affects all monitors)
bind = SUPER, Left, exec, hyprnome --previous
# Switch to next workspace (affects all monitors)
bind = SUPER, Right, exec, hyprnome
# Move active window to previous workspace (affects all monitors)
bind = SUPER_SHIFT, Left, exec, hyprnome --previous --move
# Move active window to next workspace (affects all monitors)
bind = SUPER_SHIFT, Right, exec, hyprnome --move
```
*   `SUPER, Left/Right`: These will now cycle you through your workspaces. Each switch will change the workspace on all three monitors to the new "global" workspace.
*   `SUPER_SHIFT, Left/Right`: These will move the currently focused window to the previous or next global workspace, and then switch all monitors to that workspace (following the window).

You might also consider adding keybindings for directly creating or switching to specific, commonly used global workspaces if `hyprnome` supports direct targeting or if you combine it with scripts. However, the primary "next/previous" navigation is the core of the GNOME-like feel. The `hyprnome` author suggests starting on a high-numbered workspace if you want to create workspaces in both directions [[12](https://donovan.is/hyprnome)]:
```ini
exec-once = hyprctl dispatch workspace 5000000
```
Add this line to your `hyprland.conf` to ensure you have plenty of "previous" workspaces available.

**Step 4: Utilize Window Rules for Initial Application Placement**

Even with global workspaces, you'll want applications to appear on specific monitors *within* that global workspace. Hyprland's `windowrulev2` is perfect for this. For example, if you want your web browser to always open on your middle monitor (`HDMI-A-1`) and your terminal on your left monitor (`DP-1`), regardless of which global workspace you create them on:
```ini
# Find class names using `hyprctl clients`
windowrulev2 = monitor DP-1, class:Alacritty     # Terminal on left monitor
windowrulev2 = monitor HDMI-A-1, class:firefox   # Browser on middle monitor
windowrulev2 = monitor DP-2, class:Spotify      # Music on right monitor
```
These rules ensure that when an application is launched, it's assigned to your preferred monitor within the current global workspace context. If you don't specify a workspace in the rule, they will appear on the specified monitor but on the current global workspace active on that monitor (which, thanks to `hyprnome`, will be the same across all monitors when you switch). If you wanted an app to *always* be on, say, workspace "5" of its designated monitor, you could combine `monitor` and `workspace` in the rule:
```ini
windowrulev2 = workspace 5, monitor DP-2, class:SomeSpecificApp
```
This would mean "SomeSpecificApp" always goes to workspace 5 on monitor DP-2. If you then used `hyprnome` to switch to global workspace 5, all monitors would switch to their instance of workspace 5, and this app would be visible on DP-2.

**Step 5: Test and Refine**

Reload Hyprland or restart your session.
1.  Open several applications. Observe if they adhere to your `windowrulev2` placements.
2.  Use your `hyprnome` keybindings (e.g., Super+Right) to switch to a new, empty global workspace. All three monitors should change to this new workspace.
3.  Open more applications in this new workspace. Again, check their placement.
4.  Use `hyprnome --move` (e.g., Super+Shift+Left/Right) to move windows between global workspaces.
5.  Cycle back to your previous workspace. The applications you left there should be visible on their respective monitors, exactly as you arranged them.

This setup should now provide you with a triple monitor Hyprland environment where workspace switching is global, closely mimicking the behavior you were used to in GNOME Shell, while still allowing you to leverage Hyprland's tiling and other powerful features. You can further refine this by exploring other `hyprnome` flags like `--cycle` or `--no-empty` to fine-tune the workspace creation behavior, and by adding more sophisticated `windowrulev2` entries for your most-used applications. The key is that `hyprnome` handles the "global" aspect of workspace switching, while Hyprland's native features handle window placement and tiling within that global context. This combination offers a powerful and familiar workflow.

## Conclusion: Mastering Your Multi-Monitor Domain in Hyprland

Transitioning to Hyprland from a desktop environment like GNOME Shell involves a re-evaluation of familiar concepts, with multi-monitor workspace management being a prime example. Hyprland's default per-monitor workspace model, where each display maintains its own independent set of workspaces, offers a powerful and flexible paradigm for organizing tasks, distinct from GNOME's more unified, global workspace approach [[2](https://wiki.hypr.land/Configuring/Monitors)]. While this independence can initially seem counter-intuitive, it unlocks workflows where different monitors can be dedicated to persistent, specific tasks, unaffected by workspace changes on other screens. However, for users who have built their productivity around the all-monitors-switch-together behavior of GNOME, this default Hyprland behavior can feel like a hurdle.

This guide has navigated these differences, starting with a clear explanation of Hyprland's core workspace philosophy. We then detailed the essential steps for physically configuring your triple monitor setup in `hyprland.conf`, ensuring your displays are correctly positioned and scaled for a seamless desktop experience [[2](https://wiki.hypr.land/Configuring/Monitors)]. We explored Hyprland's native tools for managing windows across these independent workspaces, including keybindings for moving windows between workspaces and monitors, and the powerful `windowrulev2` for automating application placement. While these features operate within the per-monitor framework, they are crucial for any sensible setup.

Recognizing the specific desire for GNOME-like global workspace switching, we introduced `hyprnome`, a dedicated utility designed to provide this exact functionality within Hyprland [[11](https://github.com/donovanglover/hyprnome), [12](https://donovan.is/hyprnome)]. By integrating `hyprnome` into your keybindings, you can effectively command all your monitors to switch to the same workspace simultaneously, thus bridging the gap between Hyprland's underlying model and the workflow you're accustomed to. The practical guide provided a step-by-step approach to configuring your monitors, installing `hyprnome`, setting up global workspace keybindings, and using window rules to ensure applications open on your preferred monitors within this global context.

The journey to a "sensible" triple monitor setup in Hyprland is one of understanding its defaults and then leveraging its configurability—through native settings, IPC scripting, or tools like `hyprnome`—to mold it to your preferences. Whether you embrace Hyprland's per-monitor independence for its granular control or adapt it to a more global model using `hyprnome`, the result is a highly efficient, personalized, and dynamic desktop environment. The key is experimentation and a willingness to explore the rich configuration options Hyprland provides. With the knowledge and techniques outlined in this guide, you are now well-equipped to master your multi-monitor domain in Hyprland, crafting an experience that is both powerful and perfectly tailored to your workflow.

## References

[2] Monitors. https://wiki.hypr.land/Configuring/Monitors.

[3] Monitors. https://wiki.hyprland.org/0.41.2/Configuring/Monitors.

[11] donovanglover/hyprnome: GNOME-like workspace switching in Hyprland. https://github.com/donovanglover/hyprnome.

[12] hyprnome | Donovan Glover. https://donovan.is/hyprnome.

[31] Dual monitor workspaces in Ubuntu 18.04 - gnome. https://askubuntu.com/questions/1059479/dual-monitor-workspaces-in-ubuntu-18-04.
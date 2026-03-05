# Packages to Install

## Via Omarchy Menu
* **Appearence** 
	- [x] Fira Code font
- **Services**
	- [x] Tailscale
	- [x] Dropbox (The installation process takes you to the login) 
-  **Development Environments**
    - [x] GO
    - [x] Python
    - [x] Elixir
        - [x] Phoenix
    - [x] Zig
    - [x] Rust
    - [x] Ocaml
    - [x] Postgress in a docker container
    - [x] Javascript
        - [x] Node-js
        - [x] Bun
        - [x] Deno
        - I've installed all 3 as there are no clear winners yet
      - [x] Ruby on Rail
-  **Editors**
	- [x] Zed
	- [x] VS-Code
- **AI**
	- Opencode is installed by default
	 - [x] Install LM Studio
	 - [x] Install Gemini CLI 
	 - [x] Dictation
	  - There is a handy script to install install a very good voice recognition model for dictation. 
- **Gaming**
	- [x] Install Steam
	- [x] Install Retroarch
## From Official Arch Packages
There is a nice way to access Pacman through omarchy menu
  - [x] Syncthing
  - [x] amdgpu_top
  - [x] chezmoi
  - [x] Yazi
## From AUR 
- [x] Brave Browser
# System Appearance
- [x] Change The Theme to Gruvbox
- [ ] Add Wall Papers I like to the right place
**LM Studio**
- [ ] Download models
## Gaming
 - [x] Steam
    - [x] Sign into Steam

  - [x] RetroArch

    - [ ] Setup RetroArch

    

## System Tweaks

- [ ] change Key Maps  to the ones I am used to

```elixir
# Change Omarchy menu Launch Key
unbind = SUPER ALT, SPACE
bindd = SUPER, X, Omarchy Menu, exec, omarchy-menu-[ ] 
# Change The Close Window Key
unbind = SUPER, W
bindd = SUPER, Q, Close Active Window, killactive

```

  - [x] in `inputs.conf' change touchpad settings

```elixir
clickfinger_behavior = true
gesture = 3, horizontal, workspace
```

- [ ] Set up Auto start
  - [ ] Syncthing



# Post Install 

- [ ] Logins
  - [x] Sign in and Connect With Spotify
  - [x] Login to Tailscale
  - [x] Sign into Zed Editor
    - I like the Agent Client Protocol, A cool way access CLI agent frameworks in an editor with a great vim mode

  - [ ] Setup
  - [ ] Setup Opencode
    - [ ] Gruvbox Themes

  - [ ] Setup Gemini CLI

- [x] Sign into VS-Code
  - [x] Sync settings via the Github Account
- [x] Sign into Opencode (Omarchy has this installed by Default)
  - [ ] z.ai Coding plan
  - [ ] openrouter
- [ ] Sign into Gemini CLI
- [ ] Sync with Brave Sync Chain 
  - do this after 

# Workflow Tweaks

## Dotfiles Restoration (2026-02-03)

After installing Omarchy on fresh-tofu, restored old dotfiles using chezmoi:

**Process:**
1. Installed Omarchy on fresh-tofu (Arch Linux)
2. Applied existing dotfiles from personal dot_files repository
	1. Configured chezmoi for ongoing dotfile management
3. Authenticated with GitHub (gh CLI)
4. Verified all configurations match original setup

**What's Managed:**
- Shell configuration (zsh, Oh My Zsh)
- Terminal settings (Ghostty)
- Development tool configurations (mise, uv, git)
- Custom aliases and functions
- API keys and environment variables (where appropriate)

**Future Restores:**
- `chezmoi apply` to restore everything
- `chezmoi add ~/.config/file` to track new configs
- All changes tracked in git repository

- setup Syncthing
  - Sync Notes
  - [x] Start Syncthing service
  - [x] Sync Obsidian new_brain vault to phone
  - [x] Resolve 16 sync conflicts (workspace and plugin data)
  - [x] Create .stignore file to prevent future conflicts
- setup Obsidian

# Recent Activity (2026-01-30)

## Development Tools
- [x] Installed Clawdbot via molt.bot
- [x] Configured Clawdbot for WhatsApp gateway
- [x] Set up chezmoi for dotfiles management
- [x] Cloned dot_files repo to chezmoi source directory
- [x] Authenticated with GitHub (gh CLI)

## Apps & Utilities
- [x] M5Burner installed (ESP32 flashing tool)
  - Moved to ~/Apps/
  - Added user to dialout and uucp groups for device access
- [x] Used kdeconnect for device management
- [x] Tested Ghostty terminal
- [x] Used multiple terminals (bash/zsh)

## System Configuration
- [x] Tailscale: logged in and set operator=$USER
- [x] Syncthing: started and configured for vault sync
- [x] Formatted USB drive (/dev/sda1) to FAT32

## Projects & Planning
- [x] Created "Dotfiles Overhaul - fresh-tofu" project note
- [x] Compared current system with dotfiles repo
- [x] Created "Syncthing Setup & Maintenance" resource note
- [x] Updated this checklist with completed items

## Tools in Use
- **Terminal emulators:** Ghostty (primary), Kitty (with 200+ themes)
- **Editors:** Zed (signed in), VS Code (synced via GitHub), Neovim (LazyVim)
- **CLI tools:** eza, bat, fzf, zoxide, starship, chezmoi
- **Package managers:** Pacman, Yay (AUR), brew (via Oh My Fish)

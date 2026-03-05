# Dotfiles Overhaul - fresh-tofu - State Snapshot

**Date:** 2026-01-30
**System:** fresh-tofu (Omarchy Arch)
**Purpose:** Snapshot of current system vs dotfiles repo differences

---

## System: `fresh-tofu` (Omarchy Arch)

### Environment
- **Desktop Environment:** Hyprland + Waybar
- **Theme:** Gruvbox
- **Shell:** Bash (using chezmoi zsh config)
- **Package Manager:** Pacman + Yay (AUR)

### Installed Tools & Apps

**Development:**
- ✅ Go, Python, Elixir/Phoenix, Zig, Rust, OCaml, Ruby on Rails
- ✅ Node.js, Bun, Deno (all 3 installed)
- ✅ Postgres in Docker container

**Editors:**
- ✅ Zed (signed in, using Agent Client Protocol)
- ✅ VS Code (synced via GitHub)
- ✅ Neovim (LazyVim setup)
- ✅ Ghostty (terminal)
- ✅ Kitty (terminal)

**Terminals & Tools:**
- ✅ eza, bat, fzf, zoxide, starship (all in path)
- ✅ chezmoi (v2.69.0)
- ✅ LM Studio
- ✅ Gemini CLI
- ✅ Opencode (Omarchy default)

**Services:**
- ✅ Tailscale (connected, operator=$USER)
- ✅ Syncthing
- ✅ Dropbox
- ✅ Steam
- ✅ RetroArch

**Other:**
- ✅ Fira Code font
- ✅ amdgpu_top
- ✅ M5Burner (in ~/Apps)

---

## Comparison: Current System vs Dotfiles Repo

### Shell Configuration

#### Current `~/.zshrc` (Minimal):
```bash
. "$HOME/.local/share/../bin/env"

# Added by LM Studio CLI (lms)
export PATH="$PATH:/home/tofu/.lmstudio/bin"
```

#### Repo `dot_zshrc` (Full oh-my-zsh setup):
- **Oh-My-Zsh** with plugins:
  - docker, docker-compose, extract, fzf-tab
  - gcloud, git, node, npm, pip
  - poetry, python, virtualenv, virtualenvwrapper
  - rust, web-search, zoxide, you-should-use
  - zsh-autosuggestions, zsh-interactive-cd, colored-man-pages
- **Aliases:** ls→eza, n→nvim, nf→fzf+nvim, of→fzf+open, and many more
- **Editor:** nvim
- **Environment:**
  - ANTHROPIC_BASE_URL and AUTH_TOKEN
  - BUN_INSTALL and PATH
  - MotherDuck tokens for work/personal machines
  - gcloud SDK
  - zoxide, atuin, starship integration
- **Host-specific configs:**
  - `enviro-dev`: Work machine with API keys
  - `fresh-tofu`: Personal machine with MD_PERSONAL token

**Gap:** Current system has minimal zshrc; repo has full-featured setup

### Neovim

#### Current `~/.config/nvim`:
- LazyVim setup (11.5k bytes LICENSE, full lua config)
- Git-managed with plugins in `lua/plugins/`

#### Repo `private_dot_config/nvim.vanila`:
- Complete custom nvim config
- Orgmode, Telekasten, obsidian integration
- Whichkey, Telescope, Harpoon, Oil

**Gap:** Two different nvim setups - current uses LazyVim, repo has custom vanilla setup

### Terminal Emulators

#### Ghostty:
- **Current:** Basic 963 byte config
- **Repo:** Full theme collection (350+ themes)

#### Kitty:
- **Current:** Basic 690 byte config + kitty-themes submodule (full repo cloned)
- **Repo:** Same kitty-themes plus theme.conf

**Gap:** Ghostty themes not in repo

### Wayland/Hyprland

#### Current `~/.config/hypr/`:
- `autostart.conf`, `bindings.conf`, `envs.conf`
- `hypridle.conf`, `hyprlock.conf`, `hyprland.conf`
- `hyprsunset.conf`, `input.conf`, `monitors.conf`
- `input.conf.bak.1756960134`
- `workspace-switch.sh`

#### Repo: No Hyprland configs tracked

**Gap:** All Hyprland config is local, not in dotfiles

### Starship

#### Current:
```toml
# 768 bytes - Gruvbox theme setup
```

#### Repo:
- Full starship.toml with customizations

### Waybar

#### Current:
- `config.jsonc` and `style.css` (modified locally)

#### Repo:
- Different versions

---

## Missing from Repo (Local Only)

1. **Hyprland configs** - All `.config/hypr/*` files
2. **Opencode config** - `.config/opencode/opencode.json`
3. **Zed config** - `.config/zed/settings.json`, `keymap.json`
4. **Helix configs** - `.config/helix/config.toml`, `language.toml`
5. **Nushell configs** - `.config/nushell/config.nu`, `env.nu`
6. **Ranger configs** - `.config/ranger/*`
7. **Local bin scripts:**
   - cleanup-duplicate-terminals
   - detect-terminal-apps
   - ghostty-themes
   - launch-workspace-layout
   - manage-workspace-layout
   - test-workspace-system
   - update-theme-colors
8. **Local fonts:**
   - Fira Code Nerd Font variants
   - Anonymice Nerd Font
   - Inconsolata, Roboto Mono, Space Mono
   - Segoe UI Emoji (seguiemj.ttf)
9. **Workspace system** - launch/manage scripts for terminal layout

---

## In Repo but Not Installed Locally

1. **Spacemacs** - `dot_spacemacs` (30KB)
2. **Tmux** - `dot_tmux.conf`
3. **Wezterm** - `dot_wezterm.lua`
4. **Scripts folder** - Various shell scripts in repo

---

## Additional Observations

### Recent Command History (2026-01-30)
- Tailscale login & setup
- Ghostty usage
- kdeconnect usage
- Syncthing usage
- gh auth login (completed)
- chezmoi cd attempts
- gh repo clone tofusoul/dot_files
- M5Burner setup (moved to ~/Apps, added user to dialout/uucp groups)
- Clawdbot setup
- Formatting USB drive (/dev/sda1)

### Key Observations
- Switched from bash to zsh temporarily (zsh commands in history)
- Using chezmoi cd to explore dotfiles

### Notes:
- M5Burner setup details moved to: `30 Resources/M5 Cardputer - Arch Linux Setup.md`

---

*Snapshot created: 2026-01-30 17:20*

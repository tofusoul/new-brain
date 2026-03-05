# What I Did After Installing Omarchy
*Comprehensive System Restoration Guide*

**Last Updated**: 2026-02-03 - Added Omarchy menu packages checklist and pending tasks documentation

## 📅 Overview
This document captures all the changes, installations, and configurations made after installing Omarchy. Use this to restore your system to its current state.

**System**: fresh-tofu (Arch Linux rolling release)
**Installation Date**: 2025-09 (original), dotfiles reapplied 2026-02-03

**Recent Update (2026-02-03)**:
- Installed Omarchy on fresh-tofu
- Applied old dotfiles to restore familiar environment after Omarchy install
- All packages, configurations, and workflows restored to match original setup

---

## 🛠️ System Setup

### What is Omarchy?
Omarchy is a custom Arch Linux installation system that provides:
- Menu-based package installer with curated selections
- Built-in theme system (Gruvbox, custom themes)
- Pre-configured development environments
- Streamlined system setup for Arch Linux

### Operating System & Core
- **OS**: Arch Linux (rolling release)
- **Shell**: Migrated from bash to zsh with Oh My Zsh
- **Terminal**: Ghostty with Gruvbox theme
- **Package Manager**: `yay` (AUR helper) + `pacman`

### Dotfiles Restoration (2026-02-03)
After installing Omarchy on fresh-tofu, applied old dotfiles to restore familiar environment:

**Process**:
1. Installed Omarchy on fresh-tofu (Arch Linux)
2. Applied existing dotfiles from personal dot_files repository
3. Configured chezmoi for ongoing dotfile management
4. Authenticated with GitHub (gh CLI)
5. Verified all configurations match original setup

**Dotfiles Managed via chezmoi**:
- Shell configuration (zsh, Oh My Zsh)
- Terminal settings (Ghostty)
- Development tool configurations (mise, uv, git)
- Custom aliases and functions
- API keys and environment variables (where appropriate)

**Benefits**:
- Familiar working environment restored instantly
- Future system restores are trivial with chezmoi apply
- Configuration changes tracked in git repository

### Packages Installed via Omarchy Menu

**Appearance**:
- [x] Fira Code font

**Services**:
- [x] Tailscale (logged in, operator=$USER configured)
- [x] Dropbox

**Development Environments**:
- [x] GO (1.25.1 - managed by mise)
- [x] Python (3.13.7 - managed by mise)
- [x] Elixir (1.18.4-otp-28 - managed by mise)
  - [x] Phoenix
- [x] Zig (0.15.1 - managed by mise)
- [x] Rust
- [x] OCaml
- [x] PostgreSQL (in Docker container)
- [x] JavaScript
  - [x] Node.js (22.19.0 LTS - managed by mise)
  - [x] Bun (2.4.5 - managed by mise)
  - [x] Deno
  - Note: Installed all 3 JavaScript runtimes as no clear winners yet
- [x] Ruby on Rails (3.4.5 - managed by mise)

**Editors**:
- [x] Zed (signed in, Agent Client Protocol configured)
- [x] VS Code (synced via GitHub account)

**AI Tools**:
- [x] Opencode (installed by default with Omarchy)
- [x] LM Studio
- [x] Gemini CLI
- [x] Dictation (handy script for voice recognition model)

**Gaming**:
- [x] Steam (signed in)
- [x] RetroArch

### Core Applications Installed
```bash
# System Tools
sudo pacman -S zsh zsh-completions
sudo pacman -S ghostty
sudo pacman -S docker docker-compose docker-buildx

# Development Tools
sudo pacman -S python-gobject python-poetry-core python-terminaltexteffects

# AUR Helper
yay -S ghostty
yay -S lazydocker lazygit
yay -S asdcontrol-git

# Additional AUR packages
yay -S Syncthing
yay -S amdgpu_top
yay -S chezmoi
yay -S Yazi
yay -S brave-browser
```

---

## 🔧 Development Environment Setup

### Python Environment Management
```bash
# UV (Python Package Manager)
# Installation: Via official script (not package manager)
# Location: ~/.local/bin/uv
# Version: 0.8.15

# Mise (Version Manager)
# Installation: Via package manager
# Location: /usr/bin/mise
# Purpose: Manage multiple runtime versions
```

### Runtime Versions (Managed by Mise)
```
deno     2.4.5         Latest
elixir   1.18.4-otp-28 Latest
erlang   28.0.2        Latest
go       1.25.1        Latest
node     22.19.0       LTS
python   3.13.7        Latest
ruby     3.4.5         Latest
zig      0.15.1        Latest
```

### Rust Tools
```bash
# Installation via cargo
cargo install usage-cli  # Version: 2.2.2
```

### System Configuration & Tweaks

**Keymap Changes**:
```elixir
# Change Omarchy menu Launch Key from SUPER+ALT+SPACE to SUPER+X
unbind = SUPER ALT, SPACE
bindd = SUPER, X, Omarchy Menu, exec, omarchy-menu

# Change Close Window Key from SUPER+W to SUPER+Q
unbind = SUPER, W
bindd = SUPER, Q, Close Active Window, killactive
```

**Touchpad Settings** (`inputs.conf`):
```elixir
clickfinger_behavior = true
gesture = 3, horizontal, workspace
```

**Theme**:
- [x] Changed to Gruvbox theme
- [ ] Add favorite wallpapers to the right place

### Pending Setup Tasks

**System Appearance**:
- [ ] Add wallpapers I like to the right place

**LM Studio**:
- [ ] Download models

**Gaming**:
- [ ] Setup RetroArch

**Auto-start Services**:
- [ ] Set up Syncthing auto-start

**Opencode Configuration**:
- [ ] Gruvbox themes
- [ ] z.ai coding plan
- [ ] openrouter setup

**Other Logins**:
- [ ] Sign into Gemini CLI
- [ ] Sync with Brave Sync Chain

### Syncthing Setup & Obsidian Vault Sync

**Completed (2026-01-30)**:
- [x] Start Syncthing service
- [x] Sync Obsidian new_brain vault to phone
- [x] Resolve 16 sync conflicts (workspace and plugin data)
- [x] Create .stignore file to prevent future conflicts

**Configuration**:
- Syncing Obsidian vault across devices
- Used .stignore to exclude problematic files (workspace, plugin data)
- Prevents future sync conflicts

### Recent Activity (2026-01-30)

**Development Tools**:
- [x] Installed Clawdbot via molt.bot
- [x] Configured Clawdbot for WhatsApp gateway
- [x] Set up chezmoi for dotfiles management
- [x] Cloned dot_files repo to chezmoi source directory
- [x] Authenticated with GitHub (gh CLI)

**Apps & Utilities**:
- [x] M5Burner installed (ESP32 flashing tool)
  - Moved to ~/Apps/
  - Added user to dialout and uucp groups for device access
- [x] Used kdeconnect for device management
- [x] Tested Ghostty terminal
- [x] Used multiple terminals (bash/zsh)

**System Configuration**:
- [x] Tailscale: logged in and set operator=$USER
- [x] Syncthing: started and configured for vault sync
- [x] Formatted USB drive (/dev/sda1) to FAT32

**Projects & Planning**:
- [x] Created "Dotfiles Overhaul - fresh-tofu" project note
- [x] Compared current system with dotfiles repo
- [x] Created "Syncthing Setup & Maintenance" resource note
- [x] Updated checklist with completed items

**Tools in Use**:
- **Terminal emulators**: Ghostty (primary), Kitty (with 200+ themes)
- **Editors**: Zed (signed in), VS Code (synced via GitHub), Neovim (LazyVim)
- **CLI tools**: eza, bat, fzf, zoxide, starship, chezmoi
- **Package managers**: Pacman, Yay (AUR), brew (via Oh My Fish)

---
- [ ] Add wallpapers I like to the right place

**LM Studio**:
- [ ] Download models

**Gaming**:
- [ ] Setup RetroArch

**Auto-start Services**:
- [ ] Set up Syncthing auto-start

**Opencode Configuration**:
- [ ] Gruvbox themes
- [ ] z.ai coding plan
- [ ] openrouter setup

**Other Logins**:
- [ ] Sign into Gemini CLI
- [ ] Sync with Brave Sync Chain

---

## 🎨 Terminal & Shell Configuration

### Ghostty Terminal Setup
**File**: `~/.config/ghostty/config`

**Theme**: Gruvbox Dark
- Background: `#282828`
- Foreground: `#ebdbb2`
- Complete 16-color palette configured
- Font: Fira Code Nerd Font, size 12
- Window decorations disabled
- Padding: 8px

**Key Settings**:
```toml
command = zsh  # Default shell
cursor-style = block
scrollback-limit = 10000
mouse-hide-while-typing = true
```

### Oh My Zsh Installation
```bash
# Installation
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Theme: robbyrussell (default)
# Plugins: 14 plugins configured
```

### Oh My Zsh Plugins Installed
```bash
# Standard Plugins (via oh-my-zsh)
git, docker, docker-compose, python, pip, node, npm, cargo
command-not-found, history-substring-search, colored-man-pages, extract

# Custom Plugins (manually installed)
zsh-autosuggestions
zsh-syntax-highlighting
fzf-tab
```

**Plugin Installation Commands**:
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/Aloxaf/fzf-tab ~/.oh-my-zsh/custom/plugins/fzf-tab
```

---

## 🔗 Zsh Configuration
**File**: `~/.zshrc`

### Environment Setup
```bash
# Omarchy Integration
source ~/.local/share/omarchy/default/bash/rc

# Environment Variables
. "$HOME/.local/share/../bin/env"
. "$HOME/.cargo/env"

# Mise Integration
eval "$(mise hook-env -s zsh)"

# API Configuration
export ANTHROPIC_BASE_URL="https://api.z.ai/api/anthropic"
export ANTHROPIC_AUTH_TOKEN="[TOKEN]"
```

### Custom Aliases
```bash
# Development Shortcuts
py="python", py3="python3", venv="source .venv/bin/activate"
d="docker", dc="docker-compose", st="streamlit", po="poetry", m="mise"

# Git Shortcuts
gs="git status", gp="git push", gl="git pull", ga="git add"
gc="git commit", gco="git checkout", gb="git branch"

# Navigation
ll="ls -la", la="ls -A", l="ls -CF"
..="cd ..", ...="cd ../..", ....="cd ../../.."

# Project Specific
enviro="cd ~/Projects/Enviroflow_App"
dev-check="cd ~/Projects/Enviroflow_App && mise run dev-check"
pipeline="cd ~/Projects/Enviroflow_App && mise run pipeline"
```

### Advanced Configuration
```bash
# FZF Configuration
export FZF_DEFAULT_OPTS="--height=40% --layout=reverse --border"

# History Search
bindkey '^R' history-incremental-search-backward
bindkey '^[[A' history-substring-search-up
bindkey '^[[B' history-substring-search-down

# Auto-completion
zstyle ':completion:*' menu select
zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Za-z}'

# fzf-tab Configuration
zstyle ':fzf-tab:complete:cd:*' fzf-preview 'ls --color=always $realpath'
```

---

## 📦 Project-Specific Setup

### Enviroflow App Configuration
**Project**: `~/Projects/Enviroflow_App`

#### Mise Configuration (`mise.toml`)
```toml
[env]
_.python.venv = ".venv"

[tasks]
# CLI Pipeline Commands
cli = "python -m enviroflow_app.cli.main"
pipeline = "python -m enviroflow_app.cli.main run-all"

# Individual Commands (25+ tasks)
extract-trello = "python -m enviroflow_app.cli.main extract trello"
extract-float = "python -m enviroflow_app.cli.main extract float"
# ... (all extract/transform/load commands)

# Code Quality
lint = "ruff check . --fix"
typecheck = "basedpyright ."
test = "pytest"
dev-check = "ruff check . --fix && basedpyright . && pytest"
```

#### Automatic venv Activation
- **Trigger**: Entering project directory
- **Tool**: mise hook-env
- **Venv**: `.venv` (managed by uv, not mise)
- **Python**: 3.10.18 (managed by uv)

---

## 🔄 Migration from Bash to Zsh

### Key Changes
1. **Shell Migration**: Default shell changed from bash to zsh
2. **Configuration Migration**: Omarchy integration preserved
3. **Enhanced Features**: Added Oh My Zsh plugins and custom aliases
4. **Environment Management**: Mise hooks integrated with zsh

### Backup Files
- `~/.zshrc.pre-oh-my-zsh` - Original zsh configuration
- `~/.bashrc` - Still contains original bash setup

---

## 🔑 Authentication & API Setup

### Claude Code Integration
```bash
# Installation
npm install -g @anthropic-ai/claude-code

# Configuration Files
~/.claude.json - Main configuration
~/.claude.json.backup - Backup copy
```

### API Tokens & Services
- **Anthropic API**: Configured with base URL and token
- **Project Secrets**: Streamlit secrets in `.streamlit/secrets.toml`
- **Development Keys**: Various API keys for Trello, Float, Xero, etc.

---

## 🎯 Key Features & Workflows

### Development Workflow
```bash
# Project NavigationEats
cd ~/Projects/Enviroflow_App  # Auto-activates venv via mise

# Common Commands
mise run pipeline          # Run full ELT pipeline
mise run dev-check         # Code quality checks
mise run dev-status        # Check pipeline status
mise run lint              # Run linter with auto-fix
```

### Terminal Features
- **Auto-completion**: Enhanced with zsh-autosuggestions
- **Syntax highlighting**: Commands colored as you type
- **Fuzzy tab completion**: fzf-tab for better navigation
- **History search**: Ctrl+R for incremental search
- **Git integration**: Enhanced with oh-my-zsh git plugin

---

## 📋 System Verification Checklist

### To Verify Installation:
1. **Shell**: `echo $SHELL` should be `/usr/bin/zsh`
2. **Oh My Zsh**: Check `~/.oh-my-zsh/` exists
3. **Plugins**: Verify in `~/.oh-my-zsh/custom/plugins/`
4. **Mise**: `mise list` should show all runtimes
5. **UV**: `uv --version` should show 0.8.15
6. **Ghostty**: Check `~/.config/ghostty/config`
7. **Project Setup**: `cd ~/Projects/Enviroflow_App` should activate venv

### Key Files to Backup:

**Primary - Managed via chezmoi**:
- `~/.local/share/chezmoi/` - chezmoi source directory (contains all dotfiles)
- `~/dot_files/` - Personal dotfiles git repository

**Individual Files (for reference)**:
- `~/.zshrc` - Main zsh configuration
- `~/.config/ghostty/config` - Terminal configuration
- `~/Projects/Enviroflow_App/mise.toml` - Project mise tasks
- `~/.config/mise/config.toml` - Global mise configuration
- `~/.claude.json` - Claude Code configuration

**Note**: With chezmoi, you only need to backup your dotfiles repository. Everything else can be restored with `chezmoi apply`.

---

## 🚀 Restoration Commands

### Primary Method: chezmoi (Recommended)
After installing Omarchy on a fresh system, restore dotfiles with chezmoi:

```bash
# Install chezmoi if not already installed
sudo pacman -S chezmoi

# Clone your dotfiles repository (if not already set up)
# This is typically done once during initial setup

# Apply all dotfiles
chezmoi apply

# Verify dotfiles are applied
chezmoi status
```

### Manual Restore Script (if chezmoi unavailable):
```bash
# Install core packages
sudo pacman -S zsh zsh-completions ghostty docker docker-compose docker-buildx git github-cli
yay -S lazydocker lazygit asdcontrol-git

# Install Rust tools
cargo install usage-cli

# Install Oh My Zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install custom plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/Aloxaf/fzf-tab ~/.oh-my-zsh/custom/plugins/fzf-tab
npm i -g opencode-ai@latest p
# Install UV
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Copy configuration files from backup
cp ~/.zshrc.backup ~/.zshrc
cp -r ~/.config/ghostty/config.backup ~/.config/ghostty/config
cp ~/.config/mise/config.toml.backup ~/.config/mise/config.toml
```

---

## 📝 Notes

### System Philosophy
- **Tool Separation**: uv manages Python, mise manages venv activation
- **Plugin Management**: Mix of oh-my-zsh standard and custom plugins
- **Theme Consistency**: Gruvbox dark across terminal and tools
- **Workflow Optimization**: Extensive aliases for development efficiency

### Maintenance Tips
- **Dotfiles**: `chezmoi add ~/.config/some-file` to track new configs, then `chezmoi apply` to update
- Regular updates: `sudo pacman -Syu` && `yay -Syu`
- Plugin updates: Check git repos in `~/.oh-my-zsh/custom/plugins/`
- Runtime updates: `mise upgrade`
- Clean unused: `mise uninstall --all`

### Fresh System Setup Workflow
1. Install Omarchy
2. Install and configure chezmoi
3. Clone dot_files repository to chezmoi source directory
4. Run `chezmoi apply` to restore all configurations
5. Verify setup (check shell, terminal, tools)
6. Commit any system-specific changes back to dotfiles

### Setup Chinese
- use `rime` for fx
---
title: Dot Files
---

- using [[Chezmoi]] to manage dotfiles, seems nice and straight forward

---

## Dotfiles Saved in My Chezmoi Repo

Below is a summary of the actual dotfiles and configuration directories I have saved in my chezmoi repo, along with their sources and purposes:

### Top-Level Dotfiles

- **.spacemacs**  
  Source: Spacemacs  
  Purpose: Main configuration for Spacemacs editor (Emacs distribution).

- **.tmux.conf**  
  Source: tmux  
  Purpose: Custom configuration for tmux terminal multiplexer.

- **.wezterm.lua**  
  Source: wezterm  
  Purpose: Configuration for wezterm terminal emulator.

- **.zshrc**  
  Source: Zsh  
  Purpose: Zsh shell configuration (aliases, environment, plugins).

### Fonts

- **.local/share/fonts/**  
  Source: Various Nerd Fonts, Proxima Nova, Inconsolata, Roboto Mono, Space Mono, etc.  
  Purpose: Custom fonts for terminal and editor use.

### Application Configs (under `.config/`)

- **chezmoi/chezmoi.toml**  
  Source: chezmoi  
  Purpose: Chezmoi’s own configuration file.

- **ghostty/config & ghostty/themes/**  
  Source: Ghostty terminal emulator  
  Purpose: Terminal settings and a large collection of color themes.

- **helix/**  
  Source: Helix editor  
  Purpose: Editor configuration and language settings.

- **kitty/**  
  Source: Kitty terminal emulator  
  Purpose: Terminal configuration and theme management.

- **lazygit/**  
  Source: LazyGit  
  Purpose: Configuration for the LazyGit terminal UI.

- **lvim/**  
  Source: LunarVim  
  Purpose: Configuration for LunarVim (Neovim distribution).

- **nushell/**  
  Source: Nushell  
  Purpose: Shell configuration for Nushell.

- **nvim/**  
  Source: Neovim  
  Purpose: Main Neovim configuration.

- **nvim.vanila/**  
  Source: Neovim  
  Purpose: Minimal/vanilla Neovim configuration.

- **ranger/**  
  Source: Ranger  
  Purpose: File manager configuration.

- **starship.toml**  
  Source: Starship  
  Purpose: Prompt configuration for Starship cross-shell prompt.

- **zed/**  
  Source: Zed editor  
  Purpose: Editor configuration.

### Scripts

- **scripts/**  
  Source: Personal  
  Purpose: Custom scripts for automation or setup.

---

These files are all stored in the chezmoi source directory (`~/.local/share/chezmoi`) and are managed, versioned, and deployed to my system using chezmoi. This setup ensures my development environment, terminal, editors, and fonts are consistent and portable across machines.

---





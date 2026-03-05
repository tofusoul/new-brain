# Yazi File Manager

Yazi is a terminal file manager, written in Rust, that is extremely fast and customizable. It uses asynchronous I/O and aims to provide a modern and efficient file management experience in the terminal.

## Installation

You can install Yazi through various package managers. For example, on Arch Linux, you can use:

```bash
pacman -S yazi
```

Refer to the official Yazi documentation for other installation methods.

## Keybindings

Yazi uses vim-like keybindings. Here are some of the most common ones:

### Navigation

| Key(s) | Action |
|---|---|
| `h`, `j`, `k`, `l` | Move left, down, up, right |
| `Arrow Keys` | Alternative navigation |
| `Enter` or `o` | Open file or enter directory |
| `h` (in a directory) | Go to parent directory |
| `gg` | Go to the top of the file list |
| `G` | Go to the bottom of the file list |
| `gh` | Go to home directory (`~`) |
| `.` | Toggle hidden files |
| `~` or `F1` | Show help menu |
| `q` | Quit Yazi |
| `Q` | Quit without changing directory |

### File Operations

| Key(s) | Action |
|---|---|
| `y` | Yank (copy) selected files |
| `x` | Cut (move) selected files |
| `p` | Paste files |
| `P` | Paste files (overwrite) |
| `d` | Delete selected files (to trash) |
| `D` | Permanently delete selected files |
| `r` | Rename selected file(s) |
| `a` | Create a new file or directory (`/` at the end for directory) |
| `cc` | Copy the complete file path |
| `cn` | Copy the filename |
| `cd` | Copy the directory path |

### Searching and Filtering

| Key(s) | Action |
|---|---|
| `f` | Filter files in the current directory |
| `s` | Search for a file by name |
| `S` | Search for content within files |
| `/` | Find next match |
| `n` / `N` | Find next / previous match |
| `Ctrl + s` | Cancel search |

### Tabs

| Key(s) | Action |
|---|---|
| `t` | Open a new tab |
| `1-9` | Switch to a specific tab |
| `[` / `]` | Switch to previous/next tab |
| `{` / `}` | Swap current tab with previous/next tab |
| `Ctrl + c` | Close current tab |

## Configuration

Yazi is configured through TOML files located in `~/.config/yazi/`.

1.  **Create the configuration directory:**
    ```bash
    mkdir -p ~/.config/yazi
    ```

2.  **Create the main configuration files:**
    ```bash
    touch ~/.config/yazi/yazi.toml
    touch ~/.config/yazi/keymap.toml
    touch ~/.config/yazi/theme.toml
    ```

3.  **Populate with defaults:** You can copy the default configurations from the Yazi GitHub repository to get started.

### `yazi.toml`

This file is for general settings, like layout, sorting, and file openers.

### `keymap.toml`

Customize your keybindings in this file. You can add or override the default keybindings.

### `theme.toml`

Define the color scheme and appearance of Yazi.

## Tips and Tricks

*   **Shell Wrapper:** Set up a shell wrapper to automatically `cd` into the last directory you were in when you quit Yazi. You can find instructions for this in the official documentation.
*   **Open with:** You can configure Yazi to open different file types with specific applications in your `yazi.toml`.
*   **Task Manager:** Use `W` to open the task manager and see the progress of file operations.

# My Linux Setup

This document outlines the setup steps for the various software packages and tools I use on my system. It's generated based on my command history and serves as a personal "what I did after installing" guide for Fedora Linux.

## Installation on Fedora Silverblue / Immutable

For immutable systems like Fedora Silverblue, the installation process is different. Here's a general guide:

*   **System-level packages:** Use `rpm-ostree` to layer packages that need to be part of the core OS. This is good for things like shell environments or system services.
    ```bash
    rpm-ostree install <package-name>
    ```
*   **GUI Applications:** Use Flatpak whenever possible.
    ```bash
    flatpak install flathub <app-id>
    ```
*   **Development Environments:** Use `distrobox` or `toolbox` to create mutable containerized environments for your development tools and projects. This keeps your base system clean.
    ```bash
    distrobox create --name my-dev-box --image fedora:latest
    distrobox enter my-dev-box
    ```
    Inside the box, you can use `dnf` or other package managers as you would on a standard system.

## Shell & Terminal

### Zsh

**Installation**
```bash
sudo dnf install zsh
```

**Configuration**
Set Zsh as your default shell:
```bash
chsh -s $(which zsh)
```
On Silverblue, you may need to use `lchsh` or manually edit `/etc/passwd` after layering `util-linux` (`rpm-ostree install util-linux`). A more robust method is:
```bash
sudo usermod --shell $(which zsh) $USER
```

### Oh My Zsh

**Installation**
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Starship

**Installation**
```bash
curl -sS https://starship.rs/install.sh | sh
```

**Configuration**
Add to `~/.zshrc`:
```bash
eval "$(starship init zsh)"
```

### Zoxide

**Installation**
sudo dnf install zoxide
```

**Configuration**
Add to `~/.zshrc`:
```bash
eval "$(zoxide init zsh)"
```

### Eza

**Installation**
```bash
sudo dnf install eza
```

### Nushell

**Installation**
```bash
sudo dnf install nushell
```

## Languages & Runtimes

### Go

**Installation**
```bash
sudo dnf install golang
```

### Python

Python is pre-installed. For managing packages and virtual environments, `uv` is recommended.

### Node.js (via NVM)

Using nvm (Node Version Manager) is recommended for managing multiple versions:
1.  Install nvm:
    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    ```
2.  Install the latest LTS version of Node.js:
    ```bash
    nvm install --lts
    ```

### Rust

The recommended way to install Rust is using `rustup`.
```bash
sudo dnf install rustup
rustup-init
```
After installation, configure your shell by adding this to `~/.zshrc`:
```bash
source "$HOME/.cargo/env"
```

### Zig

**Installation**
```bash
sudo dnf install zig
```

## Development Tools

### Atuin

**Installation**
```bash
curl --proto '=https' --tlsv1.2 -LsSf https://setup.atuin.sh | sh
```

### bat

**Installation**
```bash
sudo dnf install bat
```

### chezmoi

**Installation**
```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
```

### lazygit

**Installation**
```bash
sudo dnf copr enable atim/lazygit -y
sudo dnf install lazygit
```

### Neovim

**Installation**
```bash
sudo dnf install -y neovim python3-neovim
```

### ripgrep

**Installation**
```bash
sudo dnf install ripgrep
```

### fd

**Installation**
```bash
sudo dnf install fd-find
```

### fzf

**Installation**
```bash
sudo dnf install fzf
```

### GitHub CLI (gh)

**Installation**
```bash
sudo dnf install dnf5-plugins
sudo dnf config-manager addrepo --from-repofile=https://cli.github.com/packages/rpm/gh-cli.repo
sudo dnf install gh --repo gh-cli
```
After installation, authenticate:
```bash
gh auth login
```

### uv (Python Packaging)

**Installation**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### nmap

**Installation**
```bash
sudo dnf install nmap
```

### bottom (btm)

**Installation**
```bash
cargo install bottom --locked
```

### Turso CLI

**Installation**
```bash
curl -sSfL https://get.tur.so/install.sh | bash
```

### ublue Developer Tools

The ublue images come with a variety of pre-installed tools. Since you opted not to include the standard ones, this section is a placeholder. You can add tools here as needed.

## GUI Applications & Editors

### Zed

**Installation**
```bash
curl -f https://zed.dev/install.sh | sh
```

### Cursor

Cursor is available as an AppImage. Download it from the official website and make it executable.
```bash
# Example
chmod +x Cursor-*.AppImage
./Cursor-*.AppImage
```

### Ghostty

**Installation (from source)**
```bash
git clone https://github.com/ghostty-org/ghostty
cd ghostty
zig build -Doptimize=ReleaseFast
# Follow further instructions from the repository
```

## Services & Daemons

### Docker

**Installation**
1.  Set up the Docker repository:
    ```bash
    sudo dnf -y install dnf-plugins-core
    sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
    ```
2.  Install Docker Engine:
    ```bash
    sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
    ```
3.  Start and enable Docker:
    ```bash
    sudo systemctl start docker
    sudo systemctl enable docker
    ```
**Post-installation**
Add your user to the `docker` group to run commands without `sudo`:
```bash
sudo usermod -aG docker $USER
```
(You will need to log out and log back in for this to take effect.)

### Tailscale

**Installation**
1.  Add the Tailscale repository:
    ```bash
    sudo dnf config-manager --add-repo https://pkgs.tailscale.com/stable/fedora/tailscale.repo
    sudo dnf install tailscale -y
    ```
**Configuration**
1.  Start the Tailscale service:
    ```bash
    sudo systemctl enable --now tailscaled
    ```
2.  Connect to your Tailscale network:
    ```bash
    sudo tailscale up
    ```
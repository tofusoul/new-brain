# What I do

This document outlines the setup steps for the various software packages and tools I use on my system. It's generated based on my command history and serves as a personal "what I did after installing" guide.

## Shell & Terminal

### Zsh

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install zsh
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install zsh
    ```

**Configuration**

After installation, set Zsh as your default shell:
```bash
chsh -s $(which zsh)
```

### Oh My Zsh

**Installation**

You can install Oh My Zsh using `curl` or `wget`:

*   **curl:**
    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```
*   **wget:**
    ```bash
    sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
    ```

### Starship

**Installation**

*   **Homebrew (macOS/Linux):**
    ```bash
    brew install starship
    ```
*   **Script (Linux/macOS):**
    ```bash
    curl -sS https://starship.rs/install.sh | sh
    ```

**Configuration**

Add the following to the end of your `~/.zshrc` file:
```bash
eval "$(starship init zsh)"
```

### Zoxide

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install zoxide
    ```
*   **Ubuntu:**
    ```bash
    sudo apt install zoxide
    ```
*   **Script (Linux/WSL):**
    ```bash
    curl -sS https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | bash
    ```

**Configuration**

Add the following to the end of your `~/.zshrc` file:
```bash
eval "$(zoxide init zsh)"
```

### Eza

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install eza
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install eza
    ```

## Languages & Runtimes

### Go

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install golang
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install golang-go
    ```
*   **Manual (for latest version):**
    1.  Download the latest version from [https://go.dev/dl/](https://go.dev/dl/).
    2.  Extract the archive to `/usr/local`:
        ```bash
        sudo tar -C /usr/local -xzf go<VERSION>.linux-amd64.tar.gz
        ```
    3.  Add Go to your PATH in `~/.zshrc`:
        ```bash
        echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.zshrc
        ```

### Python

Python is typically pre-installed. If not, you can install it:

*   **Fedora:**
    ```bash
    sudo dnf install python3
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install python3
    ```

### Node.js

*   **Fedora:**
    ```bash
    sudo dnf install nodejs
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install nodejs npm
    ```
*   **Using nvm (Node Version Manager) is recommended for managing multiple versions:**
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

*   **Fedora:**
    ```bash
    sudo dnf install rustup
    rustup-init
    ```
*   **Ubuntu/Script:**
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
After installation, configure your shell:
```bash
source "$HOME/.cargo/env"
```
You should add this to your `~/.zshrc` to make it permanent.

## Development Tools

### Atuin

**Installation**

*   **Script (Recommended):**
    ```bash
    curl --proto '=https' --tlsv1.2 -LsSf https://setup.atuin.sh | sh
    ```
*   **Fedora (Copr):**
    ```bash
    sudo dnf copr enable sramanujam/atuin
    sudo dnf install atuin
    ```
*   **Ubuntu (APT):**
    ```bash
    sudo apt update
    sudo apt install atuin
    ```

### bat

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install bat
    ```
*   **Ubuntu:**
    ```bash
    sudo apt install bat
    ```
    On some Ubuntu versions, the command is `batcat`. You can create a symbolic link:
    ```bash
    mkdir -p ~/.local/bin
    ln -s /usr/bin/batcat ~/.local/bin/bat
    ```

### chezmoi

**Installation**

*   **Script:**
    ```bash
    sh -c "$(curl -fsLS get.chezmoi.io)"
    ```
*   **Fedora (Copr):**
    ```bash
    sudo dnf copr enable lihaohong/chezmoi
    sudo dnf install chezmoi
    ```
*   **Ubuntu (Snap):**
    ```bash
    sudo snap install chezmoi --classic
    ```

### lazygit

**Installation**

*   **Fedora (Copr):**
    ```bash
    sudo dnf copr enable atim/lazygit
    sudo dnf install lazygit
    ```
*   **Ubuntu (PPA):**
    ```bash
    sudo add-apt-repository ppa:lazygit-team/daily
    sudo apt update
    sudo apt install lazygit
    ```

### Neovim

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install -y neovim python3-neovim
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install neovim python3-neovim
    ```

### ripgrep

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install ripgrep
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install ripgrep
    ```

### fd

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install fd-find
    ```
*   **Ubuntu:**
    ```bash
    sudo apt install fd-find
    ```
    On Ubuntu, the command is `fdfind`. You can create an alias in your `~/.zshrc`:
    ```bash
    alias fd=fdfind
    ```

### fzf

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf install fzf
    ```
*   **Ubuntu:**
    ```bash
    sudo apt update
    sudo apt install fzf
    ```

### GitHub CLI (gh)

**Installation**

*   **Fedora:**
    ```bash
    sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
    sudo dnf install gh
    ```
*   **Ubuntu:**
    ```bash
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
    sudo apt update
    sudo apt install gh
    ```
After installation, authenticate with your GitHub account:
```bash
gh auth login
```

### uv

**Installation**

*   **Script (Recommended):**
    ```bash
    curl -LsSf https://astral.sh/uv/install.sh | sh
    ```
*   **pipx:**
    ```bash
    pipx install uv
    ```
*   **pip:**
    ```bash
    pip install uv
    ```

## Services & Applications

### Docker

**Installation**

*   **Fedora:**
    1.  Set up the Docker repository:
        ```bash
        sudo dnf -y install dnf-plugins-core
        sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
        ```
    2.  Install Docker Engine:
        ```bash
        sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
        ```
    3.  Start and enable Docker:
        ```bash
        sudo systemctl start docker
        sudo systemctl enable docker
        ```

*   **Ubuntu:**
    1.  Set up the Docker repository:
        ```bash
        sudo apt-get update
        sudo apt-get install ca-certificates curl gnupg
        sudo install -m 0755 -d /etc/apt/keyrings
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
        sudo chmod a+r /etc/apt/keyrings/docker.gpg
        echo \
          "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
          $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
          sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        ```
    2.  Install Docker Engine:
        ```bash
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
        ```

**Post-installation**

To run Docker commands without `sudo`, add your user to the `docker` group:
```bash
sudo usermod -aG docker $USER
```
You will need to log out and log back in for this to take effect.

### Docker Compose

Docker Compose is now included with Docker Engine as a plugin. See the Docker installation instructions above.

### Tailscale

**Installation**

*   **Script (Recommended):**
    ```bash
    curl -fsSL https://tailscale.com/install.sh | sh
    ```
*   **Fedora:**
    ```bash
    sudo dnf config-manager --add-repo https://pkgs.tailscale.com/stable/fedora/tailscale.repo
    sudo dnf install tailscale
    ```
*   **Ubuntu:**
    ```bash
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/$(lsb_release -cs).noarmor.gpg | sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/$(lsb_release -cs).tailscale-keyring.list | sudo tee /etc/apt/sources.list.d/tailscale.list
    sudo apt-get update
    sudo apt-get install tailscale
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



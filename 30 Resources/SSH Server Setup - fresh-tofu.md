# SSH Server Setup - fresh-tofu

**Created:** 2026-02-23
**Host:** fresh-tofu (desktop computer)
**OS:** Arch Linux

## Setup Steps

```bash
# 1. Enable and start SSH service
sudo systemctl enable --now sshd

# 2. Check if it's running
sudo systemctl status sshd

# 3. Allow SSH through firewall (if using ufw)
sudo ufw allow ssh

# 4. Get your local IP address
ip addr show | grep "inet " | grep -v 127.0.0.1

# 5. Set up SSH keys on your remote machine (do this FROM the machine you'll connect FROM)
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id tofu@<IP_ADDRESS_FROM_STEP_4>

# 6. (Optional but recommended) Disable password authentication after keys work
sudo nano /etc/ssh/sshd_config
# Find and change: PasswordAuthentication no
# Save and restart: sudo systemctl restart sshd
```

## Connection Commands

```bash
# From remote machine
ssh tofu@<IP_ADDRESS>

# Or with custom port if configured
ssh -p <PORT> tofu@<IP_ADDRESS>
```

## Notes

- OpenSSH is already installed (version 10.2p1-2)
- User account: `tofu`
- Hostname: `fresh-tofu`
- Keys: Ed25519 recommended for better security

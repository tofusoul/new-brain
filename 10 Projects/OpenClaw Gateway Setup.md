---
Type: Project
Status: active
Created: 2026-01-31
---

# 🔧 OpenClaw Gateway Setup

**Goal:** Configure OpenClaw Gateway for remote access and channel management

---

## 📋 Tasks

### ✅ Completed
- [x] Install OpenClaw CLI tools (obsidian-cli, clawdhub)
- [x] Set up Bean's identity (SOUL.md, IDENTITY.md)
- [x] Configure Gateway WhatsApp channel
- [x] Create System Status & Onboarding summary note
- [x] Create Bean Onboarding project note
- [x] Fix Daily, Weekly, Monthly Obsidian templates
- [x] Install calendar skill from ClawdHub
- [x] Get ClawdHub working again

### ✅ Completed
- [x] Configure Brave API key for web search
- [x] Test web search via Brave API

### 🚧 In Progress
- [ ] Test Google Calendar access via calendar skill
- [ ] Configure remote access (Tailscale or VPN)
- [ ] Test Gateway dashboard from local network

### 📥 Backlog
- [ ] Design capture flow (Nothing Phone/Keep → Obsidian)
- [ ] Simplify task queries in Obsidian (fix or replace with manual checkboxes)
- [ ] Set up Telegram bot for remote access
- [ ] Explore event sources for Christchurch
- [ ] Create daily review automation
- [ ] Document "system death" prevention strategies

---

## 📝 Notes

### Gateway URL (Local)
- **Default:** `http://127.0.0.1:18789` (localhost)
- **Notes:** Works on devices on same local network
- **Remote access requires:** Tailscale tunnel or VPN connection

### Gateway URL (Remote)
- Configure via Tailscale or VPN
- URL will be accessible from any network

### Tailscale Setup (if needed)
1. Install Tailscale on your Linux server (homelab)
2. Enable HTTPS connection
3. Configure port forwarding for Gateway port (18789)
4. Update Gateway config with remote auth token

### Channel Configuration
- **WhatsApp:** ✅ Connected and working
- **Telegram:** Setup via @BotFather + HTTP API token
- **Google Assistant:** Optional future integration

### Key Documentation
- [OpenClaw Docs](https://docs.openclaw.ai)
- [Gateway Configuration](https://docs.openclaw.ai/gateway/configuration)
- [Remote Access](https://docs.openclaw.ai/gateway/remote)
- [Telegram Integration](https://docs.openclaw.ai/channels/telegram)

---

## 🔗 Related Notes

- [[Bean Onboarding]] — Overall onboarding project
- [[System Status & Onboarding]] — Tools and configuration summary
- [[Gateway]] — OpenClaw Gateway setup and configuration
- [[Obsidian Setup]] — Vault structure and PARA methodology

---

## 💡 Why This Matters

OpenClaw Gateway provides:
- **Remote access** to Andrew from anywhere
- **Channel management** (WhatsApp, Telegram, etc.)
- **Web UI dashboard** for configuration
- **Browser control** via Chrome extension
- **Skill management** via ClawdHub

This setup completes the foundation for Bean to be a truly omnipresent assistant.

*Last updated: 2026-01-31*

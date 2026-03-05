# Syncthing Setup & Maintenance

**Status:** ✅ Active and syncing
**Devices:** 2 (fresh-tofu + nothing/phone)
**Primary folder:** new_brain (~/new_brain)

---

## Device Configuration

### fresh-tofu (Desktop)
- **Device ID:** `B6IWXIA-AQCIGNR-VCB2STL-DOCOCOV-C7HNGVO-OVCSG4Q-NXPZIIA-3TN5AQZ`
- **Address:** Dynamic
- **Connection:** Local network (192.168.1.8:22000)
- **OS:** Linux (Arch/Omarchy)

### nothing (Phone)
- **Device ID:** `PXZQEHH-34V2NSL-7IQP7XP-4R7F6MP-JSERIQA-ZH462XF-JYPPUML-EAUZMAA`
- **Address:** Dynamic
- **Connection:** TCP via TLS 1.3
- **Client version:** v2.0.13

---

## Folder Configuration

### new_brain (Primary Vault)
- **Folder ID:** `jhxpr-trcg7`
- **Path:** `~/new_brain`
- **Type:** Send & Receive
- **Rescan interval:** 3600s (1 hour)
- **FS watcher:** Enabled (10s delay)
- **Auto normalize:** Enabled
- **Marker:** `.stfolder`
- **Size:** ~200 MB

### Other Folders
(None currently - add as needed)

---

## .stignore File

Location: `~/new_brain/.stignore`

### Purpose
Prevent machine-specific and volatile files from syncing to avoid conflicts.

### Current Patterns

```ignore
# Obsidian workspace files (UI state, cursor positions, open files)
.obsidian/workspace
.obsidian/workspace-mobile
.obsidian/workspace.json

# Obsidian plugin data (volatile state, changes constantly)
.obsidian/plugins/*/data
.obsidian/plugins/*/data.json
.obsidian/plugins/*/*.sync-conflict-*

# BRAT plugin cache (plugin downloads)
.obsidian/plugins/obsidian42-brat/plugins/

# Syncthing conflict cleanup
*.sync-conflict-*

# Operating system files
.DS_Store
Thumbs.db
Desktop.ini

# Editor/IDE files
*.swp
*.swo
*~
.vscode/
.idea/

# Temporary files
*.tmp
*.bak
*.orig
```

### What Shouldn't Sync

**Machine-specific files:**
- Obsidian workspace state (different on each device)
- Plugin data files (change independently)
- Editor temp files
- OS metadata

**Why:**
These files change constantly and independently on each device. Syncing them causes endless conflicts and overwrites useful local state.

### What Should Sync

✅ **Sync these:**
- Markdown notes (`.md`)
- Images and attachments
- PDFs and other documents
- Plugin settings/config (not data)
- Canvas files (`.canvas`)
- `.obsidian/` config files (except workspace/data)

❌ **Don't sync these:**
- `.obsidian/workspace*`
- `.obsidian/plugins/*/data.json`
- `.obsidian/plugins/*/data/` directories
- `.sync-conflict-*` files

---

## Maintenance Tasks

### Regular Checks
- [ ] Review conflict files in folder
- [ ] Check .stignore patterns still appropriate
- [ ] Verify folder sizes aren't exploding
- [ ] Test new apps don't create conflicts

### When Conflicts Appear
1. Identify what type of file is conflicting
2. Decide if it should sync or be ignored
3. Add to `.stignore` if needed
4. Clean up conflict files
5. Trigger reindex: `curl -H "X-API-Key: $KEY" -X POST http://127.0.0.1:8384/rest/db/scan?folder=FOLDER_ID`

---

## Incidents

### 2026-01-30: 16 Sync Conflicts Resolved

**Issue:**
16 sync conflict files in new_brain vault from Obsidian workspace and plugin data syncing between devices.

**Root Cause:**
Obsidian was syncing:
- `.obsidian/workspace` - open files, cursor positions, window state
- `.obsidian/plugins/obsidian-day-planner/data` - plugin state files

These change constantly on each device independently, causing conflicts.

**Resolution:**
1. Created `.stignore` file with appropriate patterns
2. Deleted 16 conflict files:
   - 6 `workspace.sync-conflict-*` files
   - 10 `obsidian-day-planner/data.sync-conflict-*` files
3. Triggered Syncthing reindex
4. Verified sync status: idle, no errors

**Lessons:**
- Always add `.stignore` to Obsidian vaults with multiple devices
- Workspace and plugin data files should NEVER sync
- Plugin settings (manifests, config) are OK; plugin data is not

---

## Troubleshooting

### Syncthing Not Starting
```bash
systemctl --user start syncthing
systemctl --user enable syncthing  # Start on boot
```

### Check Sync Status
```bash
# Connection status
curl -H "X-API-Key: qXpSnU5UFyotqLZMTQb5r7EWJ3T4AYwx" \
  -s http://127.0.0.1:8384/rest/system/connections

# Folder status
curl -H "X-API-Key: qXpSnU5UFyotqLZMTQb5r7EWJ3T4AYwx" \
  -s http://127.0.0.1:8384/rest/db/status?folder=jhxpr-trcg7
```

### Find Conflict Files
```bash
find ~/new_brain -name "*.sync-conflict-*"
```

### Clean Up Conflicts
```bash
find ~/new_brain -name "*.sync-conflict-*" -delete
```

### Trigger Rescan
```bash
curl -H "X-API-Key: qXpSnU5UFyotqLZMTQb5r7EWJ3T4AYwx" \
  -X POST http://127.0.0.1:8384/rest/db/scan?folder=jhxpr-trcg7
```

### Access Web UI
```
http://127.0.0.1:8384
```

---

## Syncthing Configuration

### Service
- **Location:** `/usr/lib/systemd/user/syncthing.service`
- **Status:** Enabled (auto-start)
- **Command:** `/usr/bin/syncthing serve --no-browser --no-restart`

### Web UI
- **Address:** `127.0.0.1:8384`
- **TLS:** Disabled
- **API Key:** `qXpSnU5UFyotqLZMTQb5r7EWJ3T4AYwx`
- **Theme:** Default

### Options
- Global announce: Enabled
- Local announce: Enabled
- Relays: Enabled
- NAT traversal: Enabled
- Auto-upgrade: Every 12 hours
- Start browser: True

---

## References

- Syncthing docs: https://docs.syncthing.net
- Ignore patterns: https://docs.syncthing.net/users/ignoring.html
- Obsidian + Syncthing guide: (search web for latest)

---

*Last updated: 2026-01-30 17:10*

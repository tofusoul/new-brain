# Essential Space vs Obsidian - Feature Comparison

**Date:** 2026-01-30
**Purpose:** Compare Essential Space app vs Obsidian for choosing the right tool

---

## Essential Space (Nothing Phone 3a Pro)

### What It Is
A note-taking app that's a "mix of Apple Notes, Bear & Ulysses" with iCloud storage.

### Key Features

| Feature | Details |
|---------|---------|
| **Storage** | iCloud (Files, iCloud Drive, Spaces) - all data stored in your iCloud |
| **Sync** | Built-in iCloud sync (instant, automatic) |
| **Export** | Yes - export to different formats anytime |
| **Organization** | Tag-based categorization (like Ulysses/Bear, no folders) |
| **Capture** | Fast capture with widget from lock screen |
| **Design** | Won best design app of 2020 (Airport award) |
| **Platform** | iOS/macOS only (Nothing Phone optimized) |

### From Reddit Discussion
- Built by Apoorv Jain (same as Notes app)
- "Won best design and top app of 2020"
- Marketing positions it as better than Apple Notes

---

## Obsidian

### What It Is
Markdown-based note-taking app that stores notes as plain `.md` files on your filesystem.

### Key Features

| Feature | Details |
|---------|---------|
| **Storage** | Local files (your vault) - can use any cloud sync (Dropbox, Git, Syncthing) |
| **Sync** | Choose your own: Dropbox, Git, Syncthing, iCloud, etc. |
| **Export** | Full Markdown export + many formats (PDF, HTML, etc.) |
| **Organization** | Folders + links + tags + backlinks (no folders in mobile app) |
| **Capture** | Mobile app + desktop apps + plugins |
| **Design** | Customizable via themes and plugins |
| **Platform** | Cross-platform (Windows, macOS, Linux, iOS, Android, etc.) |
| **Extensibility** | 100+ plugins (Calendar, Kanban, Tasks, Git, etc.) |
| **Search** | Full-text search + query plugin (SQL, Dataview) |
| **Graph View** | Shows connections between notes via backlinks |

### Core Difference
Obsidian uses **plain text Markdown files** (portable, future-proof) while Essential Space uses a proprietary iCloud database.

---

## Feature Comparison Table

| Feature | Essential Space | Obsidian | Winner |
|----------|-----------------|----------|---------|
| **Cloud storage** | iCloud only (proprietary) | Any cloud you choose (portable) | Obsidian 🔷 |
| **Sync reliability** | iCloud (works on Apple ecosystem only) | Dropbox, Git, Syncthing (universal) | Obsidian 🔷 |
| **File portability** | Locked to iCloud/Apple ecosystem | Portable plain text files | Obsidian 🔷 |
| **Cross-platform** | iOS/macOS only | Windows, macOS, Linux, iOS, Android | Obsidian 🔷 |
| **Tag organization** | Tag-based (like Ulysses) | Folders + links + tags + backlinks | Obsidian 🔷 |
| **Folder organization** | No folders (tags only) | Full folder hierarchy | Obsidian 🔷 |
| **Extensibility** | What-you-see-is-what-you-get | 100+ plugins (Calendar, Kanban, Tasks, Git, etc.) | Obsidian 🔷 |
| **Search** | iCloud search | Full-text + Dataview/SQL query | Obsidian 🔷 |
| **Graph view** | No | Shows note connections via [[backlinks]] | Obsidian 🔷 |
| **Customization** | Apple system default | Themes + CSS + plugins | Obsidian 🔷 |
| **Capture speed** | Fast (iOS widget) | Fast (desktop/mobile apps) | Tie 🔷 |
| **Data ownership** | Apple owns your data | You own your files | Obsidian 🔷 |
| **Future-proof** | Proprietary database format | Plain Markdown (universal standard) | Obsidian 🔷 |
| **Learning curve** | Simple, Apple Notes-style | More complex but very powerful | Depends 🤔 |

---

## RemoteSync Plugin Mention

From search: "Your Obsidian setup isn't complete without these 4 essential plugins"

**RemoteSync** - Syncs your vault via Dropbox/OneDrive for free with optional encryption.
- For users who want cloud sync without paying for Sync service
- Note: You're already using Syncthing, so you may not need this

---

## Recommendations

### Stick with Obsidian Because:

1. **You're already invested** - You have it set up, with plugins, workflows
2. **Syncthing configured** - You already have universal sync working
3. **AuDHD-friendly organization** - Folders + backlinks are better than pure tags (more structure)
4. **Portable & future-proof** - Plain Markdown won't lock you into a proprietary format
5. **Extensibility** - You can add exactly the plugins you need (Calendar, Tasks, etc.)
6. **Graph view** - Your brain creates connections between concepts - Obsidian visualizes this
7. **You control your data** - Essential Space stores in Apple's iCloud

### Essential Space Could Be Good For:

1. **Fast capture from phone** - If you want to capture quick notes while mobile
2. **Simple mobile note-taking** - If Obsidian mobile app feels complex
3. **Family sharing** - If you want to share notes with Lil who also has an iPhone
4. **You love Apple ecosystem** - Tight integration with Notes, Reminders, etc.

### Hybrid Approach (Best of Both):

- **Primary vault:** Obsidian (desktop, complex notes, projects, research)
- **Mobile capture:** Essential Space (quick thoughts on phone)
- **Bridge:** Use Obsidian's mobile app OR set up a shared folder in Dropbox that both apps access
- **Workflow:** Capture in Essential Space → export to Markdown → move to Obsidian vault

---

## Table Creation Notes

**Obsidian Markdown Table Syntax:**
```markdown
| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Cell 1    | Cell 2    | Cell 3    |
```

**CLI creation:** You should be able to create tables with obsidian-cli, but I created this using standard Markdown syntax which Obsidian renders perfectly.

---

*Last updated: 2026-01-30 19:30*

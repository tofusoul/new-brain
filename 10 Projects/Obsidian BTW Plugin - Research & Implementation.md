# Obsidian BTW Plugin - Research & Implementation

**Status:** 🔄 Research Phase
**Purpose:** Create an Obsidian plugin that lets me quickly point to any part of Obsidian (notes, settings, folders) during conversations

---

## What BTW Means

**BTW** = **"By The Way"** - Quick reference or side comment during conversations

**Examples:**
- "BTW, dotfiles are in `~/.local/share/chezmoi/`"
- "BTW, the workspace script is in `.local/bin/`"
- "BTW, check Tasks section for dotfiles decisions"

**Problem:** No easy way to make these references clickable or searchable without opening whole notes

---

## Plugin Concept

**Core Idea:** A quick-access panel that shows all important Obsidian locations and actions

### Panel Components

1. **Quick Reference** - Pre-saved links to frequently referenced areas:
   - Tasks: `[[00 Periodic/Tofurky Tasks & Questions]]`
   - Dotfiles: `[[10 Projects/Dotfiles Overhaul - fresh-tofu]]`
   - Projects: `[[10 Projects]]`
   - System: `[[20 Areas - System]]`

2. **Context Management** - When Andrew mentions a topic, show relevant notes
   - Andrew: "What about the dotfiles?"
   - Tofurky: Search for dotfiles, open relevant note
   - Quick filters (today's notes, last 7 days, by project)

3. **Chat Integration** - Log BTW references during conversations
   - Auto-capture to "Conversation Log" note
   - Timestamp each reference
   - Group by conversation session

4. **Bookmarks** - Favorite or frequently accessed notes
   - Quick-open without searching
   - Custom organization

---

## Technical Approach

### Option 1: Simple Obsidian Commands (Easiest, Limited)

```javascript
// Use Obsidian's built-in commands plugin
// Command: "Quick Reference Panel"
// When triggered, opens search dialog with pre-filled query

obsidian.commands.executeCommandById("quick-reference");
```

**Pros:**
- Easy to implement (just configuration)
- Works on desktop and mobile
- No plugin development needed

**Cons:**
- No persistent panel
- Must re-trigger search for each reference
- No bookmarks/favorites

### Option 2: Minimal Plugin (Balanced, Recommended)

```javascript
// Obsidian Plugin API
// Create a right-hand panel with sections
// Register custom view

class QuickRefPlugin extends Plugin {
  onload() {
    // Add ribbon icon
    // Register command: "Open Quick Reference"
    // Create workspace leaf for panel
  }
}
```

**Panel Features:**
- Search input
- Saved links (clickable)
- Bookmarks section
- Chat log viewer
- Customizable order

**Pros:**
- Persistent panel (always available)
- Built-in Obsidian navigation
- Full plugin control
- Can add bookmarks/favorites
- Works on desktop

**Cons:**
- Requires plugin development
- Mobile Obsidian has limited plugin support
- Installation across devices

### Option 3: External Service + Obsidian URI (Most Powerful, Most Complex)

```javascript
// Create local web service or electron app
// Expose HTTP endpoint for quick access
// Use obsidian:// protocol to open specific notes

// Example service
// GET /quickref?type=tasks
// Response: obsidian://open?vault=/path/to/vault&file=00%20Periodic/Tofurky%20Tasks%20%26%20Questions.md

obsidian.app.openInternalLink("obsidian://open?path=Notes/Tasks");
```

**Pros:**
- Extremely powerful (custom UI, database, features)
- Works from any app
- Can add real-time updates
- Can integrate with chat directly

**Cons:**
- Most complex to build
- Security considerations
- Needs Obsidian running
- Latency (network call vs instant)

---

## Recommended Approach

**Start with Option 2 (Minimal Plugin)**

### Phase 1: Setup & Basic Functionality
1. [ ] Study Obsidian Plugin API documentation
2. [ ] Research existing quick-access plugins
3. [ ] Set up plugin development environment
4. [ ] Create plugin skeleton with workspace leaf
5. [ ] Add ribbon icon
6. [ ] Register command "Open Quick Reference"

### Phase 2: Core Features
1. [ ] Implement search input
2. [ ] Add static links (Tasks, Projects, etc.)
3. [ ] Implement bookmarks (save/remove)
4. [ ] Add chat log (manual entry)
5. [ ] Test on desktop

### Phase 3: Chat Integration
1. [ ] Add "Log Reference" action (BTW mentions)
2. [ ] Auto-capture with timestamp
3. [ ] Store in "Conversation Log" note
4. [ ] Add quick-open from chat log

### Phase 4: Polish & Enhancement
1. [ ] Add themes (Gruvbox)
2. [ ] Keyboard shortcuts
3. [ ] Export chat log
4. [ ] Mobile testing (Obsidian mobile plugin limitations)
5. [ ] Documentation

---

## Mockup / Design

```
┌─────────────────────────────────┐
│ Quick Reference Panel              │
├─────────────────────────────────┤
│ 🔍 Search:                      │
│ [__________________] [Search]   │
├─────────────────────────────────┤
│ ⭐ Bookmarks                    │
│ [Tasks] [Projects] [Dotfiles]  │
├─────────────────────────────────┤
│ 📂 Quick Links                   │
│ [00 Periodic]                   │
│ [10 Projects]                    │
│ [20 Areas - System]             │
├─────────────────────────────────┤
│ 💬 Chat Log                      │
│ • Tasks (Jan 30, 7:30pm)       │
│ • Dotfiles (Jan 30, 7:45pm)    │
│ • Dotfiles (Jan 30, 7:48pm)    │
└─────────────────────────────────┘
```

---

## Alternative: Built-in Obsidian Commands (Fallback)

If plugin development is too complex, use built-in features:

### Quick Commands
Create commands that open frequently referenced notes:

```yaml
# Obsidian Commands Plugin
commands:
  - id: open-tasks
    name: Open Tasks
    action: open
    target: 00 Periodic/Tofurky Tasks & Questions

  - id: open-dotfiles
    name: Open Dotfiles
    action: open
    target: 10 Projects/Dotfiles Overhaul - fresh-tofu

  - id: open-projects
    name: Open Projects
    action: open
    target: 10 Projects

  - id: open-system
    name: Open System Settings
    action: open
    target: 20 Areas - System
```

**Access:**
- `Ctrl+P` → Open command palette
- Type "Tasks", "Dotfiles", etc.
- Enter → Opens note instantly

### Hotkeys
Assign keyboard shortcuts:

```yaml
hotkeys:
  - key: ctrl+shift+t
    command: open-tasks

  - key: ctrl+shift+d
    command: open-dotfiles

  - key: ctrl+shift+p
    command: open-projects
```

---

## Chat Integration Examples

### Manual BTW Capture

**In conversation:**
Tofurky: "BTW, we should update the dotfiles snapshot"
Andrew: "Can you add that to Tasks?"

**In Obsidian:**
1. Tofurky opens Quick Reference panel
2. Types "dotfiles" in search
3. Opens dotfiles note
4. Adds task: "Update snapshot" to Tasks note
5. Closes panel, returns to chat

### Contextual Suggestions

**When Andrew mentions:**
- "Tasks" → Show dotfiles tasks
- "Dotfiles" → Show dotfiles decisions
- "System" → Show system settings
- "Projects" → Show all projects

**Tofurky actions:**
1. Detect mentioned topic (simple keyword matching)
2. Search Quick Reference panel
3. Offer: "Open Tasks? Open Projects? Search system settings?"
4. Log BTW reference with timestamp

---

## Implementation Plan

### Week 1: Research & Setup
1. [ ] Study Obsidian Plugin API docs
2. [ ] Research existing quick-access plugins
3. [ ] Set up plugin development environment
4. [ ] Create plugin skeleton

### Week 2: Core Plugin
1. [ ] Implement basic panel UI
2. [ ] Add search functionality
3. [ ] Add static links
4. [ ] Test on desktop

### Week 3: Bookmarks & Chat
1. [ ] Add bookmarks (save/remove)
2. [ ] Implement chat log
3. [ ] Add "Log Reference" action
4. [ ] Test with real conversations

### Week 4: Polish & Release
1. [ ] Add themes
2. [ ] Add keyboard shortcuts
3. [ ] Mobile testing
4. [ ] Documentation
5. [ ] Share with Andrew

---

## Notes

### Why This Matters
**Problem:** "I want to be able to quickly point to a part of obsidian that I want you to look at and change during conversations"

**This solves:**
- ✅ Quick access to any note/section
- ✅ Context during conversations (BTW mentions)
- ✅ Reduced cognitive load (don't have to remember where things are)
- ✅ One-click opening (no search needed)
- ✅ Chat log (history of what we discussed when)
- ✅ Structured way to reference Obsidian during conversations

### Current Priority
This is **HIGH** priority - Andrew will reference Obsidian frequently during conversations.

---

*Created: 2026-01-30*
*Status: Ready for review*
*Estimated time to basic implementation: 1-2 weeks*

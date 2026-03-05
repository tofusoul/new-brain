# Obsidian Bases - Cross-Channel Memory System

**Status:** 🔄 Setup Phase
**Started:** 2026-01-30
**Purpose:** Track conversations and tasks across ALL channels (WhatsApp, web chat, etc.) in one searchable system

---

## Why Obsidian Bases?

**Current Approach:**
- All conversations tracked in single markdown file: `00 Periodic/Tofurky Tasks & Questions.md`
- This creates problems:
  - No easy search for specific conversations
  - Can't link conversations to related projects
  - Hard to track which channel a conversation happened on
  - WhatsApp is primary channel, but other channels (future) also need tracking

**Obsidian Bases Solution:**
- **Bases = Databases** - Each base is a separate "database" (folder of markdown notes)
- **Search = Global** - Search across ALL bases at once
- **Properties = Structured** - Each note has fields (title, date, channel, tags, etc.)
- **Links = Connections** - Link conversations to projects, tasks, people

**Benefits:**
- ✅ **Full-text search** - Search conversation across all bases
- ✅ **Properties** - Filter by channel, date, project, person
- ✅ **Linked notes** - Connect conversations to tasks/projects
- ✅ **Cross-channel** - WhatsApp, web chat, Discord, Telegram - all in one place
- ✅ **Relationships** - Track what you discussed with Lil, kids, colleagues
- ✅ **Queryable** - "What did we discuss about dotfiles?" → search and find

---

## Obsidian Bases Core Concepts

### 1. Properties
Each base note has properties you define:

**Common Properties:**
- `Title` - Conversation topic
- `Date` - When conversation happened
- `Channel` - WhatsApp, Web Chat, Discord, Telegram, etc.
- `Participants` - Who was involved (Andrew, Lil, kids, etc.)
- `Status` - Active, Completed, Follow-up needed
- `Projects` - Related projects (comma-separated)
- `Tags` - Custom tags (comma-separated)
- `Importance` - Low, Medium, High
- `Summary` - Brief description

### 2. Links
- **Backlinks:** `[[Note Name]]` - link to related notes
- **Alias:** `[Displayed Name|note-name]` - alternative names

### 3. Relationships
- Bases show related notes graphically
- "Linked mentions" - which notes reference each other
- Use for connecting conversations to projects, tasks, resources

### 4. Templates
- Create default note templates for quick conversation capture
- Define which properties to fill automatically

### 5. Daily Notes
- Create a "Today's Conversations" daily note for quick capture
- Link to base notes for detailed tracking

---

## Setup Plan

### Phase 1: Create Base Structure

1. **Create base folders:**
   ```
   /home/tofu/new_brain/
   ├── 50 Bases/                    # All bases
   │   ├── conversations/             # Individual conversations
   │   ├── people/                  # People profiles
   │   ├── projects/                # Project tracking
   │   └── daily/                  # Daily summaries
   └── .obsidian/
       └── plugins/
           └── obsidian-bases/      # Install Bases plugin
   ```

2. **Install Obsidian Bases:**
   - Search for "Obsidian Bases" plugin in Obsidian
   - Install via "Third-party plugins" search
   - Community plugins → Search "obsidian-bases"
   - Enable and configure

### Phase 2: Define Templates

**Conversation Note Template:**
```yaml
---
title: "{{date}}: {{topic}}"
date: "{{date}}"
channel: "{{channel}}"
participants: "{{participants}}"
status: "Active"
projects: []
importance: "Medium"
tags: [conversation, {{channel}}]
created: "{{timestamp}}"
---
# Conversation Summary

## Topic: {{topic}}

### Participants
{{participants}}

### Key Points
{{key_points}}

### Decisions Made
{{decisions}}

### Action Items
{{action_items}}

### Resources Mentioned
{{resources}}

### Next Steps
{{next_steps}}
---
```

**Person Note Template:**
```yaml
---
name: "{{person}}"
role: "{{role}}" # spouse, child, colleague, friend, etc.
relationship: "{{relationship}}"
contact_info: "{{contact}}"
created: "{{timestamp}}"
---
# {{name}} - {{role}}

## Contact Information
- **Phone:** {{phone}}
- **Email:** {{email}}
- **Address:** {{address}}

## Notes
- **First met:** {{first_met}}
- **Family:** {{family_details}}
- **Work:** {{work_details}}
- **Interests:** {{interests}}
- **Key conversations:**
  - [[Date: {{conversation_date1}}]]
  - [[Date: {{conversation_date2}}]]

---
# Link conversations here automatically
```

**Project Note Template:**
```yaml
---
title: "{{project}}"
status: "{{status}}" # Active, On Hold, Completed, Archived
created: "{{timestamp}}"
type: "project"
priority: "{{priority}}" # Low, Medium, High, Critical
importance: "{{importance}}"
tags: [project, {{project_tags}}]
---
# {{project}}

## Description
{{description}}

## Goals
{{goals}}

## Progress
{{progress}}

## Tasks
{{tasks}}

## Resources
{{resources}}

## Related Conversations
{{related_conversations}}

---

# Link conversations here automatically
```

**Daily Note Template:**
```yaml
---
title: "{{date}} - Conversations & Capture"
date: "{{date}}"
created: "{{timestamp}}"
type: "daily"
---
## Conversations Today

### WhatsApp
{{whatsapp_summary}}

### Web Chat
{{web_chat_summary}}

### Other Channels
{{other_channels_summary}}

## Quick Tasks from Today
{{quick_tasks}}

## Thoughts
{{thoughts}}

---

# Link to individual conversation bases here
```

### Phase 3: Workflow

**Capture Flow:**
1. Conversation happens on any channel (WhatsApp, web, etc.)
2. Capture quickly:
   - If mobile (WhatsApp): Use Essential Space quick capture widget
   - If desktop: Use Obsidian quick capture (Ctrl+E or plugin)
3. Export from Essential Space regularly:
   - Export notes as markdown files
   - Move to `50 Bases/conversations/` in Obsidian
   - Link to relevant people/projects

**Review Flow:**
1. Daily (or weekly): Review new conversation notes
2. Add properties: tags, related projects, importance
3. Link to relevant projects, people
4. Create/update project notes based on conversations

**Search Flow:**
1. When needing information: "What did we discuss about dotfiles?"
2. Open Obsidian Bases: Search across all bases
3. Filter by channel, date range, tags, etc.
4. Find conversation note → see linked projects, tasks, resources

---

## Folder Structure

```
50 Bases/
├── conversations/
│   ├── 2026-01-30-Initial Setup.md
│   ├── 2026-01-30-Dotfiles Discussion.md
│   └── ...
├── people/
│   ├── Lil - Wife.md
│   ├── Kids.md
│   └── Colleagues.md
├── projects/
│   ├── 10 Projects - Dotfiles Overhaul - fresh-tofu.md
│   ├── 20 Areas - Health & Mind.md
│   └── ...
└── daily/
    ├── 2026-01-30.md
    └── ...
```

---

## Getting Started with Obsidian Bases

### 1. Install Plugin
1. Open Obsidian on desktop
2. Settings → Community Plugins → Browse
3. Search "obsidian-bases"
4. Click "Install"
5. Enable plugin after installation
6. Create bases: Settings → Obsidian Bases → Create Base
7. Name first base: "All Conversations"
8. Set root folder: `50 Bases/conversations`

### 2. Create First Base Note
```markdown
---
title: "All Conversations - Test"
type: "base"
created: 2026-01-30T19:00
---
# Test base for cross-channel conversation tracking

## Purpose
Track all conversations across WhatsApp, web chat, and future channels in one searchable system.

## Properties
- `title`: Conversation topic
- `date`: When conversation happened
- `channel`: WhatsApp, Web Chat, Discord, Telegram, etc.
- `participants`: Who was involved
- `status`: Active, Completed, Follow-up needed
- `projects`: Related projects
- `tags`: Custom tags
- `importance`: Low, Medium, High
- `summary`: Brief description

## Links
- Link to: [[People]]
- Link to: [[Projects]]

## Notes
This is a test base to ensure Obsidian Bases is working correctly.
```

### 3. Test Basic Workflow
1. Capture a conversation on WhatsApp
2. Export from Essential Space to markdown
3. Move to `50 Bases/conversations/`
4. Link to relevant people/projects
5. Search across base to test

---

## Advanced Features to Explore Later

### 1. Saved Filters
Create common search filters:
- `channel:WhatsApp` - Show only WhatsApp conversations
- `status:Follow-up` - Show conversations needing action
- `projects:dotfiles` - Show dotfiles-related conversations
- `date:last-30-days` - Recent conversations

### 2. Kanban Board
Create project board for ongoing conversations/tasks:
- Columns: Inbox, Active, Waiting, Done
- Link to conversation bases

### 3. Calendar Integration
- Create event notes for scheduled conversations/meetings
- Link to related bases
- Use Obsidian Calendar plugin (if installed)

### 4. Dashboard Note
Create a "Dashboard" daily note with:
- Active conversations
- Today's tasks
- Recent highlights
- Links to important bases

---

## Migration Strategy

### From Current System
1. **Export** current `Tofurky Tasks & Questions.md` content
2. **Extract** unique conversations, tasks, decisions
3. **Import** into Bases with appropriate templates
4. **Verify** everything is searchable

### Going Forward
1. **Immediate capture** - Use Obsidian Bases for all new conversations
2. **Essential Space integration** - Keep it for mobile capture, export to Bases regularly
3. **Cross-channel consistency** - All channels use same property structure
4. **Regular reviews** - Daily/weekly reviews to link conversations to projects

---

## Notes for Me (Andrew)

### Why This Matters
Your brain creates overwhelming mental space. You said:
- "I want to create stable, fun, easily deployed system that handles complexity my AuDHD brain can't quite handle called life"
- "I want to externalize what I am holding on to and make it accessible quickly"
- "I want to help me digest all this information and come up with an easy, accessible and fun way to carry out these plans"

**Obsidian Bases directly addresses this:**
- ✅ **Externalize memory** - Conversations, tasks, projects in searchable system
- ✅ **Accessible quickly** - Global search across all bases
- ✅ **Easy to use** - Properties, templates, links
- ✅ **Fun/accessible** - Make it visual, use your creativity
- ✅ **Structured but flexible** - Properties add structure, Markdown lets you be free
- ✅ **Cross-channel** - Track all conversations in one place

### Your Role
- Try using Bases for the next few conversations
- Give feedback on what works/doesn't work
- Let me know if you want templates adjusted
- I'll help you refine the system over time

---

## Next Steps

### For Me
1. [ ] Install Obsidian Bases plugin
2. [ ] Create folder structure in `50 Bases/`
3. [ ] Create first base note
4. [ ] Test basic capture → export → link workflow
5. [ ] Give feedback on system

### For Tofurky
1. [x] Created project note with full setup guide
2. [ ] Created folder structure
3. [ ] Defined templates
4. [ ] Documented migration strategy
5. [ ] Ready to help with implementation and refinement

---

*Last updated: 2026-01-30 19:35*

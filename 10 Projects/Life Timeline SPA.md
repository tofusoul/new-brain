---
Type: Project
started: true
start_date: 2026-02-01
status: active
---

# Life Timeline SPA

## Overview
An interactive Single Page Application (SPA) that lives in your vault, displaying a visual timeline of all your daily note entries with the ability to add new entries directly.

## Features

### ✅ What It Does
- **Visual Timeline**: Display all your journal entries, notes, and tasks in chronological order
- **Filter by Date**: Jump to any specific date
- **Filter by Type**: View only journals, notes, or tasks
- **Quick Access**: Click any entry → opens in Obsidian
- **Add New Entries**: Simple form to add journal/note/task → saves to correct daily note
- **Statistics**: See total entries, days tracked, tasks, journals

### 📊 Statistics Tracked
- Total entries (days with content)
- Days tracked
- Total tasks logged
- Total journal entries

## How to Use

### Step 1: Start Obsidian
- Open Obsidian with your `new_brain` vault
- Make sure **Local REST API** plugin is enabled
- Check port 27123 is available (insecure port is fine for local use)

### Step 2: Open Timeline
- Navigate to `timeline.html` in your vault
- Open in browser (double-click, or right-click → Open in Browser)
- The timeline will load and display your entries

### Step 3: Navigate
- Scroll through timeline (newest first)
- Use date filter: `2026-02-01` → shows only that day
- Use type filter: `Journals` → shows only journal entries

### Step 4: Add New Entry
1. Click `+ Add Entry` button
2. Choose date, type (Journal/Note/Task)
3. Write content
4. Click `Save Entry`
5. Entry is added to the correct daily note file
6. Timeline refreshes automatically

### Step 5: Open in Obsidian
- Click any timeline entry
- Opens the full note in Obsidian
- Edit anything you need

## Technical Details

### How It Works
- Uses Obsidian's **Local REST API** (port 27123)
- Reads all daily notes from `00 Periodic/Daily/`
- Parses `## 🖋️ Log` section for entries
- Extracts entries tagged with `#journal`, `#note`, or `[ ]` for tasks
- Renders interactive HTML timeline

### Configuration (in timeline.html)
```javascript
const API_URL = 'http://localhost:27123';
const API_KEY = '9bb48ab76b7b9145cb813dca8b11118faedb488e2b9ff1c0c5de4da4dbe26238';
const VAULT_PATH = '/home/tofu/new_brain';
```

### Security Note
- API key is stored in the HTML file
- Only works locally (localhost:27123)
- Not exposed to the internet
- Your vault stays private

## Future Enhancements

### Potential Improvements
- [ ] #task Search functionality: Find entries by keyword
- [ ] #task Weekly/Monthly view toggle
- [ ] #task Export timeline as PDF or image
- [ ] #task Entry editing: Edit entries directly from timeline
- [ ] #task Dark/Light theme toggle
- [ ] #task Mobile optimization: Better phone layout
- [ ] #task Tag filtering by custom tags
- [ ] #task Mood tracking: Extract mood patterns from journals

## Related Notes
- [[00 Periodic/Daily]] — Source of timeline data
- [[ADHD Management Strategies]] — Consistency in tracking
- [[20 Areas/Productivity]] — Time management systems

## File Location
`/home/tofu/new_brain/timeline.html`

---
**Created**: 2026-02-01
**Status**: Working and ready to use

# Obsidian Linking Strategy - Minimal Context

**Purpose:** Reference specific parts of Obsidian notes without overwhelming the conversation
**Status:** 🔄 Created for review at 10pm tonight

---

## Problem

You need to quickly point to a specific part of Obsidian (a section, a task, a decision) without bringing the whole file into context.

**Current Approach:**
- Single note with multiple sections (Tasks, Questions, etc.)
- Search brings entire note - too much scrolling
- Overwhelms conversation with irrelevant information

---

## Solution: Block-Based Linking

### Strategy 1: Block Links [[Note Name]]
**What it does:** Links to an entire note, shows only that note in a popup/pane
**When to use:**
- You want to see the whole file (complete context)
- The note is small or concise
**Example:** `[[Tofurky Tasks & Questions]]`
**Result:** Opens the entire note in new pane/popup

### Strategy 2: Section Links [[^Heading]]
**What it does:** Links to a specific heading within a note, jumps directly there
**When to use:**
- You want to see one section (Tasks, Questions, etc.)
- You don't need the rest of the note
**Example:** `[[^Tasks to Do]]`, `[[^Questions to Ask]]`
**Result:** Jumps directly to that heading, only shows content from there

### Strategy 3: Block Aliases [|Displayed Name|note-name]]
**What it does:** Links to same note but shows a different name
**When to use:**
- You want to give a section a different name (more descriptive)
- Multiple names for different contexts
**Example:** `[|Health & Mind Dashboard|Tofurky Tasks & Questions]]`
**Result:** Shows same content with different label (useful for cross-linking)

### Strategy 4: Transcluded Blocks ![[Note Name]] ![[#Heading]]
**What it does:** Embeds content from another note directly into current note
**When to use:**
- You want to see content from another note inside current context
- You want same content displayed in multiple places
**Example:** `![[Tofurky Tasks & Questions]] ![[^Pending Questions]]`
**Result:** Shows actual content from other note, not a link

---

## Recommended Workflow

### For Chat Reference (Quick Pointers)
Use **Section Links** (Strategy 2) for questions:

**In conversation:**
"Check the Tasks section" → `[[^Tasks to Do]]`
"Look at Question 1" → `[[^Health & Mind]]`
"What's the Essential Space status?" → `[[^Current Question]]`

**Result:**
- I jump to that heading
- You see only relevant section
- Quick scan without whole note scrolling
- Can return to conversation easily

### For Long-Term Reference (Complete Notes)
Use **Block Links** (Strategy 1) for major topics:

**In conversation:**
"The full dotfiles project note" → `[[10 Projects/Dotfiles Overhaul - fresh-tofu]]`
"Obsidian Bases documentation" → `[[10 Projects/Obsidian Bases - Cross-Channel Memory System]]`

**Result:**
- Full note opens in new pane
- You can search within it
- Close when done
- Doesn't poll conversation context

### For Reorganizing (Same Content, Different Names)
Use **Block Aliases** (Strategy 3):

```
[|Active Tasks|Tofurky Tasks & Questions]]
[|Prioritized Items|Tofurky Tasks & Questions]]
[|Reference Only|Tofurky Tasks & Questions]]
```

**When to use:**
- Keep one master note (Tasks & Questions)
- Use block aliases to show different "views" of same content
- Each alias opens same note but feels/separates contextually
- Good for "Today's focus" vs "Backlog" vs "Archive" concepts

**Result:**
- Same content organized by mental state
- Easy to switch views
- Reduces cognitive load

---

## How These Link in Obsidian

### Block Link [[Note Name]]
```
Syntax: [[Note Name]]
Appearance: #link-color: blue (customizable)
```
- Shows note name
- Opens in active pane
- Hover preview (desktop)

### Section Link [[^Heading]]
```
Syntax: [[^Heading Name]]
Appearance: #link-color: green (customizable)
```
- Shows heading name with `^` prefix
- Scrolls to heading
- Shows content from there down

### Block Alias [|Name|note-name]
```
Syntax: [|Displayed Name|note-name]
Appearance: #link-color: orange (customizable)
```
- Shows "Displayed Name"
- Links to "note-name"
- Same content, different label
- Useful for same content, different contexts

### Transcluded Block ![[Note Name]] ![[#Heading]]
```
Syntax: ![[Note Name]] ![[#Heading]]
Appearance: No special color (shown as content)
```
- Shows actual content from Note/Heading
- Embedded in current note
- Can edit independently
- Changes sync back to original
- Good for building "dashboard" notes

---

## Practical Examples

### Example 1: During Conversation

**You ask:** "What should I do with nvim?"

**I respond:**
```
Check the dotfiles decisions section: [[^Dotfiles]]
```

**What happens:**
- I create a section link, not full block link
- When you click, Obsidian jumps to "Dotfiles" heading
- You see only dotfiles decisions
- No scrolling through entire note
- You can jump back or close that pane

### Example 2: Creating Task Reference

**You say:** "Need to add tracking for Essential Space research"

**I respond:**
```
Add to Tasks section: [[^Active Tasks]]
Add new task: Research Essential Space plugin capabilities
```

**What happens:**
- Links directly to Tasks section
- You can add the task and move on
- No need to open separate file

### Example 3: Dashboard Note

**Create a daily note with transclusions:**
```markdown
---
title: 2026-01-30 - Dashboard

# Active Conversations
![[Tofurky Tasks & Questions]] ![[^Current Question]]

# Today's Tasks
![[Tofurky Tasks & Questions]] ![[^Active Tasks]]

# Quick Actions
- [[00 Periodic/Tofurky Tasks & Questions]] - Add thought
- [[00 Periodic/50 Bases/conversations/]] - Review today

# Reference Material
- [[10 Projects/Dotfiles Overhaul - fresh-tofu]] - Check decisions
- [[10 Projects/Obsidian Bases - Cross-Channel Memory System]] - Review templates
---
```

**Benefits:**
- Everything in one place
- Only what's relevant today
- Quick access to reference material
- Sections stay synced with sources

---

## When to Use Each Strategy

### Use Block Links [[Note Name]] When:
- ✅ File is short (< 500 words)
- ✅ You want to see everything at once
- ✅ You want to open in new pane for reference

### Use Section Links [[^Heading]] When:
- ✅ File is medium (500-2000 words)
- ✅ You want specific section (Tasks, Questions, etc.)
- ✅ You want to scan quickly
- ✅ You're referring to "the decisions section" repeatedly

### Use Block Aliases [|Name|note-name] When:
- ✅ Same content, different mental states
- ✅ You want to create "Today's focus" view
- ✅ You want to separate backlog from active items
- ✅ You're switching contexts (work vs home)

### Use Transclusions ![[Note]] When:
- ✅ Building dashboard/summary notes
- ✅ You want same content in multiple places
- ✅ Creating template notes

---

## Quick Reference for 10pm Review

### Linking Quick Reference Card
```
Block Link (whole file):    [[Note]]
Section Link (jump to part):    [[^Heading]]
Block Alias (same content):    [|Name|note]
Transclusion (embed content):    ![[Note]] ![[#Heading]]
```

### Decision Framework
```
File small? → Block Link [[Note]]
Need one section? → Section Link [[^Heading]]
Need different context? → Block Alias [|Context Name|note-name]]
Building dashboard? → Transclusion ![[Note]]
```

---

## Notes

### Why This Addresses Your Concern
Your actual need: "reference specific parts of obsidian that I want you to look at and change, without bringing too much context"

**This solution gives:**
- ✅ Precise control (jump to exact part)
- ✅ Minimal context (see only what's relevant)
- ✅ Quick switching (no scrolling)
- ✅ Multiple views of same content (aliases)
- ✅ Dashboarding capability (transclusions)
- ✅ Doesn't require plugins (built-in Obsidian)

**At 10pm tonight:**
We can review these strategies
You can try them out
I can help you restructure notes using these approaches
We can decide on what works best for your brain

---

*Research notes from Obsidian linking discussions*
*Created: 2026-01-30*
*Status: Ready for review*

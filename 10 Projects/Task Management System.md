---
Type: Project
started: true
start_date: 2026-02-01
status: active
---

# Task Management System - Consolidation & Cleanup

## Overview
Consolidate scattered tasks into a unified, searchable, manageable system using Obsidian Tasks plugin.

**Current State**: Tasks everywhere — Projects, Areas, Resources, Daily notes (~586 checkboxes in Projects alone)
**Goal**: Single place to find, edit, and manage ALL tasks with due dates, priorities, statuses

## Tasks Plugin Configuration (Critical First Step)

### Settings to Configure
1. **Global Task Filter**: Set to `#task` or `#todo`
   - Settings → Tasks → Global Task Filter
   - Why: Differentiates actual tasks from other checkboxes (grocery lists, etc.)
   - Impact: Only items with filter appear in queries

2. **Done Date**: Enable automatically
   - Settings → Tasks → General → Add Done Date
   - Why: Track when tasks completed for review and analytics

3. **Recurrence**: Enable
   - Settings → Tasks → General → Recurrence
   - Why: Support routines and habits

4. **Custom Statuses** (Optional but recommended)
   - Settings → Tasks → Custom Statuses
   - Recommended statuses:
     - TODO 📋 (default, not started)
     - IN_PROGRESS ⏳ (working on)
     - DONE ✅ (completed)
     - CANCELLED ❌ (no longer needed)
     - BLOCKED 🚫 (waiting on something)
     - WAITING ⏸ (on hold)

## Task Syntax Reference

### Complete Task with All Metadata
```markdown
- [ ] #task Important meeting 🔺 📅 2026-02-15 ⏳ 2026-02-10 🛫 2026-02-08 #work #urgent
```

### Key Elements
- `#task` — Global filter identifier (your configured filter)
- `🔺` — Highest priority
- `⏫` — High priority
- `🔼` — Medium priority
- `🔽` — Low priority
- `⏬️` — Lowest priority
- `📅` — Due date (deadline)
- `⏳` — Scheduled date (when you plan to work)
- `🛫` — Start date (earliest can start)
- `🔁` — Recurrence (e.g., `🔁 every week`, `🔁 every Monday`)
- `#tag` — Tags for filtering and grouping
- `✅` — Done date (auto-added when completed)

## Query Recipes (Copy-Paste Ready)

### All Incomplete Tasks
```tasks
not done
short mode
explain
hide task count
sort by priority
sort by due
```

### Tasks Due Today or Overdue
```tasks
not done
due before tomorrow
group by priority
short mode
```

### Tasks This Week
```tasks
not done
due this week
group by due
sort by priority
```

### Tasks by Project (in specific file)
```tasks
not done
path includes Projects/ADHD Management
sort by due
group by heading
```

### Tasks for Active Projects (via frontmatter)
```tasks
not done
filter by function task.file.property('status') === 'active'
group by filename
sort by due
```

### High Priority Tasks
```tasks
priority is high or priority is highest
not done
sort by due
```

## Task Consolidation Strategy

### Phase 1: Configuration & Setup (30 min)
- [ ] #task Configure Tasks plugin global filter to `#task`
- [ ] #task Enable Done Date tracking
- [ ] #task Set up custom statuses (TODO, IN_PROGRESS, DONE, BLOCKED)
- [ ] #task Test query: `not done` (should show all tasks)

### Phase 2: Task Discovery (1-2 hours)
- [ ] #task Search vault for all checkbox items using `grep -r "\\- \\[ \\]" /home/tofu/new_brain`
- [ ] #task Review results and identify actual tasks vs checklists
- [ ] #task Document task locations (Projects, Areas, Resources, Daily)

### Phase 3: Standardization (2-3 hours)
- [ ] #task Add `#task` or `#todo` to all identified tasks
- [ ] #task Add missing due dates where appropriate
- [ ] #task Set priorities for important tasks (🔺, ⏫, 🔼)
- [ ] #task Convert task statuses to standard format (TODO, IN_PROGRESS, DONE)

### Phase 4: Centralization (2-3 hours)
- [ ] #task Create "Inbox" note in `00 Periodic/Daily/` for new tasks
- [ ] #task Move scattered tasks from Goals & Todos Mapping to Inbox
- [ ] #task Create project-specific queries in project notes

### Phase 5: Dashboard Setup (1 hour)
- [ ] #task Add "Today" query to daily note template
- [ ] #task Add "Weekly Overview" query to weekly note template
- [ ] #task Add "By Project" view to Projects folder
- [ ] #task Test tasks.html Task Manager view

### Phase 6: Workflow Establishment (Ongoing)
- [ ] #task Decide: Quick add (tasks.html) vs detailed editing (Obsidian modal)
- [ ] #task Establish daily task review routine (morning or evening)
- [ ] #task Weekly review: Clean up completed tasks and reschedule
- [ ] #task Use `🎯 Today` section in daily notes for planning

## Common Task Patterns to Avoid

### Anti-Patterns (What NOT to Do)
- ❌ Don't leave tasks scattered across 50+ files
- ❌ Don't mix tasks with general notes in same section
- ❌ Don't create tasks without due dates or project context
- ❌ Don't use inconsistent priority systems
- ❌ Don't create tasks in `Tasks` queries instead of actual notes
- ❌ Don't use `[ ]` without `#task` global filter (creates clutter)

### Best Practices
- ✅ All tasks use `#task` or `#todo` (consistent with global filter)
- ✅ Each task has: due date OR priority OR both
- ✅ Tasks live in appropriate notes (project notes for project tasks)
- ✅ Weekly tasks in recurring notes (e.g., `Routines.md`)
- ✅ Quick capture: Single place to brain dump, then organize
- ✅ One source of truth: Tasks queries show everything

## Tools & Resources

### Tools Installed
- ✅ **tasks.html** — Interactive task manager SPA
  - View all tasks in one place
  - Filter by status, priority, due date
  - Quick add with natural language support
  - Edit tasks with full metadata modal
  - Group by priority
- ✅ **Obsidian Tasks Plugin** — Query and manage across vault
- ✅ **Obsidian Local REST API** — Read/write tasks programmatically

### Files Created for This Project
- `tasks.html` — Task Manager SPA
- `Task Management System.md` — This plan
- `Task Cleanup.md` — (Existing) Previous attempt at organization

## Success Criteria

Project is complete when:
- [ ] Tasks plugin configured with global filter and custom statuses
- [ ] All scattered tasks identified and standardized with `#task` tag
- [ ] All important tasks have due dates or priorities
- [ ] `tasks.html` shows ALL tasks in vault correctly
- [ ] Daily/Weekly/Monthly queries working and accurate
- [ ] Clear workflow for capture, organize, complete

## Notes
- **Tasks plugin documentation**: https://publish.obsidian.md/tasks/
- **API endpoint**: http://localhost:27123 (insecure port)
- **API key**: Stored in tasks.html (for local access only)
- **Security**: API only works on localhost, never exposed to internet

---
**Started**: 2026-02-01
**Estimated Time**: 4-6 hours for setup, ongoing for refinement
**Next Review**: 2026-02-08 (after 1 week of use)

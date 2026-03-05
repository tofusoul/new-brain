---
Type: Project
started: true
tags: [project, notes, organization, automation, llm]
---

# Sort Notes with CLI LLM Agent

**Status:** Planning Phase
**Goal:** Use CLI LLM agent to streamline notes structure and extract insights from periodic data

## Overview
Automated note organization project leveraging LLM agents to clean up, restructure, and extract value from the vault's 1,600+ notes, particularly the daily logs.

## Current Situation
- Vault strongly resembles PARA methodology already
- Root folder cluttered with misplaced notes
- Hundreds of daily logs (2021-2025) with embedded tasks and insights
- Scattered LLM/agent notes throughout vault

## Three-Phase Plan

### Phase 1: Structural Cleanup & Initial Organization

| Action | Description | Agent Use |
|--------|-------------|-----------|
| Tidy Root Note | Move/delete redundant notes from root | Identify redundant files (Untitled, Test, etc.) |
| Consolidate Tech Notes | Move to `30 Resources/Dev/Linux` or subfolders | Suggest precise categorization |
| Reclassify General Notes | Move to `20 Areas` or `30 Resources` | Content analysis for correct placement |
| Review LLM Notes | Consolidate to dedicated folder | Folder migration of agent/LLM resources |

### Phase 2: Content Enhancement via LLM Agent

| Action | Description | Agent Use |
|--------|-------------|-----------|
| Process Daily Logs | Extract tasks from 2021-2025 daily entries | Batch process `20XX-XX-XX.md` files, extract TODOs |
| Summarize Periodic Notes | Create high-level Month/Year summaries | Generate summaries from daily data |
| Cross-Reference & Link | Improve discoverability across structure | Auto-link entities and concepts |
| Structure Metadata | Review vault implementation plans | Verify scripts against plans |

### Phase 3: Review & Maintenance

| Action | Description | Agent Use |
|--------|-------------|-----------|
| Review Archives | Move finished/abandoned projects to archives | Triage based on date and content markers |
| Standardize Templates | Ensure comprehensive, consistent templates | Quality check based on common patterns |

## Key Tasks

### Phase 1 Tasks
- [ ] #task Tidy root folder and index
- [ ] #task Move Hyprland, Qutebrowser, uv notes to Dev/Resources
- [ ] #task Categorize misplaced notes (Prune Plum Tree → Garden, etc.)
- [ ] #task Consolidate AGENTS, CLAUDE, QWEN, Qwen Code notes

### Phase 2 Tasks
- [ ] #task Set up CLI LLM agent integration
- [ ] #task Batch process all daily logs for task extraction
- [ ] #task Create/aggregate `Open Tasks in Dailies.md`
- [ ] #task Generate Month/Year summaries from daily data
- [ ] #task Auto-link related notes across structure

### Phase 3 Tasks
- [ ] #task Review `10 Projects` for finished/abandoned items
- [ ] #task Review templates for completeness
- [ ] #task Document maintenance procedures

## Resources & Scripts
- `organize_vault.py` - Existing organization script
- `Final Vault Structure Plan` - Structural requirements
- `Improving Vault With AI` - AI-assisted restructuring plan
- `PARA_Migration_Plan` - Migration methodology

## Expected Outcomes
- Clean, organized PARA structure
- All tasks extracted and organized from daily logs
- Automated cross-linking between related notes
- Clear archival of finished projects
- Standardized templates for future notes

## Related Notes
- [[Final Vault Structure Plan]] - Detailed structure requirements
- [[Improving Vault With AI]] - AI restructuring methodology
- [[PARA_Migration_Plan]] - Migration approach
- [[Note System]] - General note system management

---
*Last updated: 2025-02-01*

# AGENTS.md - Agent Guidelines for Tidied Notes Vault

## Core Principles
1. **Always check existing projects first** - Before starting any task, review the `10 Projects/` folder to identify relevant context
2. **Create project plans** - For any multi-step task, create a project plan note in `10 Projects/` 
3. **Track progress with Tasks plugin** - Use `- [ ] Task` format and `- [x] Completed task ✅ YYYY-MM-DD HH:mm` for completed items
4. **Reference the plan continuously** - Always refer back to the project plan note when working on the project

## Agent Workflow

### Step 1: Context Discovery
When user requests a task:
1. **Check existing projects** - Scan `10 Projects/` folder for relevant projects if it exists
2. **Look for active projects** - Check if any ongoing projects relate to the request
3. **Review project plans** - If the request is part of a project,. Read existing project plans to understand current status

### Step 2: Project Planning
If new project needed:
1. **Create project plan note** in `10 Projects/` with format:
   ```
   # Project Name - Plan & Progress
   
   ## Overview
   **Goal**: [clear objective]
   **Date**: [current date]
   **Status**: [planning/active/completed]
   
   ## Tasks
   ### Phase 1: [Phase Name]
   - [ ] Task 1
   - [ ] Task 2
   
   ## Decisions Made
   - [x] Decision 1 ✅ timestamp
   
   ## Changes to Plan
   *(Document changes here)*
   
   ---
   *Last updated: timestamp*
   ```

### Step 3: Execution & Updates
1. **Update project plan** after each completed task
2. **Use Tasks plugin format** with timestamps
3. **Document decisions** and changes to plan
4. **Reference project plan** throughout execution

## Project Discovery Process
1. **List projects**: Check `10 Projects/` folder contents
2. **Read project titles**: Look for relevant keywords
3. **Scan project plans**: Read active project plans for context
4. **Ask user**: If unsure which project relates, ask for clarification

## Example Agent Behavior
**User**: "Help me organize my book notes"
**Agent**:
1. Checks `10 Projects/` folder
2. Finds "Book Organization System" project
3. Reads existing plan
4. Updates plan with new task
5. Executes task while referencing plan

## Key Commands
- Always use `todowrite`/`todoread` for task management
- Always ask one question at a time
- Always check with user before making changes
- Always document progress in project plan
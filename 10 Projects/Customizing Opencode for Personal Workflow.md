---
Type: Project
started: true
start_date: 2025-09-24
status: active
---

# Customizing Opencode for Personal Workflow

## Project Goal
Customize [[opencode]] agents to better handle personal workflow tasks including:
- General computer assistance in ~/ directory
- Configuration file editing with proper safety measures
- Note management using [[PARA]] methodology in [[Obsidian]] vault
- Automated wiki linking and note organization

## Background
- **OS**: [[Omarchy]] (DHH's Arch/Hyprland remix)
- **Dotfile Manager**: [[chezmoi]] v2.65.2
- **Notes**: ~/notes as [[Obsidian]] vault
- **Method**: [[PARA]] organization system

## Tasks

### Phase 1: Core Agent Behavior Setup
- [ ] Configure opencode agents with specified proactivity level
- [ ] Set up concise response style with clear details
- [ ] Implement git-based undo logging for repositories
- [ ] Create backup system for non-git folder changes

### Phase 2: Configuration File Management
- [ ] Set up chezmoi integration workflow
- [ ] Create config backup procedures
- [ ] Implement diff checking between chezmoi and actual configs
- [ ] Establish test → chezmoi add → commit → push workflow

### Phase 3: Obsidian Note Subagent Development
- [ ] Research and configure obsidian-vault MCP server
- [ ] Create note organization subagent with capabilities:
  - [ ] Note creation with YAML frontmatter metadata
  - [ ] PARA categorization automation
  - [ ] Wiki-link generation and existing note scanning
  - [ ] Template building and management
  - [ ] Project and task review functionality
- [ ] Implement sampled review system for auto-generated links

### Phase 4: Integration and Testing
- [ ] Test Obsidian MCP integration
- [ ] Validate config editing workflows
- [ ] Test note organization automation
- [ ] Refine agent behaviors based on usage

### Phase 5: Documentation and Refinement
- [ ] Update ~/AGENTS.md with final workflows
- [ ] Create session tracking templates
- [ ] Document custom agent usage patterns
- [ ] Establish maintenance procedures

## User Preferences (Guiding Principles)

### Agent Behavior
- **Proactivity**: Check plans for major changes, auto-apply minor edits
- **Response Style**: Concise but sufficiently detailed
- **Undo System**: Git for repos, manual undo log for non-git folders
- **Config Safety**: Always backup, use chezmoi workflow, no "safe" configs

### Note Management
- **Structure**: Use existing PARA structure (10 Projects, 20 Areas, 30 Resources, 40 Archives)
- **Automation**: Obsidian-vault MCP preferred, custom subagent for complex tasks
- **Linking**: Auto-link with sampled reviews
- **Metadata**: YAML frontmatter for all created notes

### Configuration Workflow
1. Check chezmoi status and diffs
2. Consult on differences found
3. Edit actual config and test
4. If working: chezmoi add → commit → push
5. Maintain backup during process

### Most Frequent Task Types
- Configurations in ~/ directory
- Coming up with shell commands or quick scripts for computer tasks
- Online research to create markdown documents for notes/projects
- Planning and creating custom agents for opencode and other Agentic CLI coding tools

### Regular Config Files
- .zshrc
- neovim config
- Coding agent settings (opencode, claude-code, gemini-cli)
- Hyprland configs
- Walker configs and other custom setup from omarchy

## Next Immediate Actions
- [ ] Set up Obsidian-vault MCP server in opencode config
- [ ] Create note subagent markdown configuration
- [ ] Test MCP integration with existing vault
- [ ] Begin Phase 1 agent behavior configuration

## Related Notes
- [[PARA Methodology]]
- [[Obsidian Setup]]
- [[chezmoi Configuration]]
- [[Omarchy System Info]]

---
*Last updated: 2026-01-31*

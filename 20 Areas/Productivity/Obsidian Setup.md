# Obsidian Setup

**Type**: Area  
**Created**: 2025-09-24  
**Last Updated**: 2025-09-24  

## Overview

~/notes directory is configured as an [[Obsidian]] vault for personal knowledge management using [[PARA]] methodology.

## Current Configuration

### Directory Structure
```
~/notes/
├── Projects/          # Active projects with specific goals
├── Areas/            # Ongoing responsibilities  
├── Resources/         # Topics of interest
└── Archives/         # Inactive items
```

### Integration Points

#### 1. PARA Methodology
- All notes organized using [[PARA]] categories
- Wiki links in format [[keyword]] for internal connections
- Tags: #Projects #Areas #Resources #Archives

#### 2. Opencode Integration
- Agents should automatically create notes in appropriate PARA categories
- Auto-link to existing notes using [[wiki links]]
- Scan for related content before creating new notes

#### 3. Wiki Link Automation
When creating notes, agents should:
1. Identify key concepts/keywords in new note
2. Scan existing notes for matching concepts
3. Add [[wiki links]] to related notes
4. Use tags for categorization

## Automation Requirements

### Note Creation Workflow
1. **Determine PARA category** based on content type
2. **Scan existing notes** for related concepts
3. **Auto-generate wiki links** to relevant notes
4. **Apply appropriate tags** (#Projects #Areas #Resources #Archives)
5. **Create note** in correct directory

### Wiki Linking Rules
- Link to exact note titles when possible
- Use keywords that match existing note titles
- Create bidirectional links where appropriate
- Limit links to most relevant connections (3-7 per note typically)

### File Naming Conventions
- Use descriptive, human-readable names
- Avoid special characters except spaces, hyphens, underscores
- Use `.md` extension for all notes
- Date format: YYYY-MM-DD for dated content

## Features to Implement

### 1. Smart Note Categorization
- Analyze content to determine correct PARA category
- Ask user for clarification if ambiguous
- Learn from user corrections over time

### 2. Context-Aware Linking
- Understand semantic relationships between concepts
- Prioritize links to recently accessed notes
- Weight links by relevance and frequency

### 3. Template System
- Create templates for different PARA categories
- Include standard metadata (created, updated, tags)
- Auto-populate common sections

### 4. Maintenance Tasks
- Identify orphaned notes (no incoming links)
- Suggest note consolidation opportunities
- Archive completed projects automatically

## Current Status

- [x] Basic PARA directory structure created
- [x] Initial project notes created
- [ ] Wiki linking automation implemented
- [ ] Smart categorization system
- [ ] Template system
- [ ] Maintenance automation

## Related Notes

- [[Customizing Opencode for Personal Workflow]] - Main project
- [[PARA Methodology]] - Organization system
- [[wiki-links]] - Linking format reference

---

*Tags: #Obsidian #setup #PARA #automation #notetaking*
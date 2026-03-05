---
Type: Project
started: false
tags: [project, notes, app, productivity, cli]
---

# Sesame Bento - Personal Note System

**Status:** Planning/Development
**Author:** Andrew Shih
**Tagline:** Making small data beautiful

## Overview
An app that manages my headspace. Takes me back to the moment and my life in a pleasant and engaging way.

**Name Meaning:** Sesame means bitty bits, Bento means beautiful compartments to present delectables. The system is like a bento that helps make your bitty bits delectable.

## Project Goals

### Primary Goals
- Have a note system that I'm actually happy with
- Learn:
  - Tree-sitter and parsers for defining languages
  - Creating or specifying an editor
- Expose and showcase skills that are otherwise impossible to demonstrate

### What Bento Needs to Do
- Allow awareness and mindfulness about thinking, commitments, and dreams
- Connect past, present, and future in a delightful way (daily use)
- Make notes come alive so I don't feel bored by weight of thinking
- Help organize thoughts and plans
- Help remember with notes
- Place everything in time and relations with each other
- Through act of meaning-making, help prioritize

## Technology Stack for Prototype

### Core
- **Python** - Primary language
- **Prompt Toolkit** - Interactive CLI interface
- **Typer CLI** - Command structure
- **Rich CLI** - Beautiful terminal output

### Data
- **DuckDB** - Data syncing, processing, and persistence
  - Option to store as parquet files
  - Can store in:
    - Storage bucket
    - Folder (can sync via Dropbox or Syncthing)
- **MotherDuck** - Optional (cloud sync)
- **Polars** - Data manipulation (zero-copy with DuckDB)
- **Ibis** - Database abstraction
- **Pydantic** - Data validation
- **SQLModel** - SQL ORM

### Frontend
- **FastAPI** - Serve data to frontend
- **Streamlit** - Dashboarding

### Notes
- **Neovim + Telekasten** - Handle note editing (for now)
- **Mistune** - Markdown parser to generate AST

## Design & Structure

### Data Format
- Persist as plain text markdown files and parquet files
- Opt-in syncing via MotherDuck

### Grammar & Structure

#### Groups and Subgroups
- Markdown representation: Heading Levels

#### Projects
- Markdown representation: Line with full bold text

#### Tasks
- Markdown representation: Checkbox `- [ ]` or `- [x]`

#### Subtasks
- Indentation after a task line

#### Internal Links
- Markdown representation: `[[ ]]`

#### Content
- Markdown that isn't tasks

#### Tables and Rows
- Markdown representation:
  - Note: Neovim isn't as good as Emacs at tables
- Mark item as member of table with `@`
- Daily/weekly/monthly/quarterly/yearly notes treated differently for tabularizing
- Format provides metadata

### Outliner
- Easiest way to show hierarchical relationships between ideas

### Task Management
**Grouping by:**
- Week
- Date
- Tags
- Location
- Persons
- Status
- Type
- Project

**Features:**
- Linking
- Dependency tracking
- Dates
- Milestones
- Recurring tasks

## Development Phases

### Version 0.1: Works for Me (CLI Only)
**Goal:** Dogfooding full commitment, CLI-only app

**Features:**
- Basic system to deal with ALL of my info
- Tables, Notes, TODOs, Events, Projects, Journals, People
- Make doing what I do in Excel dead simple:
  - Create tables with names
  - Columns on tables have names
  - Strongly typed columns
  - Data checked as you enter it
  - Derived columns calculated
  - Merge data from multiple tables with lookups
  - Filter data
  - Create derived tables
- Sequential TUI interface

### Version 0.0.1: Good Enough for Me Bento
**Goal:** Note system I'm happy to use daily

**Current Status (Using Neovim + Telekasten):**
- [x] Journal - using nvim
- [x] Notes - using nvim
- [x] Task and event list - using nvim
  - [x] Future logs (like bujo)
  - [x] Backlog
  - [x] Events
- [ ] Lists - design and implement
- [ ] Tables - design and implement
- [x] Markdown notes linking everything - using nvim

**Sesame Bento Will Implement:**
- Command system
- Lists
- Tables

**Success Criteria:**
1. Data structures and flows sound enough to migrate all notes
2. UI polished enough to be happy using it daily

### MVP 1: Public
**Key Features:**
- Outliner features (hierarchical relationships)
- Task management:
  - Grouping (week, date, tags, location, persons, status, type, project)
  - Linking
  - Dependency
  - Dates
  - Milestones
  - Recurring tasks

## Rough Data Structure
- Command Log
- Lists
- Tables

## References
- Mistune Markdown Parser: https://mistune.lepture.com/en/latest/guide.html
- Treesitter: Parser generation
- Telekasten: Note-taking plugin for Neovim

## Related Notes
- [[Rethinking Productivity Suites]] - Philosophical foundation
- [[Productivity]] - Productivity systems
- [[Python]] - Programming language
- [[DuckDB]] - Database
- [[Polars]] - Data manipulation
- [[Note System]] - Note-taking concepts

---
*Last updated: 2025-02-01*

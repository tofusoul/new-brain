---
Type: Project
started: false
tags: [project, app, productivity, office-suite, idea]
---

# Sesame Bento - Office Suite Alternative

**Status:** Concept Phase
**Tagline:** Make small data beautiful
**Type:** Productivity/Office Application

## Overview
An office suite built on typed, structured data where everything is an object with defined relationships. A place to jot things down and get them organized naturally.

## The Problem

Current office suites have a fundamental flaw:
- Connection between separate bits of data is an afterthought
- Requires hacky workarounds
- The process of making a document should involve finding where new information fits in organization's "headspace"
- Cutting and pasting loses connections, references, and lineage of ideas

### Specific Issues
- Why can't a paragraph in meeting minutes become a todo item?
- Why can't a bullet list turn into a presentation?
- Why can't you message something from a memo to someone without switching apps?
- All done collaboratively in real time?

**Consequence:** Organizations forget why and how things ended up in policy lists, or why sales teams tell clients specific things. The disconnect causes knowledge loss.

## Core Philosophy

### Everything is an Object
- Objects relate to one another in particular ways
- Objects of similar form are a type
- A function takes an object of one type and returns an object of some type via rules

### Data Types
Everything an office worker does involves only a few types of data:
- Strings (text)
- Integers
- Floating point numbers
- Variables
- References
- Date/time
- Binary data (images, etc.)

**Examples:**
- A word is a type of object made of character strings
- A paragraph is a type of object made of words
- A record is a collection of objects
- A table is a type of collection of records where rows have same field labels
- A number is something you can do "numbery things" with (addition, subtraction)

### The Job of Office Suite
Provide a natural workflow that:
1. Takes information from minds, sensors, and other systems
2. Structures it
3. Presents it in a way that's easy to grok, derive insight, and share

## Features & Architecture

### Data Model
- **Typed structured data** (unlike traditional spreadsheets)
- Everything created is named
- References by name (unlike Excel cell references)
- Define types explicitly
- Each column in tables is typed
- Can require unique values
- Unique value columns can be keys

### Components

#### Cards
- Single atom of information
- Basic building block

#### Docs
- Word processing
- Rich text editing

#### Tables
- Just a table (none of this "sheets" shit)
- Typable, filterable, sortable
- Reference tables like index-match
- Can append slicers, etc.

#### Lists
- Relationship tables
- Organized collections

#### Pics
- Image handling and display

#### Pivot Tables
- Data aggregation
- Cross-tabulation

#### Conditional Formatting
- Visual indicators based on data

### Visual Organization
- Visual means to arrange things
- Drag and drop interface
- Natural flow from mind to data

## Workflow Examples

**Example:** Convert meeting minutes to todos
1. Write paragraph in meeting notes
2. Select paragraph → convert to todo item
3. Reference preserved back to meeting
4. Connection maintained

**Example:** Share memo content
1. See something in memo
2. Send to colleague
3. Recipient sees original reference
4. Conversation and decisions linked to source

## Comparison to Existing Tools

### Traditional Office Suites (Word, Excel, PowerPoint)
- Geared toward creating traditional documents
- Letters, forms, resumes, tables, presentations, proposals
- These are just views of data
- Office suite determines what you can do with it

### Org Mode (Inspiration)
- Has the right ideas about structure
- But needs modern UI and data modeling

## Related Concepts

### Agenda Engine
Automatically creates agenda when passed todos. Productivity suites should be built on database management services, not file systems.

Web-based suites like Google Docs are built on databases but emulate the experience of individuated files on file systems.

### Time Tracker
A pomodoro todo app that tracks estimated time against actual time spent.

## Development Plan

### Technology Stack
- [ ] #task Decide on framework
- [ ] #task Choose database backend
- [ ] #task Plan data model thoroughly

### Prototype
- [ ] #task Build basic card system
- [ ] #task Implement table with typed columns
- [ ] #task Create visual arrangement interface
- [ ] #test Test with real workflows

### Features to Build
- [ ] #task Card creation and editing
- [ ] #task Table creation with typing
- [ ] #task Reference system (by name)
- [ ] #task Simple document editing
- [ ] #task Pivot table functionality
- [ ] #task Conditional formatting

## Related Notes
- [[Productivity]] - Productivity systems
- [[App Development]] - Development resources
- [[Business & Project Ideas]] - Other ideas
- [[Spreadsheets]] - Current tools

## Inspiration
- Excel: Great data manipulation
- Org-mode: Outlining and structure
- Modern databases: Typed, relational data
- Design tools: Visual, intuitive

---
*Last updated: 2025-02-01*

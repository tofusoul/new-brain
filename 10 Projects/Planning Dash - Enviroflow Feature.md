---
Type: Project
started: false
start_date: 2022-10-28
tags: [project, enviroflow, planning, business]
---

# Planning Dash - Enviroflow Feature

**Status:** In Development (Part of Enviroflow App)
**Start Date:** 2022-10-28
**Last Worked:** 2022-11-14

## Overview
Planning dashboard component for Enviroflow App to help manage subcontractors, bookings, and project logistics for the construction business.

## Project Context
Part of the larger [[Enviroflow App]] project. Focuses on planning and coordination functionality.

## Completed Work

### Data Models
- [x] Created Jupyter Notebook to test models and document functionality (2022-10-28)
- [x] Wrote function for instantiating Table class from the store

### Data Wrangling
- [x] Created function to instantiate Table class from store

## Planned Features

### Planning Functionality
- [ ] Job scheduling (start date, status)
- [ ] Subcontractor booking management
- [ ] Job addresses and location tracking
- [ ] Trello card integration
- [ ] Google Drive file links
- [ ] Booking status tracking

### Views by Trade
- [ ] **Pipelining View**
  - Quantity tracking
  - Type classification
  - Status updates
  - Booked dates
- [ ] **Concrete View**
  - Quantity tracking
  - Concrete type selection
  - Concreter assignment
  - Pour date scheduling
  - Bookings list
- [ ] **Asphalt View**
  - Quantity tracking
  - Booking list generation
  - Status updates
- [ ] **Shared Drains**
  - Group shared drain projects
  - Measure quantities together
  - Plan and schedule combined work

### Summary Dashboard
- [ ] Tab that summarizes all data collections
- [ ] Contractor planning view
- [ ] Aggregate booking statistics

### Misc Work Tracking
- [ ] Fencing projects
- [ ] Decking projects
- [ ] Variation notes and tracking

## Technical Implementation

### Data Wrangling Tasks
- [ ] Create function for generating DataFrame that calls save to spreadsheet function
- [ ] Create button that runs all operations to update store from rebuild code

### UI Requirements
- Tabbed interface for different trade views
- Real-time status updates
- Booking calendar view
- Summary statistics

## Related Notes
- [[Enviroflow App]] - Main application project
- [[Enviroflow Data & Sync]] - Data management
- [[Spreadsheets]] - Using spreadsheets for planning
- [[Trello]] - Task management integration

## Time Logged
- 2022-11-14: Data modeling and wrangling work (see [[Journaling/LOGBOOK]])

---
*Last updated: 2025-02-01*

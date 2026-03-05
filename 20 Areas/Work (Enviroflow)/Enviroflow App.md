---
id: Enviroflow App
aliases: []
tags: 
title: Enviroflow App Notes
---
# Enviroflow App

## Next
- [ ] build a datamodel from 
- [ ]  an alternative project data model from 
- [-] #task migrate the cost estimate buildup data from spreadsheet to the database ⏳ 2025-07-11 📅 2025-09-26 ❌ 2025-09-26
<<<<<<< HEAD
- [-] #task Add an interface to the subcontract generator for adding extra lines to the data ⏳ 2025-09-26 ❌ 2026-02-23
>>>>>>> f376115 (Initial commit before sorting notes)
- [x] #task build the projects for analytics table in the ELT page instead of the project peformance page 📅 2025-07-15 ✅ 2025-09-03
- [ ] Build an interface for building and editing cost estimates #this_month
  - [ ] create a database model with [[SQLModel]] and connect it to motherduck -see [tutorial slides](https://slides.com/johanneskoester/remail-duckdb-sqlmodel#/7)
    - [ ] either that or use the data types in duckdb to model the data
  - [ ] create a interface in Streamlit to build and edit the cost estimates
- [ ] create a nice way to build custom subcontracts from rates
- [x] #task refactor the code in [[Enviroflow App]] with the help of Github Copilot. #this_week 📅 2025-07-14 ✅ 2025-09-03
  - rename classes to camel case as per PEP8.
- [ ] Add interface to build custom subcontract for [[Enviroflow App]] #this_week
- [ ] recreate the project performance report in the streamlit app #this_week

### Unsorted Notes Jotted

- [ ] Means to annotate the project data
- [ ] means to remove quotes from calculations.
- [ ] try using [lang chain motherduck](https://python.langchain.com/v0.2/docs/integrations/providers/motherduck/) for retrieval, and use the
- [ ] try installing the librares in enviroflow app as a python package in [hex](https://learn.hex.tech/docs/explore-data/projects/environment-configuration/using-packages#git-packages)

# Notes on Current Directions
>
> *The direction is often changing, keep a few bullet point of where things are heading right here*

- Need to get reports out quick, as such we are using [[Hex Data]]
  - advantages of using Hex include:
    - Data aware LLMs
    - graph of data dependency between functions
    - seamlessly switching between a live view of the data variables in execution, and editing code (instead of having to re-run)
    - No mode switching between writing code and exploring data for insights. you are doing 'Data Development' as coined by FunFunFuction.
    - no friction between delivering an interactive report and building it (can reuse more parts)
  - Downsides:
    - ~~Write backs to mother-duck from hex is impossible at the moment given the use of DuckDB 0.8 in the builtin Jupyter environment~~
      - This is no longer the case, the repo is updated to duckdb 1.0.0 so I can save to motherduck with python
- proceed with building wider data pipeline in Streamlit and simple python, but start delivering dashboards in Hex, and simplify how they work once we have better, more integrated data
- Use Streamlit as a hub for all the relevant resources

# 2 Week Plan

## [[2024-W28]] beginning [[2024-07-08]]

- [x] load project table in [[Hex Data]] [[2024-07-11]]
- [x] repopulate the project table with data from other tables
  - [x] integrate costs

## [[2024-W29]] beginning [[2024-07-15]]

- [ ] Get version 0.1 of the job performance report out
- [ ] fix the budget builder to write to motherduck
  - [ ] Integrate budget
  - [ ] get projects start date into the pipeline from float data
  - [ ] get project end date into the pipeline from invoice data
- [ ] get started on invoiced Job Performance Report

## Unsorted TODOs

- [ ] Tighten up [logging](https://discuss.streamlit.io/t/save-log-into-a-file-using-streamlit-logger/35953) on the streamlit

# TODOs (Categorised)

### Planning

- [x] tidy up this note so that it is a definitive place to mull things over when I am feeling lost and dejected [[2024-07-11]]
  - [x] go through the referenced part with the open jobs

### Security

- [ ] get rid of the `eval()` in parsing the timeline for projects.
  - [ ] save dates in the timeline as strings. untill the project table. #refactor
- [ ] Clean Quote Data Fetching send directly to Motherduck
  - [ ] No more saving in github repo
  - [ ] clean up historical data saved in github repo

### Infrastructural

- [ ] split the xero part of the app into a separate repo (maybe)
  - [ ] make it more automatic.
- [ ] Start fetching and analysing the Actions API on the cards
- [ ] Fresh start the repo when the architecture is finally clear into the [[Enviroflow]] github org
- [ ] rewrite the part of the app that interfaces with xero as a seperate repo
  - [ ] just use flask or that part
- [x] Re-Factor 'trello-class'
  - Start a full re-write of the the app and document every step.
    - **Why:**
      - I can't hand this code to anyone, it's too much of a kludge
      - Need to seperate out the construction method from the model
      - Need the Key parts of the app to be ledgeable
      - need to execution history to be observable
    - [x] get the same queried data as [[Michael Jack]]'s Trello Class
      - [x] build a representation of trello
    - [x] Rewrite the Trello Data Syncing Pipeline
    - [x] setup [[Prefect]] to to create the pipepine and filter architectrue for the data engineering aspect of the work
    - [x] abstract out the Trello Api for easy access
    - use `ibis[duckdb]` to do the analytics
    - [x] seperate out the data processing from the model in the app
    - i.e. addapt the pipe and filter architecture
    - [x] Persist and Query Trello Data
    - [x] Save the Processed data to MotherDuck

### Unstructured Data

- [ ] Use LLMs and embeddings with langchain to make unstructured data like the descriptions useful
  - [ ] use langchain to do [text summary](https://python.langchain.com/v0.2/docs/tutorials/summarization/)

### Documentation

- [ ] Document how the dataflow works
  - [ ] make explicit [[steps in the data pipeline]] [[2024-06-24]]
  - [ ] simplify the design while you are at it.
- [ ] Document the Run time object model once the Object Model is Finalised.  

### Testing

- [ ] Create a test-suite for the Data pipeline

### Data Pipeline

- [ ] Refactor the data pipeline so it's easier to read and understand and simpler if possible.
- [ ] Make the data loading interface more user friendly
- [ ] Integrate all the data into Projects
  - [x] create projet table [[2024-07-11]]
- [ ] Create

### Org Data

- [ ] Crew Data Editor and selective viewer
- [ ] show matrices around people data
  - [ ] overhead
  - [ ] average labour rate calculation
  - [ ] pie chart for composition of company roles
  - [ ] work out appending tables

### Survey Process

- [x] see if the ratio between the reports and survey capacities are in balance  
- [x] weekly report sent to eqc
- [x] report sent to customer and they

### Pricing and Budget

- [ ] Get Labour and Supplier budget into each quote line #Enviroflow-app.
  - [ ]
- [ ] save, edit and load the editable pricing data
  - #journal this was held up by old version of duckdb in the default python environment, it now has it.
  - do this in streamlit instead of hex, it's a bit more flexible, and it's a part of the data editing process
- [ ] Overhead calculator like what is [here](https://docs.google.com/spreadsheets/d/1Df90oWw027kePdTsWQBFIKrDUpnQhpTPtNNa7diNHbE/edit#gid=1144583014)
- [ ] interface for uploading and appending pricing data
  - kind of have it, but currently can only overwrite
  - [ ] write a means to append cost data
- [ ] Interface to edit subcontractor data and rates
- [ ] Means to calculate constants with updated xero and wage reports
  - [ ] calculate wage constants based on data
  - [ ] #need_clarification from [[Ryan Gebbie|Ryan]] minimum concrete rate tracking, from [[2024-02-07]] what he meant

### Project Performance

- [ ] get projects start date into the pipeline from float data
- [ ] Get end date into the pipeline from invoice data
- [ ] pm tasks status report
- [ ] project overhead (overhead per project value)
- [ ] Project Performance Table
  - [ ] Output Table Fields:
    - rename them if you want
    - [ ] Fields Already in Data
      - [ ] Project
      - [ ] Team
      - [ ] Statuses
      - [ ] Booking Date
      - [ ] Project Manager
      - [ ] Staff
      - [ ] Has VO
      - [ ] Quote Value
    - [ ] With Xero Cost Table
      - [ ] Bills
    - [ ] With Labour Table
      - [ ] Actual Hours
      - [ ] Labour Cost
    - [ ] Needs Quote Lookup
      - [ ] Concrete Qty
      - [ ] Drainage Subs Budget
      - [ ] Service Sub Bugdet
    - [ ] Needs Additional Mechanisms  
      - [ ] Notes
      - [ ] Actions Needed
      - [ ] % of Budget Used
      - [ ] Gross Profit
      - [ ] GP Margin %
      - [ ] Estimated Project Overhead
      - [ ] Approx. Net Profit
      - [ ] Approx. Net Margin $
      - [ ] Direct Labour Budget Hours
      - [ ] Estimated_Tidyup_Hours
      - [ ] Direct Labour Budget
      - [ ] TidyUp Budget
      - [ ] Total Labour Budget
      - [ ] Labour Balance
      - [ ] Bills Budget
    - [ ]
    - [ ] Needs Cost Calcs Done
    - [ ] Needs the Above Done First
      - [ ] Service Subs Bills
      - [ ] Concrete Budget
    - [ ] Needs Budget Buildup Integrated Into Quotes
      - [ ] Concretej Bills
      - [ ] Pipelining Budget
      - [ ] Pipelining Bills
      - [ ] Materials Budget
      - [ ] Materials Bills
      - [ ] Bills pct
      - [ ] Labour pct

### Project Planning

- [ ] Auto fetch the information for the projects and build a board like what what's in the PM office
- [ ] Recreating the old planning app I built with nicegui

### Subcontractors

- [ ] Write an editor for the subcontractor rates table
- [ ] Migrate subcontract generator to [[Hex Data]]
  - Do this when you get the project portforlio going for the PMs

### Back Costing

- [ ] Parse the Cost into Projects

### Error Handling / Data Cleaning

- [ ] Data Fixing Dashbaord from the output error tables
- [ ] Fix Suburb Data from addresses

### Process

- [ ] Automated email for anything booked in 3 weeks time, with a reminder that the PMs will reach out soon #confirm_with [[Ryan Gebbie|Ryan]] -- from [[2023-02-09]]

### Financials

- [ ] Means to discover missed invoices #quarterly
- [ ] check whether survey invoice is paid or not (historical)
- [ ] check when if main invoice is paid, whether survey invoice remained unpaid
- [x] Do some preliminary visuals from just the quote data

### Unsorted

#### Tagged with #Enviroflow-app
>
> *Any tasks that is listed with an #Enviroflow-app tag that is upen

``` dataview
TASK FROM ""
WHERE contains(tags, "#Enviroflow-app") and !complete and !checked
GROUP BY file.link
```

#### From Reference
>
> Don't use references to link tasks after this, instead use tags. use references for conceptual links

```dataview
TASK FROM [[]]
WHERE !complete and !checked and file.name != this.file.name
GROUP BY file.name
SORT file.name
```

# Don'ts

- setup a Redis server on the server (not the right project and too much to learn)
- [x] Gradually shift the ELT pipeline [[Hex Data]] #cancel

> [!Note]
> Not great tooling for the sort of editting i have had to do so far to for the ELT pipeline. Pushing intermediary data out to streamlit and mother duck is still the most transparent so far.
> Just need to tidy it up

-

---

# Goals
  
## **Ultimate Goal:**

- Effectively is to create an ERP that models the flow of the work and the relevant entities of the project

## Proximate Goals

- Settle into a more realistic and communicative cadence with the development, delivering chuncks of value as we go.
-

# Historical

## Evaluation of the first Development cycle

- The first stage of the development was a bit crazy. I underestimated the scale of the challenge.

### Major Mistakes were

- Not having a clear, functioning business process to model the software.
- Not having a data model upfront that makes sense. This means a lot of time spent thinking about what data model could work, chopping and changing
- Did not spend up front time design things, went with instincts on how to put things togeter, which means:
  - A lot of ad hoc code and experimentation
  - no set tasks, what I am building keeps changing, even approaches changes
- Not communicating enough about progress and difficulties
- Not properly looking for resources that would help the development
- Not keeping it as simple and minimal as possible
- Underestimating difficulties
- Played around with too many different data practices

## Current Thinking

- Maybe The excel/ data frame idea of having a cascade of tables from source to desired data is probably more suited to the demands of the company (effectively schemaless data that could be adapted to any needs). Could maybe just clean the tables an query the data using [[Polars]] (which I like way more than pandas)
- It may have been a big mistake to create a relational model for all the entities in the company (too complex)

### What worked

- persisting intermediate data in google sheets and csv/parquet for visibility and trouble shooting, as well as exploration
- streamlit to quickly iterate the UI, so last minute ideas and changes could be implimented. (e.g the subcontract generator)
  1. although when the ui gets complex enough, it's pretty hard to organise the code with streamlit. There are mechanism that will be available in the future such as 'fragments' that might make things easier.
  2. If I embrace one way dataflow fully, that might get rid of a lot of the the issues I faced.
  3. Could potentially do this even with the planning app

## What didn't Work

- Lessons
- Plan
  
- Finetune and make explicit a manual process before turning it into a computerized process
  - I.e. what we are doing with the project reports page
  - Don\'t underestimate the complexity of the manual process. E.g the planning board is actually quite complex
  - Make sure we have a proper functioning process before we proceed with automating it. There was a lot of wasted effort building the software because what the process needs to be isn\'t clear, existing process isn\'t functional
  - Features Requested
- [[Old Requirements]] notes
- [[Old Design Brief]]
  


# Merged Content from Project Plan App

- \#[[Enviroflow App]]

- have to use nicegui, streamlit\'s update model is too simplistic

\*

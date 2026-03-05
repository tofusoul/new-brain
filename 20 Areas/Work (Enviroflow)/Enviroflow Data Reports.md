---
id: Enviroflow Data Reports
aliases: []
tags: []
---

> [!tip] Main Task
> This is my main task for [[Enviroflow]] these days. 
> Should keep this particular note more organized and up to date. 

## Plan
- [ ] 1. List out the steps for the manual update
- [ ] 2. Identify the steps that can only be carried out by me currently, simplify them or provide tools for carrying out those stops for other people.
- [ ] 3. Automate the pipeline where possible so it gets closer to a live report
	- [ ] 3.1 Create a means to export the data from the spreadsheet
	- [ ] 3.2 Create an interface to do some of the things needed to carry out the steps

## Process Issues and Improvements
- [ ] [[2025-01-27]] Sales invoices often not coded
	- [x] #this_month create a list of uncoded invoices to show to [[Kerry Spark]] and [[Ryan Gebbie]] ✅ 2025-06-18
		- include issues from the past, to investigate, where invoices are coded to projects that arn't projects, see [this spreadsheet](https://docs.google.com/spreadsheets/d/1-c_VsrnmDK7eOB3pRxjTP0f2v0qFanpFomNuZJktDoU/edit?gid=45459369#gid=45459369)
## Tasks Noted Elsewhere
```dataview
TASK FROM [[]]
WHERE contains(text,this.file.name) and !completed and !checked
GROUP BY file.name
```

## Done 
```dataview
TASK FROM [[]]
WHERE contains(text,this.file.name) and completed and checked
GROUP BY file.name
```

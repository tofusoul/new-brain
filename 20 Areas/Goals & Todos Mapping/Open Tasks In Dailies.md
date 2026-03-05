---
id: Open Tasks In Dailies
aliases: []
tags: []
---

```dataview
Task from "Daily"
where !complete and !checked
group by file.link as Date
sort Date desc
limit 100
```
- [x] ☝Obsidian Look for Open Tasks in Dailies #Obsidian/Dataview/Queries 

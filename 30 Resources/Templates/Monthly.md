---
aliases:
  - "{{date:MMMM}} {{date:YYYY}}"
tags: ["#this_month"]
---

# 📅 {{date:MMMM}} {{date:YYYY}} in [[00 Periodic/Year/{{date:YYYY}}]]

## 🎯 Monthly Goals

- [ ]

- [ ]

## 📝 This Month's Tasks
```tasks
not done
(tags include #this_month)
short mode
```

## 📊 Month Overview

### Weeks in this Month
```dataview
LIST rows.file.link
FROM "00 Periodic/Week"
WHERE contains(rows.file.path, "{{date:YYYY}}-W{{date:ww}}")
```

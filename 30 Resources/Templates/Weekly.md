---
aliases: []
tags: []
days:
  - "[[{{monday:YYYY-MM-DD}}]]"
  - "[[{{tuesday:YYYY-MM-DD}}]]"
  - "[[{{wednesday:YYYY-MM-DD}}]]"
  - "[[{{thursday:YYYY-MM-DD}}]]"
  - "[[{{friday:YYYY-MM-DD}}]]"
week_starts: "{{monday:YYYY-MM-DD}}"
week_ends: "{{sunday:YYYY-MM-DD}}"
week _no: "{{date:ww}}"
---
# Week:{{date:ww}} in Month [[Month/{{date:YYYY}} {{date:MMMM}}]] of
  [[Year/{{date:YYYY}}]]

## What Do I Want To Get Done This Week?

- [ ]

## Monday [[{{monday:YYYY-MM-DD}}]]

- Work Day

## Tuesday [[{{tuesday:YYYY-MM-DD}}]]

- Work Day

## Wednesday [[{{wednesday:YYYY-MM-DD}}]]

- Work Day

## Thursday [[{{thursday:YYYY-MM-DD}}]]


## Friday [[{{friday:YYYY-MM-DD}}]]

## Saturday [[{{saturday:YYYY-MM-DD}}]]

## Sunday [[{{sunday:YYYY-MM-DD}}]]

``` dataview
TASK FROM ""
WHERE contains(tags, "#this_week") and !completed and !checked
GROUP BY file.link
```

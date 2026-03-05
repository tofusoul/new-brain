
# 2025 October

# This Month
``` dataview
TASK FROM ""
WHERE contains(tags, "#this_month") and !completed and !checked
GROUP BY file.link
```
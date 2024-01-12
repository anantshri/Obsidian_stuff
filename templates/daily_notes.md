---
date: {{date}}
---
# 📆  [[{{date-1d:YYYY-MM-DD}}]] <- Today -> [[{{date+1d:YYYY-MM-DD}}]]

## TASKS DUE TODAY
```tasks
not done
due on {{date:YYYY-MM-DD}}
group by priority
group by tags
short mode
```

## Tasks started already
```tasks
not done
has start date
starts before {{date+1d:YYYY-MM-DD}}
group by priority
group by due
short mode
```

## Highest Priority Items Pending

```tasks
not done
priority highest
group by tags
short mode
```

# Notes from Yesterday

![[{{date-1d:YYYY-MM-DD}}#Tomorrow|no-h1 clean]]
# Notes






----
# Tomorrow



# Auto Feed
-----
## Pinboard Bookmarks



--------
## Articles and Other Items Created/Edited today

```dataview
TABLE string(split(string(file.mtime), " - ")[0]) as "Last Modified"
  WHERE !contains(file.path, "{{date:YYYY-MM-DD}}")
  AND !contains(file.path, "Daily Journal")
  AND file.mday = date("{{date:YYYY-MM-DD}}")
SORT file.mtime DESC
```

---
# Pending Tasks

```tasks
not done
due before {{date:YYYY-MM-DD}}
group by priority
group by tags
```

--------
## new tasks


--------
## Done today

```tasks
done on {{date:YYYY-MM-DD}}
```

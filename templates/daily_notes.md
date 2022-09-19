# [[{{date-1d:YYYY-MM-DD}}]] <- Today -> [[{{date+1d:YYYY-MM-DD}}]]

# TASKS DUE TODAY
```tasks
not done
due on {{date:YYYY-MM-DD}}
group by tags
```

# Tasks started already 
```tasks
not done
has start date
starts before {{date+1d:YYYY-MM-DD}}
group by due
```

# Notes











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
## Tasks
### Overdue
```tasks
not done
due before {{date:YYYY-MM-DD}}
group by tags
```


--------
### new tasks


--------
### Tasks by Date
```tasks
not done
group by due
group by tags
```

### Done today
```tasks
done on {{date:YYYY-MM-DD}}
```

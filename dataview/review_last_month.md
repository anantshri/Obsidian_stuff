### Books Read last month
```dataview
List FROM "Readwise/Books"
WHERE file.cday.month = (date(this.file.cday) - dur(1 month)).month
AND file.cday.year = (date(this.file.cday) - dur(1 month)).year
SORT file.path asc
```

### Articles Highlighted Last month

```dataview
List FROM "Readwise/Articles" OR "Hypothesis"
WHERE file.cday.month = (date(this.file.cday) - dur(1 month)).month
AND file.cday.year = (date(this.file.cday) - dur(1 month)).year
SORT file.path asc
```



### Additional Notes Created
```dataview
List WITHOUT ID (link(file.path, file.path)) FROM -"Readwise" AND -"Hypothesis" AND -"Daily Journal"
WHERE file.cday.month = (date(this.file.cday) - dur(1 month)).month
AND file.cday.year = (date(this.file.cday) - dur(1 month)).year
SORT file.path asc
```

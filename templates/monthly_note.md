
---
date: {{date}}
start_date: <% moment(tp.file.title).startOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %> 
end_date: <% moment(tp.file.title).endOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %>
---

### Books Read This month
```dataview
List FROM "Readwise/Books"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```

### Articles Highlighted Last month

```dataview
List FROM "Readwise/Articles" OR "Hypothesis"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```

### Additional Notes Created
```dataview
List WITHOUT ID (link(file.path, file.path)) FROM -"Readwise" AND -"Hypothesis" AND -"Daily Journal"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```
## Tasks complete this month

```tasks
has done date
done after <% moment(tp.file.title).startOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %> 
done before <% moment(tp.file.title).endOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %>
group by done
group by tags
```

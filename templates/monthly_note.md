---
date: {{date}}
start_date: <% moment(tp.file.title).startOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %>
end_date: <% moment(tp.file.title).endOf('month'.format('YYYY-MM-DD')).format("YYYY-MM-DD") %>
---
>[!Monthly Review Process]
>1. Based on weekly reviews, abstract interesting points upwards at monthly level
>2. List out + and - items
>3. List out public activities
>	1. Travel
>	2. Awards / recognitions
>	3. Blogpost
>	4. Talks
>	5. Trainings
>	6. Public Appearances
>4. Interesting people met
>5. Interesting scenario's explored
>6. Top 5 Important tasks done
>7. Negatives
>	1. What got missed
>	2. What could have been better
>	3. Scenarios, situations


# {{ date }} : Monthly Highlights









# Recap

<%*
let start_of_month = moment(tp.file.title,'YYYY-MM').startOf('month').startOf('IsoWeek');
let end_of_month = moment(tp.file.title,'YYYY-MM').endOf('month').startOf('IsoWeek');
let weeks_in_month = end_of_month.diff(start_of_month, 'weeks') + 1;
tR += Array(weeks_in_month).fill(null).map((x, i) => moment(tp.file.title,'YYYY-MM').startOf('month').startOf('IsoWeek').add(i, 'w').format("## [Week ]WW![[[]GGGG-[W]WW[#Review thoughts|no-h1 clean][]]]")).join('\r\n')
%>

# Notes

## Notes This month





## Books Read This month
```dataview
List FROM "900-Resources/Readwise/Books"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```

## Articles Highlighted Last month

```dataview
List FROM "900-Resources/Readwise/Articles" OR "900-Resources/Hypothesis"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```



## Additional Notes Created
```dataview
List WITHOUT ID (link(file.path, file.path)) FROM -"900-Resources/Readwise" AND -"900-Resources/Hypothesis" AND -"900-Resources/Daily Journal" AND -"900-Resources/FleetingNotesApp" AND -"900-Resources/Review-notes"
WHERE file.cday.month = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).month
AND file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```
## Important Tasks complete this month

```tasks
has done date
done after <% moment(tp.file.title).startOf('month'.format('YYYY-MM-DD')).subtract(1,'day').format("YYYY-MM-DD") %>
done before <% moment(tp.file.title).endOf('month'.format('YYYY-MM-DD')).add(1, 'day').format("YYYY-MM-DD") %>
tags regex matches /#money|#health|#relationship|#brand/
group by function task.done.format("YYYY[%%]-MM[%%] MMM [- Week] WW")
short mode
```


## Misc Tasks completed this month

```tasks
has done date
done after <% moment(tp.file.title).startOf('month'.format('YYYY-MM-DD')).subtract(1,'day').format("YYYY-MM-DD") %>
done before <% moment(tp.file.title).endOf('month'.format('YYYY-MM-DD')).add(1, 'day').format("YYYY-MM-DD") %>
tags regex does not match /#money|#health|#relationship|#brand/
group by function task.done.format("YYYY[%%]-MM[%%] MMM [- Week] WW")
short mode
```

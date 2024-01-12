>[!Yearly Review]+
>Note down interesting things from rollups per month
>Additional items to be done
>1. Highlight of the year
>2. Best of the year
>3. Worst of the year
>4. What could have been different
>5. Blessing in Disguises
>6. Any review notes


# Year in review

- 



# Monthly Highlights

<%*
let start_of_year = moment(tp.file.title,'YYYY').startOf('year');
let end_of_year = moment(tp.file.title,'YYYY').endOf('year');
let months_in_year = end_of_year.diff(start_of_year, 'months') + 1;
tR += Array(months_in_year).fill(null).map((x, i) => moment(tp.file.title,'YYYY').startOf('year').add(i, 'M').format("## [Month ]MMMM![[[]YYYY-MM[#Monthly Highlights|no-h1 clean][]]]")).join('\r\n') 
%>



# Stats and References
## Books Read This month
```dataview
List FROM "Readwise/Books"
WHERE file.cday.year = (date(<% moment(tp.file.title).format("YYYY-MM-DD") %>)).year
SORT file.path asc
```

## Tasks Completed this year

```tasks
has done date
done after <% moment(tp.file.title).startOf('year'.format('YYYY-MM-DD')).subtract(1,'day').format("YYYY-MM-DD") %> 
done before <% moment(tp.file.title).endOf('year'.format('YYYY-MM-DD')).add(1,'day').format("YYYY-MM-DD") %> 
group by function task.done.format("YYYY[%%]-MM[%%] MMM")
short mode
```

## New Beginning

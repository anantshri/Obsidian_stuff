<%*
let title = tp.file.title; // expects format "YYYY-WXX"
let dashIndex = title.indexOf("-W");
let yearStr = title.substring(0, dashIndex);
let weekStr = title.substring(dashIndex + 2);
let year = parseInt(yearStr);
let week = parseInt(weekStr);

// Calculate week boundaries
let startOfWeek = moment().isoWeekYear(year).isoWeek(week).startOf('isoWeek');
let endOfWeek = moment(startOfWeek).endOf('isoWeek');
let startStr = startOfWeek.format("YYYY-MM-DD");
let endStr = endOfWeek.format("YYYY-MM-DD");

// Day-wise references
let days = [];
for (var i = 0; i < 7; i++) {
  days.push(moment(startOfWeek).add(i, 'days').format("YYYY-MM-DD"));
}
%>

# Review thoughts

>[!Highlight of the week]
>

# Weekly Cleanup
- [ ] cleanup personal email
- [ ] cleanup company email
- [ ] desktop cleanup
- [ ] downloads cleanup
- [ ] update CRM data

# Week's Impact

How did this week impact me on these areas:

## Work
```tasks
has done date
done after <% startStr %>
done before <% endStr %>
tags includes #brand
short mode
```
How does it map to Work

## Finance
```tasks
has done date
done after <% startStr %>
done before <% endStr %>
tags includes #money
short mode
```
How does it map to Finance

## Health
```tasks
has done date
done after <% startStr %>
done before <% endStr %>
tags includes #health
short mode
```
How does it map to Health

## Relationship
```tasks
has done date
done after <% startStr %>
done before <% endStr %>
tags includes #relationship
short mode
```
How does this relate to relationships

# Notes for Reference

[[<% days[0] %>|Monday]] ![[<% days[0] %>#Notes]]  
[[<% days[1] %>|Tuesday]] ![[<% days[1] %>#Notes]]  
[[<% days[2] %>|Wednesday]] ![[<% days[2] %>#Notes]]  
[[<% days[3] %>|Thursday]] ![[<% days[3] %>#Notes]]  
[[<% days[4] %>|Friday]] ![[<% days[4] %>#Notes]]  
[[<% days[5] %>|Saturday]] ![[<% days[5] %>#Notes]]  
[[<% days[6] %>|Sunday]] ![[<% days[6] %>#Notes]]  

## Tasks Done
```tasks
has done date
done after <% startStr %>
done before <% endStr %>
group by done
short mode
```

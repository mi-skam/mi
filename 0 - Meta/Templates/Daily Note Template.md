---
tags:
  - daily
created: <% tp.file.creation_date() %>
---
<< [[4 - Kalender/<% tp.date.now("YYYY", -1) %>/<% tp.date.now("MM-MMMM", -1) %>/<% tp.date.now("YYYY-MM-DD-dddd", -1) %>|gestern]]  | [[4 - Kalender/<% tp.date.now("YYYY", 1) %>/<% tp.date.now("MM-MMMM", 1) %>/<% tp.date.now("YYYY-MM-DD-dddd", 1) %>|morgen]] >>

# 📋 Tasks
- [ ] 

# 📝 Notes

---
### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<%tp.date.now("YYYY-MM-DD")%>") SORT file.mtime asc
```
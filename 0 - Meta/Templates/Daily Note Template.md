---
created: <% tp.file.creation_date() %>
---

<< [[4 - Kalender/Dailies/<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>|gestern]]  | [[4 - Kalender/Dailies/<%tp.date.now("YYYY-MM-DD",1,tp.file.title,"YYYY-MM-DD")%>|morgen]] >>

---
# 📝 Notes

---
### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<%tp.date.now("YYYY-MM-DD")%>") SORT file.mtime asc
```
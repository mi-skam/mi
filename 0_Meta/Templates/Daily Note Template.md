---
tags:
  - daily
created: <% tp.file.creation_date() %>
modified: 2024-11-12T12:09:28+01:00
---
<< [[<% moment(tp.file.title, "YYYY-MM-DD-dddd").add(-1, 'd').format("[4_Kalender/]YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|gestern]] | [[<% moment(tp.file.title, "YYYY-MM-DD-dddd").add(1, 'd').format("[4_Kalender/]YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|morgen]] >>

## 📝 Notes

## ⏰ Time Blocking


---

**Notes created today**
```dataview
List FROM "" 
WHERE file.cday = date("<%tp.date.now("YYYY-MM-DD")%>") AND file.name != this.file.name
SORT file.mtime asc
```

 **Notes last touched today**
 
```dataview
List FROM "" 
WHERE file.mday = date("<%tp.date.now("YYYY-MM-DD")%>") AND file.name != this.file.name
SORT file.mtime asc
```
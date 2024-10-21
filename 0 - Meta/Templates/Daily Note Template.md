---
tags:
  - daily
created: <% tp.file.creation_date() %>
modified: 2024-09-25T00:05:19+02:00
---
<< [[<% moment(tp.file.title, "YYYY-MM-DD-dddd").add(-1, 'd').format("[4 - Kalender/]YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|gestern]] | [[<% moment(tp.file.title, "YYYY-MM-DD-dddd").add(1, 'd').format("[4 - Kalender/]YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|morgen]] >>

## 📝 Notes

## ⏰ Time Blocking

## ✅ Tasks
- [ ] Timetrack ⏳ <% moment(tp.file.title, "YYYY-MM-DD-dddd").format("YYYY-MM-DD")%>

_[Google Tasks](https://calendar.google.com/calendar/u/0/r/tasks)_
```tasks
not done
filename does not include {{query.file.filename}}
group by scheduled
path does not include Template
```

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
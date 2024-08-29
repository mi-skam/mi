---
tags:
  - people
---
<% tp.file.title %>
## Meetings
```dataview
TABLE summary as "Summary" from [[<% tp.file.title %>]]
WHERE contains(tags, "meeting")
SORT date desc
```

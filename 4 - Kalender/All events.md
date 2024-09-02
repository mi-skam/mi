---
created: 2024-09-02 10:50
modified: 2024-09-02 11:01
cssclasses:
  - wide-page
---
## Dailies and Meetings

```dataview
table one-liner as Summary, attendees as Attendees from "4 - Kalender"
where contains(tags, "meeting") or contains(tags, "daily")
sort file.day desc
```

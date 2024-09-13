---
created: 2024-09-02 10:50
modified: 2024-09-11T14:17:24+02:00
cssclasses:
  - wide-page
---

> [!Info]- Dailies und Meetings
> ```dataview
> table one-liner as Summary, attendees as Attendees from "4 - Kalender"
> where contains(tags, "meeting") or contains(tags, "daily")
> sort file.day desc
> ```

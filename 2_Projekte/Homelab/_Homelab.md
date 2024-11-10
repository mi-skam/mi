---
modified: 2024-10-07T13:32:31+02:00
---
## Homelab

```dataview
TABLE description, file.etags as "tags"
FROM "2 - Projekte/Homelab"
WHERE status = "active"
```

## Inactive
```dataview
LIST
FROM "2 - Projekte/Homelab"
WHERE status = "inactive"
```

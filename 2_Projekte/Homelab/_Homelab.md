---
modified: 2024-11-11T17:47:13+01:00
---
## Homelab

```dataview
TABLE description, file.etags as "tags"
FROM "2_Projekte/Homelab"
WHERE status = "active"
```

## Inactive
```dataview
LIST
FROM "2_Projekte/Homelab"
WHERE status = "inactive"
```

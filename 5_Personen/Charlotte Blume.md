---
tags:
  - people
  - charlotte
created: 2024-08-22T14:10:11+02:00
modified: 2024-11-12T12:25:18+01:00
---
> [!DISCUSS] To Discuss with *Charlotte Blume*
>```tasks
> not done
> (tag includes #disc) AND (tag includes #charlotte)
> hide tags
> short mode
> ```

> [!WAITING] Waiting for Charlotte Blume
> ```tasks
> not done
> tag includes #waiting
> description includes [[Charlotte Blume]]
> hide tags
> short mode
> ```

## Meetings
```dataview
TABLE summary as "Summary" from [[Charlotte Blume]]
WHERE contains(tags, "meeting")
SORT date desc
```

```dataview
TASK
FROM [[Charlotte Blume]]
WHERE contains(tags, "waiting")
```

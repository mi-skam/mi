---
tags:
  - people
---
> [!DISCUSS]+ In discussion
>```tasks
> not done
> tag includes #discussion
> description includes <% tp.file.title %>
> hide tags
> short mode
> ```

> [!WAITING]+ Waiting for
> ```tasks
> not done
> tag includes #waiting
> description includes <% tp.file.title %>
> hide tags
> short mode
> ```

> [!MEETING]+ Common mettings
> ```dataview
> TABLE summary as "Summary" from [[<% tp.file.title %>]]
> WHERE contains(tags, "meeting")
> SORT date desc
> ```
---
<% tp.file.cursor() %>
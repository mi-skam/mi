---
modified: 2024-09-24T13:24:40+02:00
---

> [!ERROR]  Issue
> You have a lot of reminders in Thunderbird calendar, where you click on the dismiss button, to pass event notifications and nothing happens.

> [!success]  Solution
> 
> 
> Prerequisite:
> 
> - Install "DB Browser for SQLite".
>     
> - Exit Thunderbird app (closing or minimizing will not help).
>     
> 
> Steps to fix.
> 
>1. Open the file _"~/.thunderbird/<your-profile-folder>/calendar-data/cache.sqlite"_ in "DB Browser for SQLite". (file path will vary depending on your OS)
>2. Go to **Browse Data** tab. In the **Table** drop down list, select _"cal_events"_.
>3. Use filter to search for the calendar event that is causing trouble.
>4. Copy the data from column _"event_start"_ of your event and paste it in the column _"alarm_last_ack"_ of your event.

What we are doing here is we are telling Thunderbird, that we acknowledged/dismissed the event reminder right when the event was about to start.

---
modified: 2024-09-03T18:18:37+02:00
---

As pastebin.com closed their public api, I was looking for alternatives.

[Sprunge](http://github.com/rupa/sprunge) is great. Usage:

```bash
<command> | curl -F 'sprunge=<-' http://sprunge.us
```

or, as I use it:

```bash
alias paste="curl -F 'sprunge=<-' http://sprunge.us"
<command> | paste
```

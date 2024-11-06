---
modified: 2024-11-06T11:14:08+01:00
tags:
  - pme
---
*All projects*
```shell
docker container ls --filter label=com.docker.compose.project --format "table {{.ID}}\t{{.Label \"com.docker.compose.project\"}}\t{{.Names}}"
```

*All container by their project name*
```shell
docker container ls -q --filter label=com.docker.compose.project=$project
```
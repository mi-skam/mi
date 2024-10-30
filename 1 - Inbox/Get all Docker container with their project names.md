---
modified: 2024-10-30T18:16:39+01:00
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
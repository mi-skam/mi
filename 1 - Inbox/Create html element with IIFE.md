---
created: 2024-04-09 2024-04-09T14:41:45+02:00
modified: 2024-09-03T18:05:36+02:00
---

```js
const videoEl =
  document.querySelector(`#${videoId}`) ||
  (() => {
    const newVideoEl = document.createElement("video");
    newVideoEl.setAttribute("id", videoId);
    document.body.appendChild(newVideoEl);
    return newVideoEl;
  })();
```

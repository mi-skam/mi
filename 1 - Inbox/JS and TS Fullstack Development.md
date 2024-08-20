---
up: 
related: 
created: 2024-06-10
tags:
  - map
---
> *What is JavaScript?*

`JavaScript`is part of the [C-family](https://en.wikipedia.org/wiki/List_of_C-family_programming_languages) languages, meaning a lot of its syntax is similar to Java, C, C++ and the likes. But it's core features are inspired by Scheme and Self (like have a [[1 - Inbox/Functional Style|function]] as a first class citizen value) and in combination with a prototype-based object orientated language style, it's a different language programming experience.

## Developer Setup

We can go either the [[1 - Inbox/vim]] or [[1 - Inbox/VSCode Type- and Javascript|VSCode]] route. At the moment my web developer setup is mostly based on the latter.  To get a great developer experience #code/js/devxp we need to use a set of runtime, configurations and the right addons/ plugins.

> *Editor*
[[1 - Inbox/Adding Deno support to Zed]]

> *Runtimes*
[[1 - Inbox/NodeJS]]
[[1 - Inbox/Deno]] | [[1 - Inbox/Using 3rd party modules]] | [[1 - Inbox/Deno deps.ts pattern]] | [[1 - Inbox/type checking JavaScript]]

> *Bundler, Templates, Testing ...*
[[1 - Inbox/vite]] | [[1 - Inbox/vitest]] | [[1 - Inbox/create-vite-extra for new  projects]] | [[1 - Inbox/testing JS code]]

> *Backend*
[[1 - Inbox/Webserver für statische Projekte]]
[[1 - Inbox/Node.js minimal example  to serve files in public]]

## The language
`JavaScript`is quite open to the paradigms used to code it. It supports functional, [[1 - Inbox/OOP]], event driven and procedural coding, thus it needs some decisions upfront and discipline to have a coherent style. Much also depends on the frameworks and libraries used or the domain (e.G. game development is rather procedural, whereas backend development quite open). 
```dataview
LIST
FROM #code/js/lang or #code/ts/lang 
SORT file.name ASC
```
## Best practices
```dataview
LIST
FROM #code/js/best-practices
SORT file.name ASC
```
## Typical patterns
```dataview
LIST
FROM #code/js/patterns
SORT file.name ASC
```
## Web programming
```dataview
LIST
FROM #code/web
SORT file.name ASC
```
## Libraries

With [[1 - Inbox/lil-gui]] you can create (debugging) windows, that flow over the application.

## Frameworks

[Phaser3](https://explorer.phaser.io/) is a fast JavaScript Framework that facilitates game development for games running in the browser.

[[1 - Inbox/Wrap objects at the border]] 
[[1 - Inbox/Get game config]]
[[1 - Inbox/Infinite Scrolling List]]
[[1 - Inbox/Put all Assets into a Preload scene]]
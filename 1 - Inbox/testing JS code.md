---
created: 2023-12-26
tags:
  - x/🚧
---

It's rather important to get unit-tests done, for JavaScript [[jest]] is quite popular, but as we already using [[1 - Inbox/vite]] we might use [[1 - Inbox/vitest]] as well, which is supposed to be quite compatible with _jest_ anyway.

I follow the definition of Roy Osherove in "The art of unit testing"[^1] is a piece of code, that calls another piece of code and compares it with expected values.

## expect / match

## handle asynchronous code

## mock functions (apis)

## setup / teardown

    isolate the behaviour even more, by guaranteeing the data is setup or removed as needed for the specific tests.

[^1]: [[osherove_etal20]]

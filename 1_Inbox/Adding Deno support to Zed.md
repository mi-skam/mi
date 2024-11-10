---
created: 2024-05-14 2024-06-05T14:45:46+02:00
modified: 2024-09-03T18:28:47+02:00
---

1. Install Deno as a extension to Zed
2. Throw in a snippet, which disables `typescript-language-server` and `eslint`

`.zed/settings.json`:

```json
// Folder-specific settings
//
// For a full list of overridable settings, and general information on folder-specific settings,
// see the documentation: https://zed.dev/docs/configuring-zed#folder-specific-settings
{
  "languages": {
    "TypeScript": {
      "language_servers": [
        "deno",
        "!typescript-language-server",
        "!eslint",
        "..."
      ]
    },
    "TSX": {
      "language_servers": [
        "deno",
        "!typescript-language-server",
        "!eslint",
        "..."
      ]
    }
  }
}
```
---
modified: 2024-09-24T12:19:53+02:00
---
Du kannst eine Playlist mit yt-dlp runterladen und die Reihenfolge beibehalten, indem du eine Nummer vor den Videotitel setzt. Dafür benutzt du die `-o` (Output-Template) Option. So geht's:

```bash
yt-dlp -o "%(playlist_index)s - %(title)s.%(ext)s" <playlist_url>
```

Kurz erklärt:

- `%(playlist_index)s`: Fügt die Playlist-Nummer vorne an den Dateinamen.
- `%(title)s`: Lässt den Originaltitel vom Video.
- `%(ext)s`: Behält die Dateiendung (wie `.mp4`, `.webm`, etc.).

Mit diesem Befehl hat jedes Video eine Nummer vor dem Titel und die Playlist-Reihenfolge bleibt erhalten.
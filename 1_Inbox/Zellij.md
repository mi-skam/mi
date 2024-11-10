---
modified: 2024-10-01T06:29:51+02:00
aliases:
  - Tmux
---
Zellij ist a terminal multiplexer similar to *Tmux*. It's written in rust and comes with a pretty decent configuration of the box.

> [!WARNING] macOS and modifier
>  Zellij only understands `Ctrl` and `Alt`, where the latter is usually not send on macOS Terminal emulators. You can configure [[Item2]] to do it though
>  ![[Pasted image 20240928212742.png]]

## TMUX like sessions

I want to attach to zellij sessions semi-automatically.  


*config.fish*
```fish
if not set -q ZELLIJ
    if test "$ZELLIJ_AUTO_ATTACH" = "true"
        zellij attach -c default
    else
        zellij attach -b -c default 2>/dev/null # background start
    end
end
```

To ease attaching to the session I created helper functions, which enter a named session with `za <name>` and `zad` to enter the `default` session.

*zellij.fish*
```fish
zellij setup --generate-completion fish | source

function za
  command zellij attach --create "$argv"
end

function zaf
  za default
end
```
---
created: 2024-04-03 2024-04-04T13:43:49+02:00
modified: 2024-09-03T16:46:36+02:00
---

Make tailscale accessible for users and enable the service:

```nix
{ config, pkgs, ... }:

{
  # make the tailscale command usable to users
  environment.systemPackages = [ pkgs.tailscale ];

  # enable the tailscale service
  services.tailscale.enable = true;
}

```

Set-up the device with

```shell
sudo tailscale up
```

---

[[Best-Practices]]

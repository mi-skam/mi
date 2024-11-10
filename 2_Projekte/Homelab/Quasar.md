---
modified: 2024-09-24T11:34:22+02:00
roles:
  - vm
  - dev
description: NixOS vm, running on msi
os: nixos
ip: 
status: active
---
Nixos VM running on [[Mbp]]

It runs in the 10.254.100.0/24 network as other VMs do, too.

At the moment it doesn't work, if mullvad is connected. I found this workaround:

```shell
# enable ip forwarding if needed 
sudo sysctl -w net.inet.ip.forwarding=1
# dump existing rules
sudo pfctl -s nat -a "com.apple.internet-sharing/shared_v4" > pf.conf
# add rule as provided by @nathreed 
echo "nat on utun4 from bridge100:network to any -> utun4" >> pf.conf
# apply complete rule set
sudo pfctl -a com.apple.internet-sharing/shared_v4 -N -f pf.conf
```
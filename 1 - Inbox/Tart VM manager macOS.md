---
modified: 2024-09-27T14:01:20+02:00
---

Installation
```shell
brew install cirruslabs/cli/tart
```

Install a macOS Sonoma machine
```shell
tart clone ghcr.io/cirruslabs/macos-sonoma-base:latest sonoma-base
tart run sonoma-base
```
Install a Ubuntu machine
```shell
tart clone ghcr.io/cirruslabs/ubuntu:latest ubuntu
tart set ubuntu --disk-size 50 # default: 20 
tart run ubuntu
```

## Create a custom linux vm

To install a custom linux distribution, it's enough to create a "bare" linux vm, download the iso and install it manually. Here is an example for nixos[^1].
1. download iso
2. `tart create --linux --disk-size <disk-size-in-gb> nixos`
3. `tart run --rosetta="rosetta" --disk <path-to-iso> nixos`
4. install: https://nixos.org/manual/nixos/stable/index.html#sec-installation-manual
5. set up Rosetta: ``virtualisation.rosetta.enable = true;``
6. Run the vm with `tart run --rosetta="rosetta" nixos`

## Change the subnet range of the internal DHCP (vmnet)


> [!code] Change the default subnet
> 
>```shell
sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.vmnet.plist Shared_Net_Address 10.254.100.1
>```


> [!code] Change the default subnet mask
>
> ```shell
>sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.vmnet.plist Shared_Net_Mask -string 255.255.0.0
>```

## Some fun

Also tart macht wirklich Spaß, meine nixos vm (ohne dhcp) startet in knapp über 2 Sekunden und so kann ich easy eine VM starten wenn ich Sie brauche
`tart run --rosetta="rosetta" --no-graphics nixos &; sleep 2; ssh kudos`

und sie wieder beenden
`ssh kudos -- sudo shutdown -h now


[^1]: https://xyno.space/post/nixos-utm-rosetta
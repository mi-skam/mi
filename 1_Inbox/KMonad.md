---
modified: 2024-09-16T11:57:53+02:00
---
- [Kmonad](https://gist.github.com/amiorin/4c74f63fe599a1dcbd0933628df1aac9) entdeckt. 

## Installation

```shell
stack install --flag kmonad:dext --extra-include-dirs=c_src/mac/Karabiner-DriverKit-VirtualHIDDevice/include/pqrs/karabiner/driverkit:c_src/mac/Karabiner-DriverKit-VirtualHIDDevice/src/Client/vendor/include # installs kmonad to ~/.local/bin

/Applications/.Karabiner-VirtualHIDDevice-Manager.app/Contents/MacOS/Karabiner-VirtualHIDDevice-Manager activate # enables virtual keyboard

sudo visudo -f /private/etc/sudoers.d/kmonad # add a rule to run kmonad without entering a password

# input the line below into the file you are editing.
#  replace <kmonad> with the path to the kmonad binary (output of: which kmonad).
#  replace <user> with your username (output of: whoami). 
#  replace <hash> with the sha256 hash of the kmonad binary (output of: shasum -a 256 $(which kmonad)).
#   this hash must be updated manually after running brew upgrade.

<user> ALL=(root) NOPASSWD: sha256:<hash> <kmonad>

sudo kmonad <kmonand.kbd
```

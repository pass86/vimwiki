# shared libraries uses
```sh
otool -L foo
```

# interprocess status
```sh
ipcs
```

# put displays to sleep
* Control-Shift-Power
* `pmset displaysleepnow`

# view image group
* Command-A -> Space

# core dump
* /cores

# show/hide dock
* Command-Opt-D

# hide front window
* Command-H

# hide other window
* Command-Opt-H

# move file
* Command-Opt-V

# Mission Control
* Control-Up

# move focus to next window
* Command-`

# Toggle Dock
* Command-Opt-D

# Disable Spotlight
```sh
sudo mdutil -a -i off
```

# Show definition of the word
* Command-Control-D

# ISO to USB
```sh
diskutil list
diskutil unmountDisk /dev/disk2
sudo dd if=archlinux-2020.10.01-x86_64.iso of=/dev/rdisk2 bs=4m
sudo pkill -INFO dd # Ctrl + T
diskutil eject /dev/disk2
```

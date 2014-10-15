### linux to usb stick instructions

    diskutil list
    diskutil unmountDisk /dev/diskN
    sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m
    diskutil eject /dev/diskN
    

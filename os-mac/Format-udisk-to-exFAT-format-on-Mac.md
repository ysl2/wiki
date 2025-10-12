# Format udisk to exFAT format on Mac

```bash
# Find the disk identifier. e.g, /dev/disk7
diskutil list
# Format this disk to exfat format and give a name of "MyDisk".
diskutil eraseDisk exfat "MyDisk" /dev/disk7
```

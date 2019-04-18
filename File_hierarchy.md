First, you need to be aware of two facts:

    Android uses more than one file system (think of "multiple drives/partitions" when comparing with your computer
    while sharing a common base, directory structures might differ between manufacturers

So as starting points, I further recommend the file-system tag-wiki and the partition tag-wiki (you might also want to take a look at the most frequented questions using those tags).

In my answer, I will concentrate on the mentioned "common base". However, there still might be deviations made by some manufacturers.
Partitions

As said, Android makes use of multiple partitions. In the file system, they are represented by "directories", which serve as their mount-points:

┌─────────────┬───────────────────────────┐  
| Partition   | Explanation               |  
├─────────────┼───────────────────────────┤  
| /boot       | kernel & Co.              |  
| /cache      | app cache                 |  
| /data       | user data partition¹      |  
| /data/data  | app data¹                 |  
| /dev        | devices²                  |  
| /mnt/asec   | encrypted apps (App2SD)   |  
| /mnt/emmc   | internal sdcard³          |  
| /mnt/sdcard | external sdcard³          |  
| /proc       | process information²      |  
| /recovery   | used in recovery mode     |  
| /system     | system ROM (read-only)    |  
└─────────────┴───────────────────────────┘

¹ Details below
² virtual file systems
³ these might differ. Often, /mnt/sdcard is the internal SD card, while the external SD card is found in /mnt/sdcard/external_sd.

Above list is far from being complete, but should hold the most important partitions.
Directories

Here I again will concentrate on the partitions which are most interesting (or this answer would get far too long and, for most readers, boring.
/data and /data/data

These are in most cases two separate partitions, but there might be cases where this is handled otherwise. One thing they have in common (add /cache here as well): they get wiped on a factory-reset, while the other partitions are usually left untouched by that.

As for the directories contained, I will again concentrate on a selection; most things here you either cannot touch without having your device rooted.

┌────────────────────┬──────────────────────────────────────────────┐  
| Directory          | Explanation                                  |  
├────────────────────┼──────────────────────────────────────────────┤  
| /data/anr          | traces from app crashes (App Not Responding) |  
| /data/app          | .apk files of apps installed by the user     |  
| /data/backup       | Googles Cloud-Backup stuff                   |  
| /data/dalvik-cache | optimized versions of installed apps¹        |  
| /data/data         | app data²                                    |  
| /data/local        | temporary files from e.g. Google Play³       |  
| /data/misc         | system configuration (WiFi, VPN, etc.)       |  
| /data/system       | more system related stuff (certs, battstat)  |  
| /data/tombstones   | more crash stuff ("core dumps")              |  
└────────────────────┴──────────────────────────────────────────────┘

¹ for details on the Dalvik cache, see: dalvik
² each app gets its own data directory assigned here, using the app's package name. There might be a similar directory on your SD card, mostly used by apps with larger amounts of data.
³ usually, files are stored here temporarily to be installed/executed. Google Play e.g. downloads .apk files to this directory, before installing the downloaded app on your device

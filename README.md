# compare_everything
benchmarks, measurements and stats of everything that im curious about

# FILESYSTEMS
i made a great fs comparison among btrfs, ext4, reiserand xfs. tldr: xfs is the winner.

my setup:

i7 11800H | 32gb ddr4 3200mhz | MSI M390 2TB

Gentoo 2.9 linux-5.19.0-pf4 march=native -O3 system-wide (dont ask)

cpu governor is powersave in 90-100% freq, disk governor is noop

i will also test i5 8265U | 20gb ddr4 2400mhz | WD Blue 500gb and i will also test these on hdds not ssds if only i dont forget about this

all partitions were created with default options, i will do ext4 no journal test tomorrow maybe

all of them are exactly 20 000 mb

![Alt text](FS.png?raw=true "Title")

note 1) before copying any files to any partitions i copied them several times in my /home so i make sure they are in ram disk cache and im only measuring writing speed of destination partition and not reading speed of source

note 2) ext4 is afaik the only fs here to use fixed inode size, therefore it sucks at free space. it will always do untill u change % of partition that u wanna use for inode, but then u will get into end of inodes space error

note 3) i was not writing 3 time to ext4, then 3 times to btrfs and so on, no. i was randomly choosing partitions to write to until each has its 3 results. sometimes if results are looking mad i would even do 4th attemt just to see it lays between 2nd and 3rd

note 4) there were no such thing as ssd throttling. temperatures were observed with panel widget and never got over 44C. there were like 20-40 sec break between copying when doing manually and 30 sec break for automated copying

note 5) i was using noop governor. \/o.0\/

note 6) ext4 sucks but afaik its the most reliable one. if ur disk is  physically damaged u have higher chances to restore something if u were using ext4. but i'd just made backups instead

note 7) im planning to redo this bench with a)ram freq decreased b)cpu freq decreased c)lower amount of ram d)hdd 

note 8) results are messy. generally this tells nothing about fss's preformance, but i can conclude then that they all just perform close to each other :)

## Results

1) its clear that the winner is xfs. its better in just every single test. (just slightly better but still)

2) reiser sucks at deleting files

3) ext4 did the worst out of these 4. and thats the system they all recommend 2u. think about it

i personaly use btrfs bcz on gentoo with -O3 u wanna backup every second. if you dont need backups more often then lets say 2 per month, i'd advise u doing them with rsync to  external hdd, and use xfs for /. it will save u some space, time and prolly resources.


# APPLICATIONS

another day i thought my dolphin file manager sucks, i decided to compare it to pcmanfm(-qt). copying 25.3 GiB (27,126,149,909) folder with 104,625 files, 9,719 sub-folders to external hdd via usb took dolphin 4m 15s, pcmanfm did it in 5m 4s. disk was 60% full but i dont think thats the thing, neither is fragmentation. i will test how fast `cp -pr` do the job when i have access to this hard drive next time. testing this on my m2 ssds makes no sense, results are too random. 

upd
| program | time | time |
| --- | --- | --- |
| dolphin | 4m 15s | 7m 1s |
| pcmanfm-qt | 5m 4s | 9m 50s |
| cp-pr | 6m 38s | 5m 19s |

why are u so random :<

# DISTROS

the place for holywars

| distro | ram usageon boot |
| --- | --- |
| gentoo -O3 glibc 2.36 plasma 5.26.3 with semantic desktop w\o telemetry | 620mb |
| garuda latest plasma 5.26.5 w\o zram with killed latte-dock | 1100mb |
| debian 11 plasma 5.20 | 890mb |

will be updated a lot while i search for perfect binary distro xd

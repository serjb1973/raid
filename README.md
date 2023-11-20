## Домашнее задание: Собрать RAID-массив уровня 5.
### Цель:
#### Получить навыки работы с RAID

### Для выполнения работы используются следующие инструменты:
- VirtualBox - среда виртуализации, позволяет создавать и выполнять виртуальные машины;
- Vagrant - ПО для создания и конфигурирования виртуальной среды. В данном случае в качестве среды виртуализации используется VirtualBox;
- Git - система контроля версий

### Аккаунты:
- GitHub - https://github.com/

### Создание образа
```
vagrant up
```

### Проверка
```
[vagrant@centos7 ~]$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
devtmpfs                         908M     0  908M   0% /dev
tmpfs                            919M     0  919M   0% /dev/shm
tmpfs                            919M   17M  903M   2% /run
tmpfs                            919M     0  919M   0% /sys/fs/cgroup
/dev/mapper/centos_centos7-root  125G  1,7G  124G   2% /
/dev/md0p1                       186M  1,6M  171M   1% /mnt/part1
/dev/md0p2                       188M  1,6M  173M   1% /mnt/part2
/dev/md0p3                       190M  1,6M  175M   1% /mnt/part3
/dev/md0p5                       186M  1,6M  171M   1% /mnt/part5
/dev/md0p4                       188M  1,6M  173M   1% /mnt/part4
/dev/sda1                       1014M  131M  884M  13% /boot
tmpfs                            184M     0  184M   0% /run/user/1000
[vagrant@centos7 ~]$ lsblk
NAME                    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0  128G  0 disk  
├─sda1                    8:1    0    1G  0 part  /boot
└─sda2                    8:2    0  127G  0 part  
  ├─centos_centos7-root 253:0    0  125G  0 lvm   /
  └─centos_centos7-swap 253:1    0    2G  0 lvm   [SWAP]
sdb                       8:16   0  250M  0 disk  
└─md0                     9:0    0  992M  0 raid5 
  ├─md0p1               259:0    0  196M  0 md    /mnt/part1
  ├─md0p2               259:1    0  198M  0 md    /mnt/part2
  ├─md0p3               259:2    0  200M  0 md    /mnt/part3
  ├─md0p4               259:3    0  198M  0 md    /mnt/part4
  └─md0p5               259:4    0  196M  0 md    /mnt/part5
sdc                       8:32   0  250M  0 disk  
└─md0                     9:0    0  992M  0 raid5 
  ├─md0p1               259:0    0  196M  0 md    /mnt/part1
  ├─md0p2               259:1    0  198M  0 md    /mnt/part2
  ├─md0p3               259:2    0  200M  0 md    /mnt/part3
  ├─md0p4               259:3    0  198M  0 md    /mnt/part4
  └─md0p5               259:4    0  196M  0 md    /mnt/part5
sdd                       8:48   0  250M  0 disk  
└─md0                     9:0    0  992M  0 raid5 
  ├─md0p1               259:0    0  196M  0 md    /mnt/part1
  ├─md0p2               259:1    0  198M  0 md    /mnt/part2
  ├─md0p3               259:2    0  200M  0 md    /mnt/part3
  ├─md0p4               259:3    0  198M  0 md    /mnt/part4
  └─md0p5               259:4    0  196M  0 md    /mnt/part5
sde                       8:64   0  250M  0 disk  
└─md0                     9:0    0  992M  0 raid5 
  ├─md0p1               259:0    0  196M  0 md    /mnt/part1
  ├─md0p2               259:1    0  198M  0 md    /mnt/part2
  ├─md0p3               259:2    0  200M  0 md    /mnt/part3
  ├─md0p4               259:3    0  198M  0 md    /mnt/part4
  └─md0p5               259:4    0  196M  0 md    /mnt/part5
sdf                       8:80   0  250M  0 disk  
└─md0                     9:0    0  992M  0 raid5 
  ├─md0p1               259:0    0  196M  0 md    /mnt/part1
  ├─md0p2               259:1    0  198M  0 md    /mnt/part2
  ├─md0p3               259:2    0  200M  0 md    /mnt/part3
  ├─md0p4               259:3    0  198M  0 md    /mnt/part4
  └─md0p5               259:4    0  196M  0 md    /mnt/part5
[vagrant@centos7 ~]$
```


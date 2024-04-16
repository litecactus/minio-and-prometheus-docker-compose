# minio and promethus docker compose example for your Homelab

A docker compose to build a MINIO single node, multiple disk server. MINIO will operate with erasure coding with just four disks, but feel free to apply more disks and more servers. I think four servers with eight disks is a great spot. However, in a homelab environment, one server and four disks is more realistic!

Run these commands on your server to setup the file system and label on each disk. Bear in mind your device's may be different so try an ```lsblk``` to get the correct devices.
``` yaml
mkfs.xfs /dev/sda -L DISK1
mkfs.xfs /dev/sdb -L DISK2
mkfs.xfs /dev/sdc -L DISK3
mkfs.xfs /dev/sdd -L DISK4
```

Edit the fstab file with this command.
```
nano /etc/fstab
```

Make sure your fstab file looks like this (with your own devices i.e. /dev/sdc etc).
```
# <file system>  <mount point>  <type>  <options>         <dump>  <pass>
/dev/sda      /mnt/disk1     xfs     defaults,noatime  0       2
/dec/sdb      /mnt/disk2     xfs     defaults,noatime  0       2
/dev/sdc      /mnt/disk3     xfs     defaults,noatime  0       2
/dev/sdd      /mnt/disk4     xfs     defaults,noatime  0       2
```


1. Install docker via docker.com instructions and ```sudo apt install git```
2. ```git clone https://github.com/litecactus/minio-docker.git```
3. Mount disks and add to ```fstab``` as above
4. ```cd minio-docker```
5. ```nano docker-compose.yml``` to edit the domain and ports as desired
6. ```docker compose up -d```
7. Navigate to your URL as specified in the docker-compose.yml file.

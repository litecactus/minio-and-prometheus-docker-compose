# minio docker compose 

A docker compose yaml file to build a MINIO single node multiple disk setup.

``` yaml
$ mkfs.xfs /dev/sda -L DISK1
$ mkfs.xfs /dev/sdb -L DISK2
$ mkfs.xfs /dev/sdc -L DISK3
$ mkfs.xfs /dev/sdd -L DISK4

$ nano /etc/fstab

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
5. ```docker compose up -d```

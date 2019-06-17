# SKCC_DataEng_Final

1. swappiness
 sudo sysctl vm.swappiness=1
vm.swappiness = 1

[ config  변경]

[centos@ip-172-31-3-92 /]$ sudo vi /etc/sysctl.conf
vm.swappiness = 1

![ex_screenshot](./캡처_swapness.png)

2. attributes mount

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1  100G  899M  100G   1% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/0
tmpfs           1.6G     0  1.6G   0% /run/user/1000


![ex_screenshot](./attributes_mount.png)

3. 
fsck -a /dev/nvme0n1p1
fsck from util-linux 2.23.2
/sbin/fsck.xfs: XFS file system.


4. [Disable transparent hugepage support]

$ cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never ([always] 에 대괄호가 있으면 실행 중)

$ sudo tuned-adm profile network-latency
$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]


5.list your network
 ifconfig -a 

![ex_screenshot](./config_5.png)

6. show that ...
 getent hosts

 7. show the nscd service
 [centos@ip-172-31-3-92 home]$ ps -ef | grep nscd
centos   20162 12193  0 05:01 pts/0    00:00:00 grep --color=auto nscd

8. show the ntpd serivce
[centos@ip-172-31-3-92 home]$ ps -ef | grep nptd
centos   20164 12193  0 05:01 pts/0    00:00:00 grep --color=auto nptd


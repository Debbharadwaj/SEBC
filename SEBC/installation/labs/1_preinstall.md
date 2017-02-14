 vim /etc/sysctl.conf
[root@Deb-1 ~]# sysctl -a | grep -i swap
vm.swappiness = 1

Mounts:
[root@Deb-1 ~]#  cat /proc/mounts
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,seclabel,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
devtmpfs /dev devtmpfs rw,seclabel,nosuid,size=14396028k,nr_inodes=3599007,mode=755 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,seclabel,nosuid,nodev 0 0
devpts /dev/pts devpts rw,seclabel,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,seclabel,nosuid,nodev,mode=755 0 0
tmpfs /sys/fs/cgroup tmpfs ro,seclabel,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpuacct,cpu 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/net_cls cgroup rw,nosuid,nodev,noexec,relatime,net_cls 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
configfs /sys/kernel/config configfs rw,relatime 0 0
/dev/sda1 / xfs rw,seclabel,relatime,attr2,inode64,noquota 0 0
selinuxfs /sys/fs/selinux selinuxfs rw,relatime 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=27,pgrp=1,timeout=300,minproto=5,maxproto=5,direct 0 0
mqueue /dev/mqueue mqueue rw,seclabel,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,seclabel,relatime 0 0
/dev/sdb1 /mnt/resource ext4 rw,seclabel,relatime,data=ordered 0 0
tmpfs /run/user/1000 tmpfs rw,seclabel,nosuid,nodev,relatime,size=2881188k,mode=700,uid=1000,gid=1000 0 0
tmpfs /run/user/0 tmpfs rw,seclabel,nosuid,nodev,relatime,size=2881188k,mode=700 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
[root@Deb-1 ~]#

Show space for non-reserve: [root@Deb-1 ~]# df / |grep dev | cut -f 3,6 -d\ | awk '{print ($1*.05)+$2}'

Disable transparent hugepages

[root@Deb-1 ~]# /proc/vmstat/ echo never > /sys/kernel/mm/transparent_hugepage/enabled
[root@Deb-1 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
[root@Deb-1 ~]# cat /sys/kernel/mm/transparent_hugepage/defrag
[always] madvise never
[root@Deb-1 ~]# echo never > /sys/kernel/mm/transparent_hugepage/defrag
[root@Deb-1 ~]# cat /sys/kernel/mm/transparent_hugepage/defrag

List your network interface configuration

[root@Deb-1 ~]# ip link show

List forward and reverse host lookups using getent or nslookup

Show the nscd service is running

service nscd start

Show the ntpd service is running

yum install ntp

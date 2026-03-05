- == SETUP SHARED DRIVE FOR ARMS SYSTEM ==

SETUP NFS SERVER nfs server shares are configured in /etc/export `JOB` OBJECTIVE USE TOOLS <http://how-to.linuxcareer.com/how-to-configure-nfs-on-linux> chkconfig --list \| grep portmap chkconfig --list \| grep rpc chkconfig --list \| grep nfslock chkconfig nfslock on chkconfig portmap on service portmap start service nfs start exportfs -a -v system-config-securitylevel STEPS

configure iptables /etc/sysconfig/iptables

copy the iptables from app-svr-05

follow this example through. need to let the following ports through rpcinfo -p localhost outputs: system-config-securitylevel didn\'t help

configure iptables *etc/sysconfig*

need to let the following ports through rpcinfo -p localhost outputs: open these ports

CONFIGURE IPTABLE iptables --line-numbers -n -L

SET UP CLIENT MOUNTS

mount 10.203.2.12:/export/usage /mnt/usage 10.203.2.12:/export/usage /mnt/usage nfs defaults 0 0

ARMS-DEMO root/r00t\@armsdemo project/project\@armsdemo 10.203.2.46 creat mount dir set mount on fstab

ARMS1 root/armslive project/project! 10.203.2.17 creat mount dir *mnt/armsdbExport* mount 10.203.2.12:/export/usage /tttt copy over test dir set mount on fstab

`GIVE ALL PROJECT USERS THE SAME ID` OBJECTIVE all computers that mount the NFS needs to have the same uid for the user project. changing to the uid of arms-demo because project owns the application arms1 not going to be a part of this.

USE for consistant user access for nfs mounts

TOOLS usermod -u change user info id check id STEPS

LOOK UP THE UID ON EACH SERVER less /etc/passwd \| grep project ARMSDB project502:10::/home/project:/bin/bash ARMS-DEMO project500:502::/home/project:/bin/bash ARMSDB1 project501:10::/home/project:/bin/bash USE UID 500 LIST THE FILES THAT PROJECT USER OWNS ON THESE MACHINES project using find / -user project \| less ARMS-DEMO /tmp/arms.log /tmp/arms.log.1 ARMSDB /var/spool/mail/project /export/usage ARMSDB1 nothing outside of home CHANGE UID OF PROJECT check if the uid is taken less /etc/passwd \| grep 500 ARMSDB1 Change uid here first -- because nothing outsde home ARMSDB

scratch! running as root

SETTING UP SCRIPT.

example in app-svr-05

/export/disk1c/project/a2oAdmin/usagestats/usage

everything other than \~/ needs to be changed

The below scripts need to be deployed at all the arms servers. set up a NFS mounted shared drive on armsDB aftter that.

``` 
#!/bin/sh BASEDIR=dirname $0 echo $BASEDIR
```

fname==uname -n= dname=date +%Y%m%d%H%M%S fls=\$fname.\$dname.txt echo \"\$fls\"

df -k \> \$BASEDIR/\$fls echo \"\$fls\" \>\> \$BASEDIR/index.html

SAMPLE OUTPUT system 1K-blocks Used Available Use% Mounted on /dev/sda2 30470176 5125936 23771480 18% / /dev/sda7 54769276 4073424 47868816 8% /usr /dev/sda5 16253924 776860 14638072 6% /tmp /dev/sda3 20315844 11227384 8039820 59% /var /dev/sda1 194442 24075 160328 14% /boot tmpfs 16307424 0 16307424 0% /dev/shm /dev/sdb1 1728289976 521480156 1119017812 32% /mnt/md100 0

set up cron jobs for this.

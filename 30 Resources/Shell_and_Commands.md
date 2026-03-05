- <https://github.com/gleitz/howdoi>

- ZSH Resources

-   [ZSH intro](http://zsh.sourceforge.net/Intro/intro_toc.html)
-   <http://dotshare.it/>
-   Awesome-shell list is worth going through <https://github.com/alebcay/awesome-shell>

- Commands

- In built in most distros

- Less

-   [Pimp my Less](https://www.topbug.net/blog/2016/09/27/make-gnu-less-more-powerful/)

<https://www.topbug.net/blog/2016/09/27/make-gnu-less-more-powerful/>

- Installed Commands

- bat

a much better cat and less

- fd

find stuff. (better than find) fd hello.hs -X less

- rg

ripgrep

- lt

expose your computer and port to the web

- lt --port 8000

- Commands to try

- Rclone

<https://www.techrepublic.com/article/how-to-sync-from-linux-to-google-drive-with-rclone/>

- fzf

<https://www.youtube.com/watch?v=qgG5Jhi_Els>

- rga

ripgrep all

- ff

find files <https://github.com/vishaltelangre/ff>

- xsv

<https://crates.io/crates/xsv> manipulate csv

- SYSADMIN

- Job Control

  Action              
  ------------------- ----------
  suspend job         Ctrl + z
  Run in background   bg
  Run in foreground   fg

------------------------------------------------------------------------

- Tarballs

​ tar -pczf name.tar.gz directory ​ tar cvf - /path/to/zip \| gzip -c \> name.tar.gz

- Environment

​env VAR=Value \[sets variable for session\] ​ export VAR=Value ​ vim /etc/environment

- Users

sudo adduser *user* ​ sudo userdel *user* ​ sudo vim /etc/passwd ​ sudo passwd *user*

- Group

​ sudo groupadd *group* ​ sudo groupdel *group* ​ sudo useradd -G *group* *user* ​ sudo deluser *user* *group* ​ sudo vim /etc/group

- Permissions

​ 4 = read ​ 2 = write ​ 1 = execute ​ sudo chmod 777 *file* -R ​ sudo chown -R *user* *file* ​ sudo chgrp -R *group* *file*

- FTP

type ftp to enter into console

- Find System information

  Command               arg/      What it does                              Comment
  --------------------- --------- ----------------------------------------- ----------------------------------------
  `top`                           Process manager                           
                        Shift+m   while top is running sorts by mem usage   
  `df`                            list space free on system                 
                        -hT       -hT (human + Type)                        
  `dmesg`                         show system log                           
  `lsblk`                         list block storage devices                
  `fdisk`               -l        list information on drives                
  `uname`               -a        information on the computer               
                        -m        cpu architecture                          
                        -r        kernel version                            
  `lshw`                          list hardware                             
  `lspci`                         List peripherals                          
                        -v        verbose                                   
                        -vv       very verbose                              
                        -tv       shows tree                                No reason to not do this.
  `lsusb`               -tv       lists usb devices                         
  `tree`                          draws the directory tree below cwd        has to be installed manually
  `lsmod`                         shows kernal moduals currently loaded     
  `cat /proc/cpuinfo`             shows the cpu version                     
  `cat /proc/version`             shows the kernal version                  
  `cat /proc/swaps`               shows swap                                other system information stored there.
  `ps`                  -ef       lists process                             
  `uptime`                        shows uptime                              
                                  how do I see local network information?   
  file                            guesses what type of file the files is    
                        -i        more information on the file              
                        -iz       look at files in zips                     
                        -s        block or special char files               
  env                             Shows the variable                        
  help                            show the list of built in commands        
  whereis                         Locate files for acommand                 
  which                           returns pathname of files                 
  alias                           shows list of all aliases                 
  cal                             prints calendar                           
  echo                  \$?       shows the exit code of the last command   
                                                                            

- Core Dumps

-   If there is a core file in your home folder

``` 
gdb -c core
```

to find out what is the source of the coredump

- Apps & Tools

<https://www.freecodecamp.org/news/improve-your-workflow-with-these-awesome-cli-tools-fc3750cbb2bf/> <https://github.com/agarrharr/awesome-cli-apps>

- fselect

Find files with sql like querries <https://github.com/jhspetersson/fselect>

- [ ] install fselect and spend an hour learning it and noting it down 

- Tokei

get project stats <https://github.com/XAMPPRocky/tokei>

- SCRIPTING

- For loops

``` 
for i in * do done
- The if test -f "$i" bit tests if the item is a file.
```

DEBIAN PACKAGES apt-show-versions \> InstalledPkgs dpkg --get-selections

  ----------------------
  grep -v deinstall \>
  ----------------------

\$(hostname)-files ls /var/cache/apt/archives \> AddedPkgs ls /var/cache/apt/archives/partial \> PartialPkgs dpkg-query -W --showformat=\'\$ \$`\n`\' \| sort -n

------------------------------------------------------------------------

------------------------------------------------------------------------

``` 
#!/bin/bash

#------------------------
- DEFINE THE VARIABLES
#------------------------

- a way to get the directoy
base="$( cd "$( dirname "$0" )" && pwd )"
#------------------------
- DEFINING FUNCTIONS
#------------------------

- function to check if a directory exists. If not, create the: directory.
function chkdir {
dir=$1
purpose=$2
if [[ ! -d $dir ]]; then
   mkdir -pv $dir
   echo "Made $dir "$purpose"" >> $logfile.tmp
fi
}


- function to check if a file exists. If not, create the file.
function chkfile {
log=$1
if [[ ! -a $log  ]]; then
   touch $log
   echo "Created $log" >> $logfile.tmp
fi
}

- _FUNCTION TO PULL A FILE_
- check if files are differnt,  if they are, copy local file, backup the previous version
- pull source destination logmain log2
function pull {
   file=$1
   target=$2
   dest=$3/$1
   log2=$4
   echo "Backing up $1"
   - check if back up file at destination exists, if not, create it.
   if [[ ! -a  $dest ]]; then
      cp $target $dest
      echo "$file does not exist, made copy of $target to $dest." >> $logfile.tmp
      echo "Initial backup from $computer, made on $(date)." >> $log2.tmp
   fi
   - compare the files, if different make backup of current copy and copy from computer
   - THE CONDITIONAL BELOW ISN'T REALLY TESTED. SEE IF IT WORKS
   if `diff $target $dest >/dev/null` ; then
      - No changes are made
      echo "No Changes to $file" >> $logfile.tmp
      echo "No Changes to $file from script on run on $computer." >>$log2.tmp
   else
      cp $dest $dest.old
      echo "$file backed up" >> $mainlog.tmp
      echo "$file from $computer backed up" >> $log2.tmp
      cp $target $dest
   fi
}

function pulldir {
   target=$1
   dest=$2
   log=$3
   touch $log.tmp
   if [[ -a $dest/backup.tar.gz ]]; then
     rm $dest/backup.tar.gz
   fi
    if [[ -d $dest ]]; then
      tar -pczf $dest/backup.tar.gz $dest
    fi
   echo "Changes Synced on $(date):" > $log.tmp
   rsync -uvar $target $dest > $log.tmp 2>&1
}
```

- Arch Linux

- make package list

``` example
$ pacman -Qqe > pkglist.txt
```

- Settings

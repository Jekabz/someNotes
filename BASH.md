BASH
====

######find out OS version:

```
cat /proc/version
```

######find out number of threads:

```
nproc
```

######search for file:

```
find / -name <filename>
```

######execute .sh files from current directory:

```
./filename #runs in terminal
```
######see, where program is installed

```
which programmName
```

######bashrc:

```
vim ~/.bashrc
source ~/.bashrc #applies bashrc for current terminal session
```

######runs whatever command:

```
alt+f2
```

```
cd ~/whateverfoldername
```
######newest filename in directory, cast to string:

```
foo=$(ls -t | head -1)
```

######check process existance:

```
eval "$(<process> -s)"
service <process> status
```

######poweroff pc:

```
sudo poweroff
```
######WORKING WITH SERVICES:

```
service <name> status
service <name> start
service <name> stop
service <name> restart
```

######NETWORKING:

```bash
#find out router adress
route -n
```

######SSH_INSTRUCTIONS

```
ssh-keygen -t rsa
ssh-copy-id haze@192.168.2.110
ssh-add
ssh haze@192.168.2.110 -p <port>
ssh haze@<router_ip> -p <port>http://www.textchat.dev/
```

* kill ssh:

```
sudo netstat -tnpa | grep ESTABLISHED.*sshd
pkill -o -u haze sshd
```

######CASSANDRA_INSTRUCTIONS:

* run cassandra:
```
$CASSANDRA_HOME=/home/haze/apache-cassandra-2.2.1/bin
cd $CASSANDRA_HOME
sudo ./bin/cassandra -f
```

* run cqlsh:
```
$CASSANDRA_HOME=/home/haze/apache-cassandra-2.2.1/bin
cd $CASSANDRA_HOME
./cqlsh
```

######HOSTS_FILE

* etc/hosts
* ip_addrese atstarpe hostname

######SCP

* transfers files
* -r option for folders

```
scp [options] /local/path user@adress:/remote/path
```
###### GREP

* Search input fo lines that mach  pattern

###### HERE DOCUMENT

* 

###### #!/bin/bash VS #!/bin/sh

* On Linux and other Unix-like systems you have a choice of multiple shells
* Different shells have tiny little inconsistencies between them
  * Bash has quite a lot of scripting features that are unique only to bash, and not to other shells
  * /bin/sh is an executable representing the system shell.The system shell is kind of the default shell that system scripts should use. In Linux distributions, for a long time this was usually a symbolic link to bash, so much so that it has become somewhat of a convention to always link /bin/sh to bash or a bash-compatible shell. However, in the last couple of years Debian (and Ubuntu) decided to switch the system shell from bash to dash - a similar shell - breaking with a long tradition in Linux (well, GNU) of using bash for /bin/sh.
* /bin/sh on most systems will be a symbolic link and will not invoke sh. In Ubuntu /bin/sh used to link to bash, typical behavior on Linux distributions, but now has changed to linking to another shell called dash. I would use bash, as that is pretty much the standard (or at least most common, from my experience). In fact, problems arise when a bash script will use #!/bin/sh because the script-maker assumes the link is to bash when it doesn't have to be.



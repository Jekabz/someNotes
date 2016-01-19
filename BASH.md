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









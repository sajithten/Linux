# Linux Directories
/root- root directory

/home- home directory for all normal users

/bin- contains all user relatd commands or essential command binaries need to be available in single user mode for all user.

/usr- secondary hierachy for read only user data

/opt- optional application softwara packages

/etc- host specific system wise config files/req by all programmes

/var- contains log files

# To be a root user
sudo -i

# To find a file/program
find / -name ssh

# To add a user
useradd <username>
passwd <passwd>

# To delete a user

userdel <username>

userdel -r <username> will delete with all directory

# To enable password authentication for Ec2
- Edit ssh config file.
vi /etc/ssh/sshd_config

#PermitRootLogin yes need to remove #

PasswordAuthentication no must be changed to yes

then  service sshd restart 

- To login into that user
ssh <username>@<ip address of destination>

# To see a user / details
cat /etc/passwd | grep <username>

# To see a group details
 cat /etc/group | grep <groupname>

 # To add a user to a group
 gpasswd -a <username> <groupname>

  # To remove a user to a group
 gpasswd -d <username> <groupname>

 # To see users in a group

id <groupname>

getent group <groupname>

cat /etc/group | grep <groupname>

# To delete a group

groupdel <groupname>

 # To add a user with pre-defined ID
 useradd <username> -u <ID>
 eg: useradd test -u 2255

# To add text directly to a file
echo "first test" >> test.txt

# To know info about file
getfacl <filename>

# Set file access control list help
setfacl --help

# To change ownership of a file
chown <ownername>:<groupname> file/folder

chown <ownername>:<groupname> file/folder -R (To include all subfolders)

# To move a file from one location to other
mv <source> <destination>
eg: mv /root/test.txt /opt/

# To change file permission
1. Symbolic approach
2. Numeric approach

Read    -r  4

Write   -w  2

Execute -X  1

Means user having full rights user:rwx =7

- For having complete privillege

chmod u+rwx,g+rwx,o+rwx file/folder

- For remove other all

chmod u+rwx,g+rwx,o-rwx file/folder

# To know disk usage
 df -hT

du --help

du -b /home/user

# Install nginx on aws ec2

 amazon-linux-extras install nginx1 -y

service nginx start

# To copy files from one machine to another

1) Generate ssh keys in source machine
ssh-keygen
once generated public key will be in /root/.ssh/id_rsa.pub.

2) copy the public key and in destination server got to

/root/.ssh

vi authorized_keys

paste

3) ssh <destination_server_username>@<destination_server_ip>

===============================================================================
second method

sudo -i

add passwd to user by passwd ubuntu

goto vi /etc/ssh/sshd_config

set passwordauthentication yes

in source machine ssh-copy-id -i <location of public key> <username>@<ipaddress>


# To copy file from remote to destination

scp <filename> root@<ipaddress>:/home/

# To remote sync

rsync -avzhr sourcefolder/ root@<ipaddress>:/tmp/

#To know bit of OS

uname -a

# To set name for server
-----------------------

sudo hostnamectl set-hostname controller-machine

# To know ports using
---------------------
netstat -plunt

## To know the OS type:
```
$ uname -o
```
## To know the CPU archit­ecture:
```
$ uname -m
```

## To check the kernel version:
```
$ uname -r
```

## To get the OS name, release, version:
```
$ cat /etc/o­s-r­elease
```

## To list the system hardware:
```
$ lshw
```

## To get the CPU details:
```
$ lscpu
```

## To check system memory:
```
$ free -h or free -m
```

## To check the virtual memory stats:
```
$ vmstat -S m
```

## Free memory cache, dentries and inode (with root):
```
$ echo 3 > /proc/­sys­/vm­/dr­op_­caches
```

## To print the process specific memory utiliz­ations:
```
$ ps aux --sort­=-%mem
```

## To search packages for instal­lation:
```
$ apt search <pa­ckage name>
e.g.:
$ apt search python­-boto
```

## To installed package:
```
$ sudo apt-get install <pa­ckage name>
```

## To uninstall package:
```
$ sudo apt-get remove <pa­ckage name>
```

## To list the mounted disk drives:
```
$ df -kh
```

## To mount the volume:

(create the directory first to mount volume)
```
$ mkdir -p <di­rectory path e..g /mount­-vo­l>
$ sudo mount <src path> <above created dir path>
```

## To list biggest files from directory (biggest 5):
```
$ sudo du -a /dir/ | sort -n -r | head -n 5
```

##  Find the file (search for a file):
```
$ find <dir path> -name <fi­len­ame> -print
e.g. to find app.log in /var directory
$ find /var -name app.log –print`
```

## Search the text string in a directory and print filename containing that string:
```
$ find /var -type f -print | xargs grep <search test>
```

## File the text string from a given directory:
```
$ grep -rIn <search text> <di­rectory path>
```






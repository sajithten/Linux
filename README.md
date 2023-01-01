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

 # To add a user with pre-defined ID
 useradd <username> -u <ID>
 eg: useradd test -u 2255

# To add text directly to a file
echo "first test" >> test.txt

# To know info about file
getfacl <filename>

# Set file access control list help
setfacl --help



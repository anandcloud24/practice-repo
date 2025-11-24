### general Linux commands

sudo su -   # login as root users
su -
ex: su - ec2-user
~                     # indicates home
/                     # super users root directory
ls                    # list of objects
cd .. one step back
cd ../..              #two steps back
cd ../../..           #three steps back
cd         #chnage directory
touch           #creates a file
mkdir     #creates a directory
vi                    #to add content editor page
cat file              # read a file
cat > file            # content override by >
cat >> file           # content will append by >>
pwd                   # present working directory include path
tree                  # tree gives complete folder structure
whoami                # user details
rm -rf                # to delete files and directories
cp                    # copy the file
ex: cp
mv                                # move the file
ex: mv
mv     # renaming
echo                              # print statement
ex; echo "hi welcome" > file1
grep                             # to apply filter to call specific object
foreground                       # interactive terminal ex; python, java, nodejs.
Background                       # Non-interactive terminal ex; httpd, nginx etc..
yum                              # yum is a package manager for amazon Linux ec2, centos, redhat
apt                              # apt is a package manager for ubuntu.
wget                             # to download from external without package manger involvement
sudo su -  # to switch to root user
su - user  # switch to user
touch      # create a file
mkdir      # create a directory
cd         # change directory
ex: cd test    #move to test directory
cd .       # current directory
cd ..      # one step back
cd ../..   # two steps back
vi        #Editor
:wq!      #save and quit
cat       # read file
cat > file     # override existing content
cat >> file    # append
:set number     # to enable numbers
ls     # list objects
ls -l  # list of objects with permissions
ls -la ## list of objects with permissions including hidden files
cp      #copy the file
mv      #move or rename the file
echo    # print content
ex:
echo hi > file1   #print hi content in file1
wget    # to install packages from external using internet
apt     # package manager for ubuntu
yum     # package manager for (centos, amazon Linux , redhat)
curl -s ifconfig.me   # to get it ip address
curl    # by using we can run some process like insert , test query


================ Process related commands =====================

ps                 # shows current directory inside running process list
ps aux             # give complete list of process are running include cpu, memeory.
pa  -ef            # shows only process list not included memory and cpu.
top                # CPU, memory consumption
top -u user        # user related process CPU and memory
top -p  # irrespective of PID process consumption

==============top=====================
top -p 32121   # to check process ID level cpu and ram
top -u   # to check user level cpu and ram
##### yum ############
yum repolist                 #List enabled repos
yum repolist all         #List all repos
yum repoinfo                 #Show detailed info
ls /etc/yum.repos.d/         #Show repo files
cat /etc/yum.repos.d/*.repo #View repo config
yum info                  #Show which repo a package is from
yum list install                # list of packages that are configured inside yum
yum list installed              # installed packages by using yum

################ YUM ##################

1.#List all installed packages
yum list installed
2.#Search for a package
yum search
Example:
yum search nginx
3.yum list available git # to check git package is there or not if yes then yum install git -y

| Task                            | Command                                      |
| ------------------------------- | -------------------------------------------- |
| List enabled repos              | `yum repolist`                               |
| List all repos                  | `yum repolist all`                           |
| View repo config files          | `cat /etc/yum.repos.d/*.repo`                |
| Find repo for installed package | `yum list installed ` / `rpm -qi ` |
| View repo cache location        | `ls /var/cache/yum/`                         |


############## Users and permission management ########

ls -l     # it shows list of objects with permission
ls -la    # it shows list of objects with including hidden files
ls -ld    # it shows list of directories with permission
chmod # to give permissions
read 4
write 2
execute 1
all permissions ==> r+w+x = 7
chmod 724  > owner level 7, group level 2, other level 4
useradd  #to create user-1
usermod -aG user-1 user-2  #user-2 is adding into user-1 group
cat /etc/passwd   # to check list of users
vi /etc/ssh/sshd_config  # by default password login option has disabled we can enable it for login process
service sshd reload     # to update the changes
#!/bin/bash  ##shebang line
sh test.sh or ./test.sh  #to run shell script
Vi /etc/sudoers   # to grant sudo permissions
Vi /etc/sudoers.d/90-cloud-init-users   #for ec2-user


================== Networking ======================

curl ifconfig.me   # to check server public ip
hostname -I        # to check server private ip
ss -tuln         # to check active ports is used in Linux to display active network sockets, specifically showing the listenin
g ports on your system.
( netstat -tulnp old command )
lsof -i :80  # to check which process is running on specific port (ex: 80)
####
telnet
This command is used to test connectivity to a specific port on a target host.
yum list available | grep telnet
■ Example:

telnet 54.227.188.192 22 we can
Tries to connect to IP 10.0.15.201 on port 22 (SSH).
Connected Port open & service listening
Connection refused Host reachable, but port closed
Connection timed out Network/firewall blocking the connection
telnet   #Using telnet to test specific port

Example- 1: Basic Port Scan

 nmap 54.227.188.192
Scans top 1000 common ports.

Fast and lightweight.

Example -2 nmap -p 22,25,80 54.227.188.192

nmap -Pn -p 22,80 54.227.188.192
PORT   STATE    SERVICE
22/tcp open     ssh
25/tcp filtered smtp
80/tcp open     http
22/tcp open → reachable from network (SSH allowed)

80/tcp open → reachable from network (HTTP allowed)

What it does:

above process tested given ports enabled or not with that Ip

-p- means scan ALL ports from 1 to 65535 (full range).

Very thorough but takes longer.

Why it's used:
To find all open ports, even uncommon or custom ones.

Useful for security auditing, troubleshooting, or penetration testing.


nmap <target-ip> #Scan Common Ports:

ex: Scan All 65535 Ports:
nmap -p- <target-ip>

Exmaple -3 
nmap -Pn -p 1-1024 107.20.48.131



ex: Differences ss -tuln vs nmap

Feature	                ss -tuln	                                              nmap (Network Mapper)
Purpose	     View local listening ports on your machine	         Scan a target system (local or remote) for open ports


Feature	                         ss -tuln	              nmap
Checks locally running services	  ✅	                       ❌
Checks network reachability	  ❌	                       ✅

###nslookup

What is nslookup?
nslookup (Name Server Lookup) is a command-line tool used to query DNS (Domain Name System) to get domain name or IP address mapping.

ex: nslookup google.com
Linux commands


########### Linux Storage AWS EBS, EFS ##############

✅ 1. Fully Managed & Scalable
No capacity planning needed — it automatically grows and shrinks as you add or delete files.

Supports petabyte-scale storage.

✅ 2. Shared Access
Multiple EC2 instances (even in different Availability Zones) can simultaneously access the same file system.

Perfect for web farms, container clusters, or shared media/content directories.

✅ 3. Standard File System Interface
Supports POSIX-compliant file operations: read(), write(), chmod(), etc.

Works with Linux EC2 instances without needing application changes.

✅ 4. High Availability & Durability
Automatically replicates data across multiple Availability Zones (AZs) in a region.

Built for 99.999999999% (11 9's) durability.


############### Ec2-1 #########################


sudo yum install -y amazon-efs-utils


sudo mkdir -p /mnt/efs        #sudo mkdir -p /mnt/efs


sudo mount -t efs fs-03d767529b5ccfd9d:/ /mnt/efs  #Mount the EFS filesystem



df -h | grep efs


cd /mnt/efs

sudo touch testfile.txt

ls -l

################# EC2-2 ###########################

sudo yum install -y amazon-efs-utils


sudo mkdir -p /mnt/efs #sudo mkdir -p /mnt/efs


cd /mnt/efs

la 

####################  EBS vs EFS ##################


| Feature          | **Amazon EFS**                                          | **Amazon EBS**                                        |
| ---------------- | ------------------------------------------------------- | ----------------------------------------------------- |
| **Type**         | File Storage (shared filesystem)                        | Block Storage (like a virtual disk)                   |
| **Mounts to**    | Multiple EC2s at once (shared access)                   | Only one EC2 at a time (except Multi-Attach for
some) |
| **Protocol**     | NFSv4                                                   | iSCSI                                                 |
| **Scalability**  | Auto-scales to petabytes                                | Fixed size (must resize manually)                     |
| **Use Cases**    | Shared file systems, web/app servers, container storage | Databases, boot volumes, applications
with high IOPS  |
| **Performance**  | Good for throughput & parallel access                   | Better for low-latency, high-IOPS workloads
|
| **Availability** | Multi-AZ (by default)                                   | Single-AZ (Multi-AZ via replication or snapshots)     |
| **Backup**       | AWS Backup, snapshots                                   | Snapshots, lifecycle manager                          |
| **Latency**      | Higher than EBS (network filesystem)                    | Lower (directly attached)                             |
| **Pricing**      | Pay-per-use (GB/month), tiered                          | Pay for provisioned size (GB/month)                   |
| **Access Type**  | Shared file system (multiple instances)                 | Exclusive disk (per EC2)                              |
| **OS Support**   | Linux only                                              | Linux and Windows                                     |


################ Common usecase #############

Shared Web Hosting (Web Servers Behind Load Balancer)
Use Case: Multiple EC2 web servers serving a single website (e.g., Apache, Nginx) behind an ELB.
Problem: User uploads (e.g., images, PDFs) saved on one instance must be instantly visible on others.
Solution: Mount a shared EFS volume on all EC2s → all uploads and logs are stored in one place.
■ Ensures consistency across all servers
■ No need to sync files manually


############ EBS #################

lsblk-  List Block Devices
→ Lists all attached disks and partitions (very useful for EBS).
Your current lsblk output shows only one main volume xvda of size 8G with partitions mounted at / and /boot/efi.
If you recently increased the EBS volume size in AWS Console but don’t see the updated size here, it means the OS
has not detected the new volume size yet.

df -h  ###df -h — Disk Free (filesystem usage) 	→ Shows disk usage for all mounted filesystems in human-readable format.

mkfs -t ext4 /dev/xvdf

mkfs: The command itself, which stands for "make file system".
-t ext4: The option -t specifies the type of file system to create. In this case, it's ext4, which is a popular file system type used in Linux.

/dev/xvdf: 	The device on which to create the file system. In this case, it's a block device named xvdf

sudo mount /dev/xvdf /mnt/data		→ Mounts the volume to a directory.

sudo umount /mnt/data		→ Unmounts a mounted volume.

file -s /dev/xvdf		→ Checks if the disk is already formatted.

du -sh /mnt/data     → Shows total space used by files in a directory.

mount    → Lists all currently mounted filesystems.

sudo growpart /dev/xvda 1         --> You can increase volume size anytime — no downtime required.


##################################EBS Storage additional volume attach process ############################################


#### If i create new volume and attach to ec2 instance how to update the file system to use that created new volume? ########################

Create a new additional volume and attach to ec2 then connect to server run below commands
sudo mkfs.ext4 /dev/xvdb         #Format the volume (assuming the volume is /dev/sdb and you want to use ext4 file sy
stem  here xvdb=sdb  s = xv)
sudo mkdir /mnt/data            # Create mountpoint directory
sudo mount /dev/xvdb /mnt/data  #mount the volume


##After you can test Add Content to the Mounted Volume

1. Switch to the mount directory
cd /mnt/data
2. Create a test file
3. Write content to the file
echo "This is a test file on xvdb mounted volume." | sudo tee testfile.txt
##### Use Case--> When to Use an Additional Volume (EBS)
1. Separate Application Data
Store app files, logs, uploads, DB files, etc., on a dedicated volume.
Keeps data safe even if the root volume (OS) is corrupted or replaced.
2. Need More Storage Space
When the root volume (/dev/xvda) is full or insufficient for your needs.
3. Performance Isolation
Separate volumes can be optimized with different IOPS (e.g., gp3, io1).
Useful for databases, caching, or high-throughput logging.
4. Data Persistence Across Instance Lifecycle
If you stop/terminate an instance, you can detach the additional volume and attach it to another instance.
Helpful for backups, migration, or recovery.
-- volume resize -----------------
sudo growpart /dev/xvda 1   Note:This expands partition 1 (xvda1) to fill the newly resized 10 GB EBS volume.
=========================================================================================




 #########################please practice these commands also #################################

🧭 Navigation & File Management

| Task                            | Command                         | Description                               |
| ------------------------------- | ------------------------------- | ----------------------------------------- |
| View file type                  | `file <filename>`               | Shows file type info (text, binary, etc.) |
| View file size in human format  | `ls -lh`                        | Adds readable size units                  |
| Count lines, words, chars       | `wc file.txt`                   | Shows counts; `wc -l` for line count      |
| Search recursively in directory | `grep -r "pattern" /path`       | Searches inside all files under /path     |
| Compare two files               | `diff file1 file2`              | Shows line-by-line difference             |
| Combine multiple files          | `cat file1 file2 > merged.txt`  | Concatenates                              |
| Find files by name              | `find / -name filename.txt`     | Searches full filesystem                  |
| Find files by size              | `find / -size +100M`            | Files larger than 100MB                   |
| Sort file contents              | `sort file.txt`                 | Alphabetical sorting                      |
| Remove empty files              | `find . -type f -empty -delete` | Cleanup empty files                       |


⚙️ System Monitoring & Performance

| Task                      | Command           | Description                            |
| ------------------------- | ----------------- | -------------------------------------- |
| View system uptime        | `uptime`          | Shows how long system has been running |
| Real-time process viewer  | `htop`            | Better UI than `top`                   |
| Disk usage by folder      | `du -sh *`        | Shows folder size summary              |
| Check memory usage        | `free -h`         | Displays RAM usage                     |
| Check CPU info            | `lscpu`           | CPU model, cores, etc.                 |
| Check block device info   | `lsblk -f`        | Shows filesystem type and UUID         |
| Monitor I/O               | `iostat -x 1`     | Shows disk I/O stats per second        |
| Monitor network bandwidth | `iftop` / `nload` | Shows real-time network traffic        |
| View last reboot info     | `last reboot`     | Shows reboot history                   |
| Check system logs         | `journalctl -xe`  | View logs on systemd systems           |



🧑‍💻 User & Group Management

| Task                         | Command                    | Description                     |
| ---------------------------- | -------------------------- | ------------------------------- |
| Show current users logged in | `who` / `w`                | Shows logged-in users           |
| Check user info              | `id username`              | UID, GID, groups                |
| Change user password         | `passwd username`          | Updates password                |
| List groups                  | `cat /etc/group`           | Displays group data             |
| Delete a user                | `userdel -r username`      | Removes user and home directory |
| Switch user temporarily      | `sudo -u username command` | Run command as another user     |


🔐 Permissions & Ownership

| Task                              | Command                              | Description                     |
| --------------------------------- | ------------------------------------ | ------------------------------- |
| Change file owner                 | `chown user:group file`              | Modify file ownership           |
| Apply same permission recursively | `chmod -R 755 dir/`                  | Applies to all subfiles         |
| Default permission for new files  | `umask 022`                          | Sets default file creation mask |
| View file ACLs                    | `getfacl file.txt`                   | Advanced permissions            |
| Set file ACL                      | `setfacl -m u:username:rwx file.txt` | Add per-user permissions        |


🌐 Networking & Connectivity

| Task                     | Command                      | Description                |
| ------------------------ | ---------------------------- | -------------------------- |
| Check route table        | `ip route`                   | Shows network routing info |
| Check active connections | `netstat -tunap`             | Show all open connections  |
| DNS lookup               | `dig google.com`             | Advanced DNS query         |
| Ping host                | `ping -c 4 8.8.8.8`          | Test network connectivity  |
| Trace route              | `traceroute google.com`      | Shows hop path             |
| Test port using nc       | `nc -zv 10.0.0.1 22`         | Alternative to telnet      |
| Restart network          | `systemctl restart network`  | Restart service            |
| Show interfaces          | `ip addr show`               | Show IPs and interfaces    |
| Download file            | `curl -O <URL>`              | Download file via URL      |
| Upload via scp           | `scp file.txt user@ip:/path` | Secure copy over SSH       |


📦 Package Management (Cross Distro)

| Distro                | Command                           | Description           |
| --------------------- | --------------------------------- | --------------------- |
| RedHat/CentOS/Amazon  | `yum update -y`                   | Update all packages   |
| RedHat 8+             | `dnf install <pkg>`               | Newer YUM replacement |
| Ubuntu/Debian         | `apt update && apt upgrade -y`    | Update system         |
| Check package version | `rpm -qi <pkg>` / `dpkg -l <pkg>` | Query package info    |


🧰 System Services

| Task                 | Command                               | Description          |
| -------------------- | ------------------------------------- | -------------------- |
| List all services    | `systemctl list-units --type=service` | Show active services |
| Check service status | `systemctl status nginx`              | Service status       |
| Start/Stop/Restart   | `systemctl restart sshd`              | Manage services      |
| Enable service       | `systemctl enable nginx`              | Auto-start on boot   |
| Disable service      | `systemctl disable nginx`             | Disable auto-start   |


🪄 Shell & Process Control

| Task                      | Command             | Description              |
| ------------------------- | ------------------- | ------------------------ |
| Run process in background | `command &`         | Background execution     |
| Bring job to foreground   | `fg`                | Resume background job    |
| Kill process by PID       | `kill -9 <PID>`     | Force kill               |
| Kill by name              | `pkill nginx`       | Kill all nginx processes |
| Show jobs                 | `jobs`              | Background jobs list     |
| Record session            | `script output.txt` | Save terminal session    |


🧱 Compression & Archiving

| Task                | Command                       | Description   |
| ------------------- | ----------------------------- | ------------- |
| Create tar archive  | `tar -cvf archive.tar files/` | Archive files |
| Extract tar archive | `tar -xvf archive.tar`        | Extract       |
| Create gzip         | `gzip file.txt`               | Compress file |
| Unzip gzip          | `gunzip file.txt.gz`          | Decompress    |
| Create zip          | `zip -r archive.zip folder/`  | Zip a folder  |
| Extract zip         | `unzip archive.zip`           | Unzip         |


🧾 Logging & Auditing

| Task                     | Command                                     | Description       |                        |
| ------------------------ | ------------------------------------------- | ----------------- | ---------------------- |
| View authentication logs | `cat /var/log/secure` / `/var/log/auth.log` | SSH and sudo logs |                        |
| Kernel messages          | `dmesg                                      | less`             | Boot and hardware logs |
| System logs              | `journalctl -u nginx`                       | Service logs      |                        |
| Recent system boots      | `journalctl --list-boots`                   | Boot history      |                        |
| Log filtering            | `grep "error" /var/log/messages`            | Find errors       |                        |




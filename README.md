# Born2beroot
Born2beroot (42cursus). This project aims to introduce you to the wonderful world of virtualization.

# What is an operating system?

* An operating system is a program that acts as an interface between the computer user and computer hardware, and controls the execution of programs. 
* manages all of the software and hardware on the computer. 

# APT : (Advanced packaging tool)

	package management system, The aim is to easily search, install and update the software packages, APT consists of a program library and this library multiple-use command-line programs, of which apt-get and apt-cache are the keys.

# Aptitude : 
	is front-end to apt

# The differences between aptitude and apt :
 
- Apt : 
	* apt gonna install all depends
	* lower-level package

- Aptitude :
	* install the depended what you want
	* high-level package manager

# Sudo (superuser do) 
   * Is a utility for UNIX- and Linux-based systems that provides an efficient way to give specific users permission to use specific system commands at the root (most powerful) level of the system.

# Append a user to secondary groups with usermod command
sudo group :
A group of superusers that can access the root account : 
    ```usermod -a -G sudo username```
To create a user : 
    ```useradd username```
To create a group : 
    ```addgroup group_name```
To delete a user : 
    ```userdel usernameA```		
To delete a user from group :	 
    ```gpasswd --delete username group```


# What is SSH ?

=> SSH or Secure Shell is a network communication protocol that enables two computers to communicate and share data.

# What is an ssh port ?

=> SSH needs ports to connect and start the communication. 
=> There are more than 65k communication ports available and you can start the communication using any of these ports. 


# TCP

- TCP (Transmission Control Protocol)

     * Is one of the main protocols of the Internet protocol suite. 
     * It lies between the Application and Network Layers which are used in providing reliable delivery services.
     * Unicast connection, is one to one transmission from one point in the network to another point “(one sender and one receiver)
     
- UDP (User Datagram Protocol) that have multiple(one sender and multiple receivers)
- podcast(one sender and all receivers) connection.

# UFW (Uncomplicated Firewall)

- Firewall is a network security device — computer hardware or software — that can help protect your network by filtering traffic and blocking outsiders from gaining unauthorized access to the private data on your computer.

- UFW, or Uncomplicated Firewall, is an interface to iptables that is geared towards simplifying the process of configuring a firewall.

- cmd :

* Know UFW is active or not :
	```ufw status```
* Active UFW :  
	```ufw enable```
* inactive UFW : 
	```ufw disable```
* to add a rule : 
	```sudo ufw allow “rule”```
* to delete a rule :
	```
	sudo ufw status numbered
	sudo ufw delete >number<
	```

# how to change hostname ?
```
sudo nano /etc/hostname
sudo nano /etc/hosts
sudo reboot
```
# Setting up the sudo policies
```
/etc/sudoers.d/sudo_config
```
# What is a file with extension .sh?

It is a Bourne shell script. They are used in many variations of UNIX-like operating systems. They have no "language" and are interpreted by your shell (interpreter of terminal commands)

# Script shell

- What Does the wall Command Do?

	* wall is short for write to all. The purpose of the command is to send a quick message to the terminals of all currently logged in users.
		
- Architectures :
	to see architectures of my operating system :
	```	“uname -a”
		“a” means all
		“uname” print certain system information.
	```
- User log :
	``` who | cut -d " " -f 1 | sort -u | wc -l ```

- The number of physical processors :
	``` grep “physical id” /proc/cpuinfo | wc -l ```

- The number of virtual processors : 
	``` grep “processor” /proc/cpuinfo | wc -l ```
	
- Memory Usage : 
	```used : free –mega | awk ‘$1 == “Mem:” {print $3}’```
	```total : free –mega | awk ‘$1 == “Mem:” {print $2}’```
	```percent : free –mega | awk ‘$1 == “Mem:” {printf(“%.2f”, (($3/$2)*100))}’```
	
- Disk Usage :
	df :  command – Shows the amount of disk space used and available on Linux file systems
	
- last boot : 
	cmd  :	```who -b | awk ‘ {print $3 “ “ $4}’	```
	who  :	show who is logged on.
	-b   :	time of last system boot
	
- Whether LVM is active or not : 
	cmd  :	```lsblk | grep lvm | wc -l | awk ‘{if (($1) != 0) {print “yes”} else {print “no”}}’```

- sudo : 
	cmd :	```sudo grep -a “sudo “ /var/log/auth.log | wc -l```
	cmd :	```grep "sudo" /var/log/auth.log | grep COMMAND | wc -l```

- Connection TCP : 
	cmd : 	```ss -ta | grep ESTAB | wc -l```
	ss : command used to show network statistics
	-ta : -a and -t with the ss command to output a list of all the TCP connections.
	ss -ta : dumps all TCP socket

- Network : 
	cmd : 	```IP $(hostname -I) $(ip link | grep "link/ether" | awk '{print $2}') ```
	ip link : Show information for all interfaces.

- CPU load : 
	cmd :	```$(vmstat 1 2 | tail -1 | awk '{printf("%.1f%%\n", 100-$15)}')```

# not be possible to connect using SSH as root :

	cmd ```vim /etc/ssh/sshd_config```
	change this : PermitRootLogin prohibit-password
	to : PermitRootLogin no

# Cron :
```
- Example of job definition :
-  .---------------- minute (0 - 59)
-  |  .------------- hour (0 - 23)
-  |  |  .---------- day of month (1 - 31)
-  |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
-  |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR  sun,mon,tue,wed,thu,fri,sat
-  |  |  |  |  |
-  \*  \*  \*  \*  \* user-name  command to be executed
```

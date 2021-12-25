# Linux Administrator Journey

# A Brief Into to Linux
	- Major distros: Arch, Debian, Red hat, Slackware
	- Linux Mint, Ubuntu, Kali, etc, from Debian
	- CentOS, Fedora, etc from Red Hat
	- The Bash shell is available in major OS.

# Ubuntu Desktop Installation
	- Installed Ubuntu Desktop on Virtual Box.
	- sudo apt install
	- sudo apt update
	- sudo apt install git -y
	- Git clone git://github.com/scottsimpson/commandlinebasics
	- move "Extercise Files" directory from commandlinebasics directory to Documents directory.
	
# xRDP Installation on Ubuntu Desktop
	- sudo apt install xrdp 
	- sudo systemctl status xrdp
	- sudo adduser xrdp ssl-cert  
	- sudo systemctl restart xrdp
	- sudo ufw allow from 192.168.33.0/24 to any port 3389
	- sudo reboot
	
# Enable SSH on Ubuntu Desktop
	- sudo apt update
	- sudo apt install openssh-server
	- sudo systemctl status ssh
	- sudo ufw allow ssh
	- Connecting to remote server (ssh username@ip_address)

# CLI
	- Command Line Interface
	- Send typed commands
	- Displays text output
	- Shell or interpreter
	- 1971: Thompson shell for UNIX
	- Bash: Bourne-again shell

# General Command Syntax
	- ls -lh /usr/bin
	- sort -u users.txt
	- grep -i "needle" haystack
	
	- #Command		#Option(s) 		#Arguments(s)
	
	# Command
	- The command is the program you are running.
		- example: ls, sort , grep
	# Options
	- Options tell the program how to operate.
		-lh, -u, -i "needle"
		- Start with a dash
		- Usually one letter
		- Most commands offer one or more option
	#Arguments
	-	Arguments tell the command what to operate on.
		-lh /usr/bin, -u users.txt, -i "needle" haystack

# Shortcuts
    
    Key Combination 		Results
    - Ctrl-U 				Remove (crop) from cursor to start
    - Ctrl-K				Remove (crop) from cursor to end
    - Ctrl-Y				Paste cropped text
    - Ctrl-Shift-C			Copy to clipboard
    - Ctrl-Shift-V			Paste from clipboard
	
# Files and Folders
	- cd is used to navigate to differennt directories
	- For example; bgiri@ubuntu-desktop:~$ cd ~/Documents/
	
	- bgiri@ubuntu-desktop:~/Documents$ cd Exercise Files
		bash: cd: too many arguments
	- Using quatation (" ") or backslach (" \ ") let us go in directories that has space 	in name.
	- bgiri@ubuntu-desktop:~/Documents$ cd Exercise\ Files
	
	- bgiri@ubuntu-desktop:~/Documents/Exercise Files$ ls -R departments
	- -R here is used to list all files within directories
	
	- cd .. (two dots represents the parent directory of the current directories.
	
	- bgiri@ubuntu-desktop:~/Documents/Exercise Files/departments/hr/policies$ cd ../..
	- bgiri@ubuntu-desktop:~/Documents/Exercise Files/departments$
	- cd ../.. takes you parent directory of the current directory and using twice cd ..  	will take you two times to the parent directory of the current directory
	- 

# Little more about ls
	- bgiri@ubuntu-desktop:~/Documents/Exercise Files$ ls -l
	total 148
		drwxrwxr-x 7 bgiri bgiri 4.0K Dec 25 00:13 departments
		-rw-rw-r-- 1 bgiri bgiri  160 Dec 25 00:13 dupes.txt
		-rw-rw-r-- 1 bgiri bgiri 128K Dec 25 00:13 log.tar.gz
		-rw-rw-r-- 1 bgiri bgiri 1.5K Dec 25 00:13 poems.txt
		-rw-rw-r-- 1 bgiri bgiri  129 Dec 25 00:13 simple_data.txt
		-rwxrwxr-x 1 bgiri bgiri   64 Dec 25 00:13 test.sh
		
		d means this is a directory
		l menas this is a link
		- means this is a file
		
		first 	'bgiri' means group
		second 	'bgiri' means user
		
		4.0K is the file or directory size.
	
# Wildcard *
	- using * with the file extenstion moves all files with the same format
	- exmaple command: mv *.txt departments/marketing/
	
	- using * only without the file extention moves all files from the directory
	- example command: mv departments/marketing/* .
	- dot at the end is used to move files parent folder of defined directories
	- result :~/Documents/Exercise Files$ ls
		departments  dupes.txt  literature.txt  log.tar.gz  new_folder  poems.txt  simple_data.txt  test.sh

# remove
	- rm to remove file
	#Wildcard ?
	- Command example: rm poems?.txt
	- deletes poems with only one chractor afterwards
	- rm -R deletes the directory which has files in it.
	- -R stands for recursive
	
# find command
	- find command finds the files in directory with differnet parameteros
	- example command: find . -name "poe*"
	- 

# User Roles
	- Linux is a multiuser envirement
		- Users files are kept separate su command
	User roles
		- Normal user: modify thier own files, cannot make system changes
		- Superuser (root): modify any file, make system chanegs
	- use sudo to access privilaged files or directories
	- once used sudo there is a grace period which keeps user in superuser mode
	- once done with sudo, use sudo -k to give up on superuser mode
	- sudo -s | to switch over the root user
	- type exit to come back to normal user mode

# File Permissions
		rwx		rwx		rwx		the_file
		rwx		r-x		r-x		the_file_2
		User	Group	Others
		
				rwx					
		read Write Execute
		
**chmod**
Changes the permissions on a file by modifying the file mode bits.
Two methods to represends permissions
- Octal (e.g., 755, 644, and 777)
- Symbolic (e.g., a-r,g+w, and o-x)

Octal File Permissions
			Read (4)	Write (2)	Execute (1)	Result
		User	r		w		x		7
		Group	r		-		x		5
		Others	r		-		-		4

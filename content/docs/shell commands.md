
2025-02-15 15:13

Level: #child

Tags : [[linux]]

Use any of the following options to get more information about linux commands:
man commandName
info commandName
commandName -h
commandName --help
## Intro
- When you type a command in the terminal, your system looks for the executable file in the directories listed in the $PATH variable. If a directory isn't in $PATH, you must specify the full path to run a script
## env 
- This command will show special variables
## ls

- This command is used when listing all the files that are inside a container.
- It has several combinations such as -al which returns more detailed information about the files inside a particular folder.
## lsblk
- This command will show the disks and their partitions info of your pc
# cat
- This command is used to show the contents of a file eg  
     cat /etc/systemd/network.sh 
## cd

- The change directory command makes it possible for you to move inside a specified path/folder.
- by using cd .. ,you move to the previous directory/parent folder.

## pwd

- This command is used to know which directory you are in, by running it ,it will print the current folder path

## mkdir

- This command is used to create folders
- YOu can create multiple folders with one command: mkdir dogs people
- You can also create multiple nested folders by adding the -p option: mkdir -p fruits/apples

## rmdir

- Used to delete a folder or multiple folders at once ( The folder must be empty)
- To delete folders with files in them (rm -rf fruits people)

## mv

- Used to move a file by specifying the file's current path and its new path
- (mv pear new_pear) - Renaming files and folders
- If the last parameter is a folder, the file located at the first parameter is going to be moved into the folder
- (mv pear apple fruits) - pear and apple moved to the fruits folder

## cp

- Used to copy a file
- To copy folders, you need to add the -r to recursively copy the whole folder contents (cp -r fruits people)

## touch

- Used to create an empty file eg touch apple

## open

- Used to open a directory
- (open .) - opens the current directory
- Can also be used to open an application

## find

- The find command can be used to find files or folders matching a particular search pattern. It searches recursively
- (find . -name '*.js') - Find all files under the current tree that have the .js extension and print the relative path of each file that matches
- (find . -type d name src) - Find directories under the current tree matching the name 'src'
- (find folder 1 folder 2 -name filename.txt) - Searching under multiple root trees
- (find . -type d -name node_modules -or -name public) - Find directories under the current tree matching the name 'node_modules' or 'public'
- (find . -type d -name '_.md' -not -path 'node_modules/_') - excluding a path
- (find . -type f -size +100c) - Searching files that have more than 100 characters(bytes) in them
- (find . -type f -size +100k -size -1M) - Searching files bigger tha 100KB but smaller than 1MB
- (find . -type f -mtime +3) - Searching files edited more that 3 days ago
- (find . -type f -mtime -1) - Searching files edited in the last 24 hrs

## ln

- Used to create links(Pointer to another file)
- There are two types of links(hard links and soft links
- Hard links are rarely used. You cant link to directories and external filesystems
- (ln recipes.txt newrecipes.txt) - Creating a hard link
- Soft links are different. They are more powerful as you can link to other filesystems and to directories but when the original is removed, the link will be broken
- (ln -s recipes.txt newrecipes.txt) - Creating a soft link

## gzip

- Used for compressing a file
- (gzip filename) - This will compress the file and append the .gz extension to it and the original file is deleted. To prevent this, use the -c option and use the output redirection to write the output to the filename.gz file. ( gzip -c filename > filename.gz)
- (gzip -d filename.gz) - Decompressing the file

## gunzip

- Basically the equivalent of gzip only that when decompressing, no need for adding the -d

## tar

- Used to create an archive, grouping multiple files in a single file
- (tar -cf archive.tar file1 file2) - Creates an archive named archive.tar with the content of file1 file2
- (tar -xf archive.tar) - Extract files from an archive in the current folder

## alias

- This is like creating a new command to mimic an existing command so that you dont use the existing command according to your preferences
- (alias ll = 'ls -al') - Creating a new command 'll' that is an alias to 'ls -al'
- (alias) - will list all the aliases defined
- The alias will work until the terminal sessions is closed
- To make it permanent, add it to the shell configuration

## tail

- Opens the file at the end and watches for file changes
- Great for watching log files ( tail -f /var/log/system.log )

## grep

- Used to search in lines or can be combined with pipes to filter the output of another command
- (grep "error" logfile.txt) - Finds and prints all lines in logfile.txt containing the word "error"
- (grep "hello" file1.txt file2.txt) - Searches for "hello" in both files
- You can use -i to ignore case sensitivity
- (grep -i "error" logfile.txt) - Finds "Error", "error" ,etc
- Can also be used in searching in the output of another command as shown in the next line
- ps aux | grep "firefox"
- (grep -v "error" logfile.txt) - Inverting the search ie exclude all lines that contain the pattern
- (grep -n "command" logfile.txt) - Shows the line numbers where "command" has appeared
- (grep -c "error" logfile.txt) - counts the number of lines containing "error"
- (grep "^hello" file.txt) - search for lines that start with "hello"
- (grep "done$" file.txt) - search for files that end with "done"

## sort

- Used in sorting elements in a file
- (sort -r filename.txt) - Reverses the order of sorting
- Can work with pipes,i.e you can use it on the output of another command ls | sort

## echo

- echo "Hello world" - prints a simple messsage
- name="John", echo "Hello $name" - This will print the value of variable
- echo "Hello, file" > output.txt - This will direct the output to a file but will override the contents of that file
- echo "Hello file" >> output.txt - This will append or add another line at the end of output.txt
- echo "Today is $(date) - Using echo with other commands

## chown

- Every file/directory in linux has an owner
- This command is used to change the owner of the file or directory
- The owner of a directory/ file or the root user are eligible to use this command
- sudo chown astro test.txt - Transferring the file ownership to astro
- chown -R - Changing the ownership of a directory and all other files in it.
- chown : - Through this command,I can simulataneousy change the owner and the group of the file
- chgrp - Directly changing the group of the file

## chmod

- Used to change the permissions of a file
- Every file has 3 permissions (read, write and execute)
- For example if a go into a directory and run ls -al, the following is displayed :  
    drwxrwxr-x 4 astro astro 4096 Feb 9 11:33 .  
    drwxr-x--- 31 astro astro 4096 Feb 12 14:50 ..  
    drwxrwxr-x 8 astro astro 4096 Feb 13 12:32 .git  
    drwxrwxr-x 2 astro astro 4096 Feb 13 12:39 linux-basics  
    -rw-rw-r-- 1 astro astro 163 Feb 9 11:32 README.md
- The letters and hyphens you see at the start of every file/folder are the permissions given of the file/folder
- (-) means its a normal file
- (d) means its a directory
- (l) means its a link
- After that, the first 3 values eg rwx represents the permissions of the owner of the file/directory
- The next 3 values eg r-x represents the permissions of the group of the file
- The last 3 values eg --- represents the permissions of the other members or everyone else that comes across the file
- rwx means that person has read, write and execute permissions of the file/directory
- If either of the rwx values is swapped with - ,that means that person lacks the swapped permission eg :
- r-x means the person has read and execute permission but lacks the write permission
- You can change the permissions using the chmod command
- Changing permissions using numeric notation discussed below :  
    Each Permission has a numeric value :  
    r = 4  
    w = 2  
    x = 1
- chmod 755 file.txt - This command sets the owner : rwx (7), Group r-x (5) and others r-x (5)
- Changing the permissions using symbolic notation as shown below :  
    u = Owner  
    g = Group  
    o = Others
- chmod u+w file.txt - This adds the write permission to the Owner
- chmod g-x file.txt - This removes the execute permission from the group
- chmod o+r file.txt - This adds the read permission for others

## du

- This command will calculate the size of a directory as a whole
- du * - This will calculate the size of each file individually
- du -m - Displaying the size in Megabytes
- du -g - Displaying the size in Gigabytes
- du -ah - -a wil print the size of each file, -h will show a human readable notation for sizes

## df

- Used to get disk usage information
- Its basic form will print information about volumes mounted
- df -h will show the values in human readable format

## ps

- Used to inspect processes that are running on your machine
- ps ax - "a" will list other users' processes apart from yours and "x" will show other processes not linked to any terminal
- You can search for a specific process combining grep with a pipe as shown below :  
    ps ax | grep -i "tensorflow" | head
# pstree
- Command for displaying processes running on your system in a tree structure 

## top

- Used to display dynamic real time information about running processes in your machine

## kill

- Linux processes can receive signals and react to them therefore we can interact with running programs
- The kill command is used to terminate a program (kill ). The PID is the process ID
- We can use the kill command to send other signals apart from terminating a program as follows :  
    kill -HUP - hang up - It is sent automatically when a terminal window that started a process is closed before terminating the process  
    kill -INT - interrupt - It sends the same signal used when we press ctrl - c in the terminal, which usually terminates the process  
    kill -KILL - This is not sent to the process, but to the operating system which immediately stops but not terminate the process  
    kill -TERM - terminate - Its the default signal sent by kill  
    kill -CONT - continue - Used to resume a stopped process  
    kill -STOP - stop is sent to the operating system kernel which immediately stops but does not terminate the process
- You might see numbers used instead, like kill -1 . In this case,1 corresponds to HUP. 2 corresponds to INT. 9 corresponds to KILL. 15 corresponds to TERM. 18 corresponds to CONT. 15 corresponds to STOP.

## type

- A command can be one of these 4 types :  
    an executable  
    a shell built-in program  
    a shell function  
    an alias
- The type command is used to figure out the type of a command
- type

# which

- This will return the path of the command specified
# man (manual)
- This command is used to display information about the specified command eg 
- man which 
# whoami

- This command will print the user name currently logged into the terminal session

# who

- This command displays the users logged in to the system

# su

- This command is used to switch to another user
- su

# sudo

- Used to run command as a root
- You must be enabled to use sudo and once you are authorised, you can run commands as root by entering your user's password
- You can use sudo to run commands as any user. root is the default but use the -u option to specify another user :  
    sudo -u astro ls /Users/flavio

# passwd

- Users in linux have a password assigned. You can change the password using the passwd command
- When you want to change your password, you can type :  
    passwd
- When you are root , you can set the username for which you want to change the password :  
    passwd

# ping

- This command pings a specific network host, on the local network or on the internet
- Syntax is ping where could be a domain name or an IP address
- This command sends a request to the server and the server returns a response
- ping keeps sending the request every second by default. It will keep running until you stop it with ctrl - c unless you pass the number of times you want to try with the -c option: ping -c google.com

# clear

- Used to clear all the previous commands that were run in the current terminal
- The screen will clear

# crontab

- Cron jobs are jobs that are scheduled to run at specific intervals. You might have a command perform something every hour, or every day, or every 2 weeks. Or on weekends.
- They are very powerful, especially when used on servers to perform maintenance and automations.
- crontab -l - exploring which cronjobs are defined by you

## uname

- This will return the Operating System codename eg Linux
- uname -mp - The m option shows the hardware name and the p option prints the processor architecture
- uname -a - This will print all the information available


## References

https://www.freecodecamp.org/news/the-linux-commands-handbook/

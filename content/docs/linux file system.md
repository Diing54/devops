
2025-02-15 18:08

Level : #child 

Tags : [[linux]]

# Filesystems in linux

"You see, back then, Linux was not the intuitive, user-friendly system it is today. You had to read a lot. You had to know things about the frequency rate of your CRT monitor and the ins and outs of your noisy dial-up modem, among hundreds of other things. I soon realized I would need to spend some time getting a handle on how the directories were organized and what all their exotic names like _/etc_ (not for miscellaneous files), _/usr_ (not for user files), and _/___bin__ (not a trash can) meant." ~ Paul Brown

/ - This is the root directory

## /bin
- This directory contains binaries - these are some of the applications and programs that can run
- There are still more bin directories
## /boot
- Contains files that are required for starting the system - do not mess with anything here
## /dev
- Contains device files - generated at boot time or when you plug in a usb stick ,it will pop up here
## /etc
- Gets the name from "et cetera" because at the earlier days of linux, system administrators would dump files they were not sure to put but nowadays its not the case, etc stands for "everything to configure" because it contains most of the system files configurations. Users in the system, their passwords, system name files, disk partition details.
## /home
- This contains the users' personal directories, my personal directory is home/astro. Will soon create another user home/guest for anyone that wants to use my system.
## /lib
- Contains libraries - these are files containing code that applications use to run
- There are other /lib directories but this one is special as it contains the kernel modules/drivers eg sound card, video card, wifi , bluetooth etc
## /media
- This is where the external storage is mounted when you plug it in your machine
## /mnt
- Not used very often but it was used days back when manually manually mounting storage devices
## /opt
- The directory where the software you build yourself will land. Applications will land in /opt/bin and libraries in the /opt/lib directory
- Applications and libraries may also end up in /usr/local/bin and /usr/local/lib directories, this will depend with the configurations of developers
## /proc
- This is a virtual directory like /dev. Contains information about your computer eg CPU info and the kernel your Linux system is running. The files and directories are generated when your sytem is booting or when certain files related to it are changing
## /root
- This is the home directory of the superuser. Dont confuse it with the root directory "/"
## /run
- This is where system processes use to store temporary data
## /sbin
- Similar to /bin but it contains the applications the superuser will need. Contains tools that install stuff, delete stuff and format stuff
## /usr
- Back in the days, this was where users' home directories were originally kept
- These days it contains directories of applications, libraries, documentation, wallpapers, icons and other stuff to be shared by applications and services
- Contains bin, sbin and lib directorries as well. Originally, the _/bin_ directory (hanging off of root) would contain very basic commands, like `ls`, `mv` and `rm`; the kind of commands that would come pre-installed in all UNIX/Linux installations, the bare minimum to run and maintain a system. _/usr/bin_ on the other hand would contain stuff the users would install and run to use the system as a work station, things like word processors, web browsers, and other apps.
- But many modern Linux distributions just put everything into _/usr/bin_ and have _/bin_ point to _/usr/bin_ just in case erasing it completely would break something.
## /srv
- Contains data for servers eg a web server, HTML files would be stored at _/srv/http_ (or _/srv/www_). If ruuning a FTP server, the files will be stored at /srv/ftp
## /sys
- This is another virtual directory like /proc and /dev, it also contains information from devices connected to the computer
## /tmp
- Contains temporary files from applications running in the system
- You can also use it to store your own temporary files 
## /var
- Contains var/log subdirectories, logs are files that register events that happen on the system.  If something fails in the kernel, it will be logged in a file in _/var/log_; if someone tries to break into your computer from outside, your firewall will also log the attempt here. It also contains _spools_ for tasks.These “tasks” can be the jobs you send to a shared printer when you have to wait because another user is printing a long document, or mail that is waiting to be delivered to users on the system.


## References

1. https://www.linuxfoundation.org/blog/blog/classic-sysadmin-the-linux-filesystem-explained
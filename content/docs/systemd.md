

2025-04-22 18:49

Level : 

Tags : [[linux]]

# systemd

- Systemd is an init system in Linux-based operating systems that is responsible for starting the operating system and managing various services and processes.
- Think of it as the conductor for the system's startup and ongoing operations, ensuring that everything runs smoothly.
- In older times, there was the System V initialization system (SysV init) which was popular for launching processes at startup.
- systemd attempts to decrease boot times and parcel out system resources more efficiently by starting processes concurrently and in parallel, and starting only necessary services, leaving other services to start after boot as needed.

### PID 1 - Mother of all Processes
- PID 1 is the mother of all processes on Linux systems. This is the first process to start then it launches all other processes. Processes are one or more running instances of a program.
- Processes can create independent copies of themselves which are the child processes and the original the parent process. Each child has its own PID  and its own allocation of system resources.
- Threads are lightweight processes that run in parallel and share system resources with their parents.
- Some processes run in the background and do not directly interact with the users, these are processes are ; services or daemons and their names tend to end with letter d such as httpd, sshd and systemd.
- ps command to list all running processes in PID order
- The pstree command organizes this mass of information into a tree diagram showing all processes, their child processes, PIDs, and threads, which are enclosed in curly braces.
- Processes always exist in one of several states, and these states change according to system activity. 
• R is either currently running or waiting in the run queue.
• l means the process is multithreaded.
• S is interruptable sleep; the process is waiting for an event to complete.
• s is a session leader. Sessions are related processes managed as a unit.
• I is an idle kernel thread.
• < means high priority.
• N is low priority.

- systemctl is used to list services and their states ; We are interested in service files because Linux users and administrators interact mainly with service files and rarely need to bother with any other type of unit file.
- To check the service files, we use the command ;
- systemctl list-unit-files --type=service
- The four most common states that a service can be in: enabled, disabled, static, or masked.
- List only enabled services: $ systemctl list-unit-files --type=service --state=enabled

- enabled - This shows that the service has become available and is managed by systemd.
- When a service is enabled, systemd creates a symlink in /etc/systemd/system/ from the unit file in /lib/systemd/system/. It can be started, stopped, reloaded, and disabled by the user with the systemctl command. Enabling a service does not immediately start it, and disabling a service does not immediately stop it.
- disabled - Disabled means that there is no symlink in /etc/systemd/system/, and it will not start automatically at boot. You can stop and start it manually.
- masked - This means the service is linked to /dev/null/. It is completely disabled and cannot be started by any means.
- static - This means that the unit file is a dependency of other unit files, and cannot be started or stopped by the user.
- systemctl status bluetooth.service - used for querying the status of selected services
- Start a service: $ sudo systemctl start sshd.service
- Stop a service: $ sudo systemctl stop sshd.service
- Stop and then restart a service: $ sudo systemctl restart sshd.service
- Reload the service’s configuration. For example, you made a change to sshd_config and want to load the new configuration without restarting the service: $ sudo systemctl reload sshd.service
- Enabling a service configures it to automatically start at boot.e.g sudo systemctl enable sshd.service
- Stopping troublesome processes can also be done by killing them; $ sudo systemctl kill mariadb ,$ systemctl status mariadb
● mariadb.service - MariaDB 10.1.44 database server
- Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
Active: inactive (dead) since Sun 2020-06-28 19:57:49 PDT; 6s ago
- The service has cleanly stopped. If this does not work, then try the nuclear option: $ sudo systemctl kill -9 mariadb
- top command is used to identify processes using up the most CPU resources
## References

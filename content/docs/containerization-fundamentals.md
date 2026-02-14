---
title: "Containerization Fundamentals"
date: 2026-02-12
tags: ["linux","docker"]
---

*Date: 2026-02-12*
{{< tags >}}

## Intro
A Container - A linux process(one or many) with a set of kernel features applied to it.

Another definition - A regular linux process with restricted view of;
- the filesystem
- other processes
- networking
- system resources

The restriction is enforced by;
1. Namespaces - What the process can see
2. Cgroups - Managing/limiting system resources
3. Filesystem Isolation - What files the process can access

## Filesystem Isolation using `chroot` (Change Root)
`chroot` is a shell command that changes the apparent root directory of the current running process and its children. In simple terms, its changing a particular directory to be the new root directory. Once inside , you can't access any directory above it.

This is how the command is used;

```bash
sudo chroot ~/test /bin/bash
```

- `~/test` is the directory we want to make the new root for the process we are executing in the command which is `/bin/bash`
- The child processes such as commands ran through bash will reference `~/test` as their root (\)

```bash
~/test ❯ sudo chroot ~/test /bin/bash
bash-5.3# pwd
/
bash-5.3# echo "this is an isolated filesystem"
this is an isolated filesystem
bash-5.3#
```

Before using chroot, the following are the requirements;
- Root privileges - Sudo command
- Complete environment - The new root directory must contain all necessary files and essential binaries

## Namespaces
This is a feature of the linux kernel that enables the separation and isolation of kernel resources such that one set of processes sees one set of resources, while another set of processes sees a different set of resources.

## Types of Namespaces

| Namespace | Isolates | Explanation |
| :--- | :--- | :--- |
| **PID** | Process IDs | Allows a process to have its own set of PIDs (e.g., a container can have its own PID 1). |
| **NET** | Network interfaces | Provides isolated network stacks, including routing tables, IP addresses, and firewall rules. |
| **MNT** | Mount points | Isolates the file system hierarchy, so a process sees only the mounts it is allowed to see. |
| **UTS** | Hostname | Allows a process to have its own hostname and NIS domain name (useful for identifying containers). |
| **IPC** | Shared memory | Prevents processes in different namespaces from accessing each other's inter-process communication resources. |
| **USER** | User IDs | Maps a user inside the namespace to a different user on the host (e.g., root in a container is a non-root user on the host). |



## References
- https://www.redhat.com/en/topics/containers/whats-a-linux-container
- https://en.wikipedia.org/wiki/Chroot
- https://www.youtube.com/watch?v=JMcipa0g558

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



## References

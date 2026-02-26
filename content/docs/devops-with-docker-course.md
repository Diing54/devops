---
title: "DevOps with Docker (Course)"
date: 2026-02-26
tags: ["devops","docker","linux"]
---

*Date: 2026-02-26*
{{< tags >}}

## Intro
This is my summary/takeaway from a free Docker course provided by [The University of Helsinki MOOC Centre](https://courses.mooc.fi/org/uh-cs/courses/devops-with-docker).

*Docker* ---> A set of tools used to deliver software in containers.

*Containers* are packages of software. They are isolated so that they don't interfere with each other or the software running outside them.

Docker offers tools to enable interaction between containeres.

## Benefits of Containers
1. *Solves the "Works on my Machine" Problem* ---> Developers can run an application inside a container, which packages everything needed for it to run including its source code.

2. *Isolated Environments* ---> With containers, it's possible to run different applications on the same machine even if they require different version of same dependencies for them to run. Each application is packaged on its own container with its requirements. Without containers, running them side by side would be a disaster.

3. *Development* ---> Containers ease up development processes. Lets say you are brought into a team developing a web application that uses multiple services like posgres database, redis e.t.c, with a few commands, you can spin up containers running these services instead of installing them manually on your machine.

4. *Scaling* ---> With advanced tooling, we can spin up multiple containers instantly and load balance traffic between them. This is useful for applications with higher demands. 



## References

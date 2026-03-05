---
title: "DevOps with Docker (Course)"
date: 2026-02-26
tags: ["devops","docker","linux"]
---

*Date: 2026-02-26*
{{< tags >}}

## Intro
This is my summary/takeaway from a free Docker course provided by **[The University of Helsinki MOOC Centre](https://courses.mooc.fi/org/uh-cs/courses/devops-with-docker)**.

**Docker** ---> A set of tools used to deliver software in containers.

**Containers** are packages of software. They are isolated so that they don't interfere with each other or the software running outside them.

Docker offers tools to enable interaction between containeres.

## Benefits of Containers
1. **Solves the "Works on my Machine" Problem** ---> Developers can run an application inside a container, which packages everything needed for it to run including its source code.

2. **Isolated Environments** ---> With containers, it's possible to run different applications on the same machine even if they require different version of same dependencies for them to run. Each application is packaged on its own container with its requirements. Without containers, running them side by side would be a disaster.

3. **Development** ---> Containers ease up development processes. Lets say you are brought into a team developing a web application that uses multiple services like posgres database, redis e.t.c, with a few commands, you can spin up containers running these services instead of installing them manually on your machine.

4. **Scaling** ---> With advanced tooling, we can spin up multiple containers instantly and load balance traffic between them. This is useful for applications with higher demands. 

## Images and Containers
An image provides all the necessary instructions and dependencies for the container to run. A docker image is a file that is **immutable**, meaning it cannot be changed or edited. Creating a new image happens by starting from a base image and adding new layers to it.

- `docker images` or `docker image ls` ---> List all your images.

An image file is built from a file named **Dockerfile** and it looks like this by default

```Dockerfile
FROM <image>:<tag>

RUN <install some dependencies>

CMD <command that is executed on `docker run container`>
```
A Dockerfile is the instruction set for building an image.

- `docker build -t {name}:{version/tag} {directory where the Dockerfile is}` ---> builds the docker image from the Dockerfile.

Containers contain the application and what is required to execute it. They are isolated environments in the host machine with the ability to interact with each other and the host machine itself.

- `docker ps` ---> list all running containers
- `docker ps -a` ---> list all containers whether running or stopped


## References

# Docker

The traditional way that a company or a business operates is by applications running on servers.  
One application on one server, because the operating systems didn't have the capability to run multiple applications securely on a single server.  
To fix this problem engineers developed _virtual machines_.  
Virtual machines allow multiple applications to run a single server simulating hardware and software.  
This one server is running three VMs.  
It's running different OS also the applications such as databases, web services, and email and they're all running side by side on one machine.

### Virtualization modes:

1. Server / Hardware -> Hypervisor -> VMs
2. Server / Hardware -> OS -> Hypervisor -> VMs

To build Virtual machines you start off with hardware and then on top of the hardware, there is software called a _Hypervisor_.  
A hypervisor is what allows one machine to run multiple virtual machines.  
It's what allocates and controls the sharing of a machine's hardware.  
On top of the hypervisor are the virtual machines and each will have its own operating systems such as Windows, Linux, and Unix.  
On top of the operating system, there are the applications that these machines are going to be running.

### What is kernel?

A kernel manages applications and hardware resources.  
Every OS has its own kernel and these kernels have different APIs, That's why we can not run a Windows application on Linux because under the hood this application needs to talk to the kernel of the underlying OS.

### What is KVM?

Kernel-Based Virtual Machine.  
KVM is a hypervisor that is built into the Linux kernel and for using it you just need to install some tools.

---

## What is docker?

A platform for building, running, and shipping applications.  
Reasons **It works on my machine** but not on other machines:

-   One or more files missing
-   Software version mismatch
-   Different configuration settings

With docker, we can easily package our applications with everything it needs and run them anywhere on any machine with docker installed.  
So in a nutshell _Docker_ helps us **Consistently** build, run, and ship applications.  
_The leading software that is used to create, manage, and run containers is docker._

---

## Virtual Machines vs Containers

-   Container
    An isolated environment for running an application
-   Virtual machine
    An abstraction of a machine (physical hardware)

    using a tool called _hypervisor_

A Hypervisor is software used to create and manage virtual machines.

Hypervisors:

-   VirtualBox
-   VMware
-   Hyper-v (windows only)

### What are the benefits of VMs and Containers?

run applications in isolation

### Problems with the virtual machine:

-   Each VM needs a full-blown OS (needs to be licensed, patched, and monitor)
-   Slow to start (because the entire OS has to be loaded)
-   Resource intensive (because each VM takes a slice of the actual physical hardware resources)
    -   Consume a lot of disk space
    -   Consume a lot of RAM and CPU power from the server

### Containers

A **container** is an application that's been packaged with all the _files_, _configurations_, and _dependencies_ necessary for it to run.  
give us the same kind of isolation (But with advantages over VM).  
The containers share the underlying operating system that's on the server between them.

-   allow running multiple apps in isolation
-   are lightweight
-   use the OS of the host
-   start quickly
-   need fewer hardware resources

---

## Architecture of docker

Docker uses a client-server architecture.  
So it has a client component that talks to a server component using a RESTful API.  
The server also called the **DOCKER ENGINE** sets in the background and takes care of building and running containers.  
Technically a container is just a process.  
All containers on a host share the _kernel of the OS_ of the host.  
Server / Hardware -> OS -> Container engine

#### What is a daemon?

In computing, a daemon (pronounced DEE-muhn) is a program that runs continuously as a background process and wakes up to handle periodic service requests, which often come from remote processes.

### Container Engine

1. A server with a long-running daemon process "dockerd".
2. Manages images & containers.

In a nutshell, the container engine is what unpacks the container files and hands them off to the operating systems kernel.  
**The Docker daemon:**  
The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

**When we have a service we need to communicate with that, so we need a client that can talk to that service.**

### Docker Client

Docker CLI Client:

1. Command Line Interface ("docker") to interact with the server.
2. Execute docker commands to start/stop/... containers.

The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

### Running containers

Any container requires the container image to run on a kernel that was designed for it.
Windows can run both Linux and Windows containers  
because Windows 10 is now shipped with a custom-built Linux kernel.  
Linux can only run Linux containers.  
MacOS (OSX) has its own kernel which is different from Linux and Windows kernels and this kernel does not have native support for containers of applications.  
so docker on MacOS makes uses a lightweight **Linux VM** to run Linux containers.  
Most containers run on a Linux kernel.  
So when you install Docker Desktop it will manage a local VM, running a tiny Linux kernel and tiny container file system.

-   Windows
    -   Linux containers
    -   Windows containers
-   Linux
    -   Linux containers
-   MacOS
    -   Linux containers

---

## Installing Docker

To work with Docker, we need _Docker Engine_ and _Docker Client_.  
Docker Desktop is the only way to install the Docker Engine on Windows 10 or 11 and macOS operating systems.  
Docker Desktop is also available for Linux, although Linux users are free to install the Docker Engine separately.  
We can install "Docker Desktop" (DD) or "Docker Engine" (DE) or both at the same time on Linux.

### Difference between "Docker Desktop" and "Docker Engine"

Docker Desktop is a superset for Docker Engine.  
Docker Desktop is not for servers.  
Docker Engine is for servers.  
Docker Desktop includes the following:

-   Docker Engine
-   Docker CLI
-   Docker Compose
-   Kubernetes
-   Credential Helpers
-   Snyk
-   BuildKit

We can install Docker Engine on the server and connect via ssh to the server and work with it, but there's an alternative way.
We can install only Docker CLI on our local system and connect to Docker Engine on the remote server.  
To achieve this simply set your docker host to the remote server:

```bash
export DOCKER_HOST=ssh://root@123.123.123.123
```

By default, DOCKER_HOST points to localhost.  
To unset this run command below:

```bash
unset DOCKER_HOST
```

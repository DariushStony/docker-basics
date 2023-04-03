# Docker

## What is docker?

A platform for building, running and shipping applications.

Reasons **It works on my machine** but not on other machines:

-   One or more files missing
-   Software version mismatch
-   Different configuration settings

With docker, we can easily package our applications with everything it needs and run them anywhere on any machine with docker installed.

So in a nutshell _Docker_ helps us **Consistently** build, run, and ship applications.

_The leading software that is used to create, manage, and run containers is docker._

## Virtual Machines vs Containers

-   Container
    An isolated environment for running an application
-   Virtual machine
    An abstraction of a machine (physical hardware)

    using a tool called _hypervisor_

A Hypervisor is a software used to create and manage virtual machine.

Hypervisors:

-   VirtualBox
-   VMware
-   Hyper-v (windows only)

### What are the benefits of VM and Container?

run applications in isolation

### Problems with virtual machine:

-   Each VM needs a full-blown OS (needs to be licensed, patched, and monitor)
-   Slow to start (because the entire OS has to be loaded)
-   Resource intensive (because each VM takes a slice of the actual physical hardware resources)
    -   Consume a lot of disk space
    -   Consume a lot of RAM and CPU power from server

### Containers

A **container** is an application that's been packaged with all the _files_, _configurations_, _dependencies_ neccessary for it to run.  
give us the same kind of isolation (But with advantages over VM)

-   allow running multiple apps in isolation
-   are lightweight
-   use OS of the host
-   start quickly
-   need less hardware resources

## Architecture of docker

docker uses a client-server architecture.

So it has a client component that talks to a server component using a RESTful API.

The server also called the **DOCKER ENGINE** sets in the background and takes care of building and running containers.

Technically a container is just a process.

All containers on a host share the _kernel of the OS_ of the host.

### What is kernel?

A kernel manages applications and hardware resources.

Every OS has its own kernel and these kernels have different APIs, That's why we can not run a windows application on Linux because under the hood this application needs to talk to the kernel of the underlying OS.

### Running containers

Windows can run both Linux and Windows containers

because windows10 is now shipped with a custom-built Linux kernel

Linux can only run Linux containers

MacOS has its own kernel which is different from Linux and windows kernels and this kernel does not have native support for containers of applications

so docker on makes uses a lightweight **Linux VM** to run Linux containers

-   Windows
    -   Linux containers
    -   Windows containers
-   Linux
    -   Linux containers
-   MacOS
    -   Linux containers

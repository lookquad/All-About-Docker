# Docker

***Definition from [Wikipedia](https://en.wikipedia.org/wiki/Docker_%28software%29)***

**Docker** is a Computer program that performs operating-system-level virtualization. It was first released in 2013 and is developed by [Docker, Inc.](https://en.wikipedia.org/wiki/Docker,_Inc. "Docker, Inc.")[](https://en.wikipedia.org/wiki/Docker_(software)#cite_note-os4u-8)
Docker is used to run software packages called [containers](https://en.wikipedia.org/wiki/Container_(virtualization) "Container (virtualization)"). Containers are isolated from each other and bundle their own application, tools, libraries and configuration files; they can communicate with each other through well-defined channels. All containers are run by a single [operating-system kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system) "Kernel (operating system)") and are thus more lightweight than [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine "Virtual machine"). Containers are created from _images_ that specify their precise contents. Images are often created by combining and modifying standard images downloaded from public repositories.

##  A little introduction to container and VM
**What is a container?** 
A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.
A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: *code, runtime, system tools, system libraries and settings.*
The file explorer is accessible using the button in left corner of the navigation bar. You can create a new file 
![enter image description here](https://www.docker.com/sites/default/files/d8/styles/large/public/2018-11/container-what-is-container.png?itok=vle7kjDj)
**Container Vs Virtual Machine** 
 Containers and virtual machines have similar resource isolation and allocation benefits, but function differently because containers virtualize the operating system instead of hardware. Containers are more portable and efficient.
   

Container         |  Virtual Machine
:-------------------------|:-------------------------
![enter image description here](https://www.docker.com/sites/default/files/d8/2018-11/docker-containerized-appliction-blue-border_2.png)  | ![enter image description here](https://www.docker.com/sites/default/files/d8/2018-11/container-vm-whatcontainer_2.png)
|Containers are an abstraction at the app layer that packages code and dependencies together. Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space. Containers take up less space than VMs , can handle more applications. | Virtual machines (VMs) are an abstraction of physical hardware turning one server into many servers. The hypervisor allows multiple VMs to run on a single machine. Each VM includes a full copy of an operating system, the application, necessary binaries and libraries - taking up tens of GBs. VMs can also be slow to boot.

## Installation of Docker 

### Installing Docker on Ubuntu


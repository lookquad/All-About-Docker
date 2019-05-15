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
You can install Docker CE in different ways, depending on your needs, the complete official instruntion on installing Docker on Ubuntu can be found at  [Docker, Inc.](https://docs.docker.com/v17.09/engine/installation/linux/docker-ce/ubuntu/) 

-   Most users set up Docker’s repositories and install from them, for ease of installation and upgrade tasks. This is the recommended approach.
    
-   Some users download the DEB package and install it manually and manage upgrades completely manually. This is useful in situations such as installing Docker on air-gapped systems with no access to the internet.
    
-   In testing and development environments, some users choose to use automated to install Docker.

I would prefer installing Docker from repository.
### Install using the repository

Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

#### Set up the repository

1.  Update the `apt` package index:
    
    ```
    $ sudo apt-get update
    
    ```
    
2.  Install packages to allow `apt` to use a repository over HTTPS:
    
    ```
    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common
    
    ```
    
3.  Add Docker’s official GPG key:
    
    ```
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    
    ```
    
    Verify that you now have the key with the fingerprint `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`, by searching for the last 8 characters of the fingerprint.
    
    ```
    $ sudo apt-key fingerprint 0EBFCD88
    
    pub   4096R/0EBFCD88 2017-02-22
          Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid                  Docker Release (CE deb) <docker@docker.com>
    sub   4096R/F273FCD8 2017-02-22
    
    ```
    
4.  Use the following command to set up the **stable** repository. You always need the **stable** repository, even if you want to install builds from the **edge** or **test** repositories as well. To add the **edge** or **test** repository, add the word `edge` or `test` (or both) after the word `stable` in the commands below.
    
    > **Note**: The `lsb_release -cs` sub-command below returns the name of your Ubuntu distribution, such as `xenial`. Sometimes, in a distribution like Linux Mint, you might have to change `$(lsb_release -cs)` to your parent Ubuntu distribution. For example, if you are using `Linux Mint Rafaela`, you could use `trusty`.
    
    -   x86_64 / amd64
    -   armhf
    -   IBM Power (ppc64le)
    -   IBM Z (s390x)
    
    ```
    $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
    
    ```
    
    > **Note**: Starting with Docker 17.06, stable releases are also pushed to the **edge** and **test** repositories.
    
    [Learn about **stable** and **edge** channels](https://docs.docker.com/v17.09/engine/installation/).
    

#### Install Docker CE

1.  Update the `apt` package index.
    
    ```
    $ sudo apt-get update
    
    ```
    
2.  Install the latest version of Docker CE, or go to the next step to install a specific version. Any existing installation of Docker is replaced.
    
    ```
    $ sudo apt-get install docker-ce
    
    ```
    
    > Got multiple Docker repositories?
    > 
    > If you have multiple Docker repositories enabled, installing or updating without specifying a version in the `apt-get install` or `apt-get update` command will always install the highest possible version, which may not be appropriate for your stability needs.
    
3.  On production systems, you should install a specific version of Docker CE instead of always using the latest. This output is truncated. List the available versions.
    
    ```
    $ apt-cache madison docker-ce
    
    docker-ce | 17.09.0~ce-0~ubuntu | https://download.docker.com/linux/ubuntu xenial/stable amd64 Packages
    
    ```
    
    The contents of the list depend upon which repositories are enabled. Choose a specific version to install. The second column is the version string. The third column is the repository name, which indicates which repository the package is from and by extension its stability level. To install a specific version, append the version string to the package name and separate them by an equals sign (`=`):
    
    ```
    $ sudo apt-get install docker-ce=<VERSION>
    
    ```
    
    The Docker daemon starts automatically.
    
4.  Verify that Docker CE is installed correctly by running the `hello-world` image.
    
    ```
    $ sudo docker run hello-world
    
    ```
    
    This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.
    

Docker CE is installed and running. The `docker` group is created but no users are added to it. You need to use `sudo` to run Docker commands. Continue to [Linux postinstall](https://docs.docker.com/v17.09/engine/installation/linux/linux-postinstall/) to allow non-privileged users to run Docker commands and for other optional configuration steps.

#### Use Play-With-Docker

If you don't want to install Docker, an alternative is to use [Play-With-Docker](http://play-with-docker.com/), which is a website where you can run terminals directly from your browser that have Docker installed.

##  Why containers are appealing to users?

 1. No more "Works on my machine"
 2. Light Weight and fast
 3. Better resource utilization
 4. can fit far more containers than VMs
 5. Ecosystem and tooling
 A lot more to do with container. Just start exploring it...

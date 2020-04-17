# What-s-Docker
Simple tutorial for the docker beginner.

# Basic knowledges

## First of all let we look at the image:

<img src="http://linux.vbird.org/linux_basic/0110whatislinux/os_01.gif" width="250" height="200"></img>

## Boot sequence 

<img src="https://arkit.co.in/wp-content/uploads/2016/07/Linux-boot-process.png" width="350" height="530"></img>

## Hypervisor

A hypervisor (or virtual machine monitor, VMM) is computer software, firmware or hardware that creates and runs virtual machines.

<img src="https://upload.wikimedia.org/wikipedia/commons/e/e1/Hyperviseur.png" width="450" height="300"></img>

# About the Docker
Docker is a set of platform as a service (PaaS) products that uses OS-level virtualization to deliver software in packages called containers.

Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels. All containers are run by a single operating system kernel and therefore use fewer resources than virtual machines.

(form Wiki)

## Container vs VM
A container runs natively on Linux and shares the kernel of the host machine with other containers. It runs a discrete process, taking no more memory than any other executable, making it lightweight.

By contrast, a virtual machine (VM) runs a full-blown “guest” operating system with virtual access to host resources through a hypervisor. 
In general, VMs incur a lot of overhead beyond what is being consumed by your application logic.

(form official)

<img src="https://docs.docker.com/images/Container%402x.png" width="250" height="200"></img>
<img src="https://docs.docker.com/images/VM%402x.png" width="250" height="200"></img>
## History
Docker used LXC as its default execution environment.

LXC(Linux Container) is a userspace interface for the Linux kernel containment features. Through a powerful API and simple tools, it lets Linux users easily create and manage system or application containers.

But now, Docker support more isolated tools on below:
- DOpenVZ
- systemd-nspawn
- libvirt-lxc
- libvirt-sandbox
- qemu/kvm
- BSD Jails
- Solaris Zones
- chroot

# Architecture
```
┌─Docker Host
│ └─Docker Engine API(SDK)
│   └─Docker Daemon
└─Docker Client
```
As the docker deamon running in the systemD, then the Docker client can be used by us.
<img src="https://www.netadmin.com.tw/upload/news/NP170703000317070311500702.png" width="550" height="250"></img>
# Operating
First of step:
``` shell
systemctl start docker.service;
```


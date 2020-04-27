# What-is-Docker
Simple tutorial for the docker beginner.

# Basic Knowledges About Operating Systems

## Simple Operating System concept image:

<img src="https://i.imgur.com/4jqThpA.png" width="570" height="400"></img>

## Boot sequence 

<img src="https://arkit.co.in/wp-content/uploads/2016/07/Linux-boot-process.png" width="350" height="530"></img>

## LVM
In Linux, Logical Volume Manager (LVM) is a device mapper target that provides logical volume management for the Linux kernel. Most modern Linux distributions are LVM-aware to the point of being able to have their root file systems on a logical volume.

(form Wiki)

<img src="https://pic.pimg.tw/mistech/1376019734-2561621321_b.png" width="350" height="250" ></img>

``` shell
#
fdisk -l
```

## System D
systemd is a software suite that provides an array of system components for Linux operating systems.

Its main aim is to unify service configuration and behavior across Linux distributions; systemd's primary component is a "system and service manager"—an init system used to bootstrap user space and manage user processes. It also provides replacements for various daemons and utilities, including device management, login management, network connection management, and event logging.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Linux_kernel_unified_hierarchy_cgroups_and_systemd.svg/1024px-Linux_kernel_unified_hierarchy_cgroups_and_systemd.svg.png" width="650" height="450"></img>

## cgroup

cgroups (control groups) is a Linux kernel feature that limits, accounts for, and isolates the resource usage (CPU, memory, disk I/O, network, etc.) of a collection of processes.

``` shell
#
mount -t cgroup


cd /sys/fs/cgroup/cpu
mkdir testlimit
ls testlimit/
cat /sys/fs/cgroup/cpu/testlimit/cpu.cfs_quota_us
cat /sys/fs/cgroup/cpu/testlimit/cpu.cfs_period_us
echo 30000 > /sys/fs/cgroup/cpu/testlimit/cpu.cfs_quota_us // cpu usage 30%
```

## Hypervisor

A hypervisor (or virtual machine monitor, VMM) is computer software, firmware or hardware that creates and runs virtual machines.

(form Wiki)

<img src="https://upload.wikimedia.org/wikipedia/commons/e/e1/Hyperviseur.png" width="450" height="300"></img>

# About Docker
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
### LXC
Docker used LXC as its default execution environment.

LXC(Linux Container) is a userspace interface for the Linux kernel containment features. Through a powerful API and simple tools, it lets Linux users easily create and manage system or application containers.

### libcontainer
### runC containerd


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
Docker Engine:
┌─Docker Daemon
│ └─Docker Server(Host)
│   └─Docker Engine API(SDK) -- Docker registries(Docker Hub)
└─Docker Client
```
As the docker deamon running in the systemD, then the Docker client can be used by us.

<img src="https://www.netadmin.com.tw/upload/news/NP170703000317070311500702.png" width="550" height="250"></img>

## UnionFS(aufs & devicemapper)



# Getting Started
## install
``` shell
$
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine;
                  
sudo yum install -y yum-utils;

sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo;
    
sudo yum install docker-ce docker-ce-cli containerd.io;
```
## take out sudo
``` shell
sudo groupadd docker;
sudo usermod -aG docker $USER;
```
reboot or relogin;
## Run
``` shell
$
sudo systemctl enable --now docker.service;

sudo sudo docker run hello-world
```


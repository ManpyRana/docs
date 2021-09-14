# Agenda
- [Agenda](#agenda)
  - [Virtualization](#virtualization)
  - [Containerization](#containerization)
  - [Docker Image & Docker Container](#docker-image--docker-container)
  - [Docker](#docker)
  - [Docker vs Virtual Machines](#docker-vs-virtual-machines)
  - [Why use Docker?](#why-use-docker)
  - [Docker Container Lifecycle Management:](#docker-container-lifecycle-management)
  - [Create, Run, Pause, Stop And Delete](#create-run-pause-stop-and-delete)

## Virtualization

Your code runs on a system.

In the past, we used to buy bare metals for each isolated code. Meaning if you want two servers you buy two servers.

so if a code requires only 1G RAM, but the server you have is 32GB you are wasting remaining 31GB of hardware resource.

To avoid this wastage the hardware virtualization concept came to use, now on the 32 GB server, you can create 32,1GB VMs.

But still another wastage was there, the code may not utilize 100% RAM or CPU all the time . More than 90% of the time only 30% of system resources will be in use.

To avoid this Docker containerization technology was introduced.

## Containerization

The containerization creates virtualization in OS level and share the hardware resource so you can use the unutilized system resource.

This ensures your organization can save a fortune by utilizing available resource to its max.

## Docker Image & Docker Container

An ‘image’ is basically the blueprint that lets you create containers.  
A ‘container’ is a running instance of an image.

## Docker
Docker is a containerization platform for developing, shipping, and running applications inside containers. We can deploy many containers simultaneously on a given host. Containers are very fast and boot up quickly because they don’t need the extra load of a hypervisor in comparison to the virtual machines because they run directly within the host machine’s kernel.

## Docker vs Virtual Machines
| Docker | VMs |  
| --- | --- |
| Apartments | Houses|
| Share existing infrastucture | Has its own infrastructure |
| Speedy!  Can spun up in seconds| take minutes to boot |
|They don't need there own CPU, PAM or CPU. Shares the resources of the host OS| Heavier! consumes lots of RAM & CPU cycles |

## Why use Docker?

You will not just ensure the quality of the system but also ensures you save your organization some money by ensuring system resources are not wasted.  

There are a number of uses of Docker from QA perspective in any qa company. Few of them are listed below:

It runs faster in comparison to Jenkins or any other tool as the deployments are done in containers. Due to this, you can deploy the identical containers in different portions at the same time which makes it very quick.  
It’s quite easy to place frameworks, libraries, artifact versions and all project dependencies in a single container.
If an issue is encountered, you can share their images (here: image is the application, potentially even at the moment in time when a test failed) instead of bug reports. so, that makes it easy to reproduce.  
It can be used to catch the system-level bugs and evaluate their root cause as using docker containers the process is easier, because the system configurations are based on the image that was used during deployment.

It checks all the boxes:

* Environments on demand  
* Greater consistency across many users  
* More reproducible and thus reliable environments  
* Greater security options when implemented correctly  
* Less 'it works on this machine but not that one' issues  
* Less cost due to more virtualization and less physical machines to maintain  
* Faster turnaround for changes when they are made to a master image and then distributed

## Docker Container Lifecycle Management:   
## Create, Run, Pause, Stop And Delete
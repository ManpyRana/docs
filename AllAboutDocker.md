# Agenda
- [Agenda](#agenda)
  - [Virtualization](#virtualization)
  - [Containerization](#containerization)
  - [Docker Image & Docker Container](#docker-image--docker-container)
  - [Docker](#docker)
  - [Docker vs Virtual Machines](#docker-vs-virtual-machines)
  - [Why use Docker?](#why-use-docker)
    - [Open Source Containerisation - Build, Package , Run](#open-source-containerisation---build-package--run)
    - [It Works on my machine tool, Hurrey...!!](#it-works-on-my-machine-tool-hurrey)
  - [Docker Container Lifecycle Management:](#docker-container-lifecycle-management)
    - [Create, Run, Pause, Stop And Delete](#create-run-pause-stop-and-delete)
  - [Docker Commands](#docker-commands)
  - [Docker Selenium Grid(Hub and Nodes)](#docker-selenium-gridhub-and-nodes)
  - [Port Binding](#port-binding)
  - [Bind Mount & Docker Volumes](#bind-mount--docker-volumes)
  - [Docker Network](#docker-network)

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
### Open Source Containerisation - Build, Package , Run 


You will not just ensure the quality of the system but also ensures you save your organization some money by ensuring system resources are not wasted.  

There are a number of uses of Docker from QA perspective in any qa company. Few of them are listed below:

It runs faster in comparison to Jenkins or any other tool as the deployments are done in containers. Due to this, you can deploy the identical containers in different portions at the same time which makes it very quick.  
It’s quite easy to place frameworks, libraries, artifact versions and all project dependencies in a single container.
If an issue is encountered, you can share their images (here: image is the application, potentially even at the moment in time when a test failed) instead of bug reports. so, that makes it easy to reproduce.  
It can be used to catch the system-level bugs and evaluate their root cause as using docker containers the process is easier, because the system configurations are based on the image that was used during deployment.
### It Works on my machine tool, Hurrey...!!
It checks all the boxes:

* Environments on demand  
* Greater consistency across many users  
* More reproducible and thus reliable environments  
* Greater security options when implemented correctly  
* Less 'it works on this machine but not that one' issues  
* Less cost due to more virtualization and less physical machines to maintain  
* Quick turnaround for distributed and parallel testing
* Faster turnaround for changes when they are made to a master image and then distributed

## Docker Container Lifecycle Management:   
### Create, Run, Pause, Stop And Delete

## Docker Commands
| Basic | Images | Containers | System |  
|---|---|---|---|
|version | images | ps | stats|
|-v | pull | run | system df|
| info | rmi | start | system prune -f|
|--help| | stop||
|login||rm||
|logout||rename||

example : 

1. To remove the stopped containers forcefully :  
   `docker system prune -f`  

2. To create container based on image :  
   `docker run -it <image>`

3. To know running containers :  
   `docker ps`

4. To pull image :  
   `docker pull <image_from_dockerhub>`  

5. To stop and remove container :  
   `docker stop <container ID>`  
   `docker rm <container ID>`  
   OR  
   `docker rm -f $(docker ps -a -q)`  

6. To rename a container :  
   `docker rename <container-name> <new-name> `

7. You can assign memorable names to your docker containers when you run them, using the --name flag as follows. The -d flag tells docker to run a container in detached mode, in the background and print the new container ID.
   `docker run -d --name <memorable-name> <image-name>`
## Docker Selenium Grid(Hub and Nodes)
https://github.com/SeleniumHQ/docker-selenium

download *docker-compose.yml* file from the above official link and open cmd from the same location the file is put in.
To start the grid :  
`docker-compose up`  
To stop the grid :  
`docker-compose down`
To scale up:
`docker-compose up -d --scale <service>=<number>`  
Example:  
`docker-compose up -d --sacle chrome=4`
Selenium script for remote connection for Docker Selenium Grid:  
```
  DesiredCapabilities dc= DesiredCapabilities.chrome();  
  URL url= new URL(" http://localhost:4444/wd/hub");  
  RemoteWebDriver driver= new RemoteWebDriver(url,dc);
```
Steps :

1. Invoke Selenium Grid Server in Docker environment using Batch file.
2. Run Batch file using Java Code.  
   To start :  
   ```
   Runtime.getRuntime().exec("cmd /c start start_dockergrid.bat");
   ```  
   To stop :  
   ```
   Runtime.getRuntime().exec("cmd /c start stop_dockergrid.bat");
   Thread.sleep(5000);  
   Runtime.getRuntime().exec("taskkill /f /im cmd.exe"); // closes command prompt
    ```
3. Run tests using Maven *pom.xml* by adding below plugins :  
   **maven-compiler-plugin**  
   **maven-surefire-plugin**
4. Integrate Docker Selenium Grid with Jenkins.  
You can download *.war* Generic Java Package for jenkins from official site and run the command in cmd : ` java -jar jenkins.war`  
You can manually put the source code in *.jenkins* folder or can use version control for source code management. Run the project by using *mvn clean install* command.

## Port Binding
Syntax: `docker run -p <Docker-host-Port:container-Port> <image-name>`
By default, when you create or run a container using docker create or docker run, it does not publish any of its ports to the outside world.  
To make a port available to services outside of Docker, or to Docker containers which are not connected to the container’s network, use the --publish or -p flag. This creates a firewall rule which maps a container port to a port on the Docker host to the outside world. 

Example:  
Map TCP port 80 in the container to port 8080 on the Docker host.  
`-p 8080:80`

## Bind Mount & Docker Volumes
By default all files created inside a container are stored on a writable container layer. This means that the data doesn’t persist when that container no longer exists, and it can be difficult to get the data out of the container if another process needs it.

Docker has two options for containers to store files in the host machine, so that the files are persisted even after the container stops: volumes, and bind mounts. 


**Bind mounts** may be stored anywhere on the host system. They may even be important system files or directories. Non-Docker processes on the Docker host or a Docker container can modify them at any time.

`docker run -v <Local-Storage-absolute-path>:<Container-Storage> <image-name>`  
To check is mount is done properly, inspect the image and look for mounts. You can also copy environment paths-data by this command.   
`docker inspect <image-name>`  
Interact with the container using:  
`docker exec -it -user 0 <container-id> sh`  




**Volumes** are stored in a part of the host filesystem which is managed by Docker (/var/lib/docker/volumes/ on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker.  
Volumes are stored in the Linux VM rather than the host, which means that the reads and writes have much lower latency and higher throughput.
Docker Volume Commands:  
1. `docker volume create <volume-name>`
2. `docker colume prune` //it removes all unused local volume
3. `docker volume inspect <volume-name>`
4. `docker volume ls`
5. `docker volume rm <volume-name>`

`docker run -v <Docker-Volume>:<Container-storage> <image-name>`

## Docker Network
 Docker containers and services are so powerful that you can connect them together, or connect them to non-Docker workloads. Docker’s networking subsystem is pluggable, using drivers:
 1. Bridge  
It is the default network driver. You can also create user-defined bridge network. **User-defined bridge networks** are best when you need multiple containers to communicate on the same Docker host

 2. Host  
 To uses the host's networking directly and removes network isolation between the container and the Docker host, 
 3. None  
 It run in full isolated mode with no Port and IP address. It is useful when running any batch jobs.

 Docker Network Commands:  
 * `docker network ls`
 * `docker network create <network-name>`
 * `docker network inspect <network-name>`
 * `docker network rm <network-name>`
 * `docker network connect/disconnect <network-name>`
 * `docker network prune`
 * `docker run --network=<driver-name> <image-id>`

 User-Defined Bridge network advantages over default bridge network:  
 |Default Bridge Network|User-defined bridge network|
 |---|---|
 |can only be accessed(ping) via IP address| can be accessed by IP address and name|
 |Risky. Any unrealted container can talk| Scoped. Only attached containers can talk|
 |To detach, need to stop container first| Easy to attach and detach| 

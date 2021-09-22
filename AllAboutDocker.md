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




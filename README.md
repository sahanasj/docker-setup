# DOCKER concepts
Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization.

A container is a runtime instance of an image. With DOCKER, you can treat containers like extremely lightweight, modular virtual machines. And you get flexibility with those containers—you can create, deploy, copy, and move them from environment to environment, which helps optimize your apps for the cloud.
(A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.)

<details>
<summary>Docker Notes</summary>
 <br>
Containerization is increasingly popular because containers are:

* Flexible: Even the most complex applications can be containerized. <br>
* Lightweight: Containers leverage and share the host kernel. <br>
* Interchangeable: You can deploy updates and upgrades on-the-fly. <br>
* Portable: You can build locally, deploy to the cloud, and run anywhere. <br>
* Scalable: You can increase and automatically distribute container replicas. <br>
* Stackable: You can stack services vertically and on-the-fly.<br>

<b> How does Docker work? </b><br>
The Docker technology uses the Linux kernel and features of the kernel, like Cgroups and namespaces, to segregate processes so they can run independently.

1.	**Docker Machine** - Create Docker hosts on your computer, on cloud providers, and inside your own data center
2.	**Docker Compose** - A tool for defining and running multi-container Docker applications.
3.	**Docker Swarm** - A native clustering solution for Docker
4.	**Kubernetes** - Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.

<b>Containers and virtual machines</b>
<br>
* A container runs natively on Linux and shares the kernel of the host machine with other containers. It runs a discrete process, taking no more memory than any other executable, making it lightweight.
* A virtual machine (VM) runs a full-blown “guest” operating system with virtual access to host resources through a hypervisor.

 <img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/containers-vs-vms.PNG" width="650">
</details>

# Getting started - Hands on Experience with Dockers (Cloud based Lab Environment to play with Dockers)
<details>
<summary>Usage</summary>
  <br>
https://labs.play-with-docker.com/
  <br>

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-play.PNG" width="650">

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-play-2.PNG" width="650">

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-hub-3.PNG" width="650">

<br>

* Docker Hub Account * – Hub is a repository with all the images with  applications, resources of Docker.
It is just simple as like Git as such, Connect to Repo and pull the docker image and then launch Application.
<br>https://hub.docker.com/<br>

Login:
<br>
<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-hub.PNG" width="650">
<br>
Click on “Explore”:
<br>
<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-hub-2.PNG" width="650">
<br>
List of all Docker Images, Application etc..:
<br>
<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-hub-3.PNG" width="650">
<br>
</details>

# Getting Started with Docker-setup
<details>
 Installation of Docker on Ubuntu 18.04 and Use Docker<br>
<br>
<summary>Prerequisites</summary>
One Ubuntu 18.04 server set up with a non-root user with sudo privileges and a basic firewall configuration
  <br>
  <b>Install Required Packages</b>
  <br>
  Before installing Docker, you must make sure Ubuntu is ready!
  <br>
  $ sudo apt update
</details>
<br>

<details>
<summary>Quick Docker Install on Ubuntu 18.04</summary>
  <h5> Step 1 — Installing Docker </h5>
The Docker installation package available in the official Ubuntu 18.04 repository may not be the latest version. To get this latest version, install Docker from the official Docker repository. This section shows you how to do just that.
First, in order to ensure the downloads are valid, add the GPG key for the official Docker repository to your system:
  <br>

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
<br>

To use add-apt-repository or apt-add-repository commands to add PPA
<br>

$ sudo apt-get install software-properties-common
<br>

Add the Docker repository to APT sources 
<br>
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

<br>
Next, update the package database with the Docker packages from the newly added repo:
<br>
$ sudo apt-get update

<br>
<br>
Make sure you are about to install from the Docker repo instead of the default Ubuntu 18.04 repo:
<br>
$ apt-cache policy docker-ce

<br>
<br>
You should see output similar to the follow:

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/1.PNG" width="950">

<!-- ![alt text](https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/1.PNG) -->

<b>Note</b>: Notice that docker-ce is not installed, but the candidate for installation is from the Docker repository for Ubuntu 16.04 (xenial).

<br>
Finally, install Docker:
<br>
$ sudo apt-get install -y docker-ce

<br>
<br>
Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it's running:
<br>
$	sudo systemctl status docker

<br>
<br>
The output should be similar to the following, showing that the service is active and running:

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/2.PNG" width="950">

<br>
Installing Docker now gives you not just the Docker service (daemon) but also the docker command line utility, or the Docker client.
<br>

<h5> Step 2 — Executing the Docker Command Without Sudo (Optional) </h5>
If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:
<br>
$	sudo usermod -aG docker ${USER}

<br>
<br>
To apply the new group membership, you can log out of the server and back in, or you can type the following:
<br>
$	su - ${USER}

<br>
<br>
You will be prompted to enter your user's password to continue. Afterwards, you can confirm that your user is now added to the docker group by typing:
<br>
$	id -nG

<br>
<br>
If you need to add a user to the docker group that you're not logged in as, declare that username explicitly using:
<br>
$	sudo usermod -aG docker username

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/3.PNG" width="950">

<h5> Step 3 — Using the Docker Command </h5>
With Docker installed and working, now's the time to become familiar with the command line utility. Using docker consists of passing it a chain of options and commands followed by arguments. The syntax takes this form:
<br>
$	docker [option] [command] [arguments]

<br>
<br>
To view all available subcommands, type:
<br>
$	docker

<br>
<br>
To view system-wide information about Docker, use:
<br>
$	docker info

<h5> Step 4 — Working with Docker Images </h5>
Docker containers are run from Docker images. By default, it pulls these images from Docker Hub, a Docker registry managed by Docker

<br>
<br>
To check whether you can access and download images from Docker Hub, type:
<br>
$	docker run hello-world

<br>
<br>
In the output, you should see the following message, which indicates that Docker is working correctly:

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/4.PNG" width="950">

<br>
You can search for images available on Docker Hub by using the docker command with the search subcommand. For example, to search for the Ubuntu image, type:
<br>
$	docker search ubuntu
<br>

<img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/5.PNG" width="950">

The script will crawl Docker Hub and return a listing of all images whose name matches the search string. In this case, the output will be similar to this:
</details>
<br>

<details>
<summary>Install Docker Compose</summary>
Docker Compose relies on Docker Engine for any meaningful work, so make sure you have Docker Engine installed either locally or remote, depending on your setup.
  
 # Install Compose on Linux systems (using Curl)
 
 1. Run this command to download the latest version of Docker Compose: <br>
 $ sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
 
<b>Note:</b> check the Compose repository release page on GitHub for latest versions.
 https://github.com/docker/compose/releases
 
 2. Apply executable permissions to the binary:  <br>
 $ sudo chmod +x /usr/local/bin/docker-compose
 
 3. Test the installation.  <br>
 $ docker-compose --version
 
 Output:
 
 <img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-compose.PNG" width="1050"> 
 
 4. To bring up both the container, run
 $ docker-compose up
 
 Note: When run at first time, It takes some time to finish the installation with all dependencies. <br>
 To run docker-compose in detached mode, use -d option. However you may want to use non-detached mode to see output messages. <br>
 To stop all containers started in docker-compose.yml, press CTRL+C if it is running in foreground, or you can run
 
 To stop all containers started in docker-compose.yml, press CTRL+C if it is running in foreground, or you can run
 $ docker-compose down
 
 Note: Usefull command to see container we have just created "$ docker container ls --all"
 
 <img src="https://github.com/sahanasj/docker-setup/blob/master/Docker-Installation-Images/docker-container-list.PNG" width="950">
 
 # Uninstallation
 
 To uninstall Docker Compose if you installed using curl: <br>
 $ sudo rm /usr/local/bin/docker-compose
 <br>
  
 To uninstall Docker Compose if you installed using pip:  <br>
 $ pip uninstall docker-compose
  <br>
 
</details>

<br>
<details>
<summary>Quick Docker cheatsheet</summary>

<b>Using Systemctl: to start and stop docker services</b>

$ sudo systemctl status docker
<br>
$ sudo systemctl stop docker
<br>
$ sudo systemctl start docker
<br>
$ sudo systemctl daemon-reload
<br>

[Or] 

$ sudo service docker status
<br>
$ sudo service docker stop
<br>
$ sudo service docker start
<br>

<b>Uninstall old versions</b>
<br>
Older versions of Docker were called docker or docker-engine. If these are installed, uninstall them:
<br>
$ sudo apt-get remove docker docker-engine docker.io

<b>Uninstall Docker CE</b>
<br>
Uninstall the Docker CE package:
<br>
$ sudo apt-get purge docker-ce
<br>

Images, containers, volumes, or customized configuration files on your host are not automatically removed. To delete all images, containers, and volumes:
<br>
$ sudo rm -rf /var/lib/docker
<br>
<b>Note:</b> You must delete any edited configuration files manually.

<b>List Docker CLI commands</b>
<br>
$ docker
<br>
$ docker container --help

<b> Display Docker version and info</b>
<br>
$ docker --version
<br>
$ docker version
<br>
$ docker info

<b>Execute Docker image</b>
<br>
$ docker run hello-world

<b>List Docker images</b>
<br>
$ docker image ls

<b>List Docker containers (running, all, all in quiet mode)</b>
<br>
$ docker container ls
<br>
$ docker container ls --all
<br>
$ docker container ls -aq
<br>
$ docker container ls -a
<br>
<br>
<b>Gracefully stop the specified container</b>
<br>
$ docker container stop <hash> 
<br>
<b>Force shutdown of the specified container</b>
<br>
$ docker container kill <hash> 
<br>
<b>Remove specified container</b>
<br>
$ docker container rm <hash>
  <br>
<b>Remove all containers</b>
<br>
$ docker container ls -a -q
<br>
<b>Remove specified image</b>
<br>
$ docker image rm <image id>
<br>
<b>Remove all images</b>
<br>
$ docker image ls -a -q
<br>
 <b>Create a container from ubuntu image</b> <br>
 $ docker run -name my-ubuntu -it ubuntu bash <br>
 The above command will create a docker container from base ubuntu image, name it my-ubuntu, run bash command (open bash shell) and keep standard input open (-i) and text input console open (-t, together -it). It will open a bash shell in the container, where you can execute any command.
 <br>
 
 <b>Create an image from Dockerfile</b> <br>
 $ docker build -t image_name . <br>
 <br>
 
 $ docker ps -a <br>
 ps command shows lot of information. However you can filter and format the output. Format should be a Go template string. For example to see only names of  container use following command –
 <br>
 $ docker ps --format "{{.Names}}"
 <br>
 
 <b>Start Container</b>
 <br>
 $ docker start <container>
 <br>
 $ docker start -i <container>
 <br>
 use stop command to stop the container
  $ docker stop -i <container>
 <br>
 To remove a container , use rm command (you can specify multiple containers names) –
 <br>
 $ docker rm <container-1> <container-2>
 <br>
 If you want to remove running container, use -f option
 <br>
 $ docker rm -f <container>
 <br>
create a container in detached mode.
 <br>
 $ docker run -d -it --name <container> ubuntu
 <br>
 -d option runs docker container in background (detached mode). You will immediately return to command prompt after executing the above command.
 <br>
 To attach to the  the above container and the process that started it (in this case /bin/bash) –
 <br>
 $ docker attach <container>
 <br>
 This will allow you to execute commands in bash shell that was started in the container when container was run.
<br>

If you do not want to terminate the container upon existing the bash shell, you can use exec command.
<br>
$ docker exec -it <container> bash
<br>
This will open a new bash shell. Exiting that shell will not terminate the container because it was not the command that started the container.
<br>
<b>Deleting Image</b>
To remove images, use rmi command. Note that there should be no container based on the images you want to delete. If there are containers using images to be deleted, then remove those containers first using rm command mentioned above.
<br>
$ docker rmi my-image1 my-image2
<br>
Instead of names you can also use image ids.
<br>
<p>Stop and remove all docker containers and images</p>
<b>List all containers (only IDs)</b> <br>
$docker ps -aq <br>

<b>Stop all running containers</b> <br>
$ docker stop $(docker ps -aq) <br>

<b>Remove all containers</b> <br>
$docker rm $(docker ps -aq) <br>

<b>Remove all images</b> <br>
$ docker rmi $(docker images -q) <br>

<b>Remove all containers</b>, so be careful <br>
$ docker rm $(docker ps -a -q)
<br>
-q option tells ps command to return only ids, which are then fed to rm command.
docker ps list containers <br>
-a the option to list all containers, even stopped ones. Without this, it defaults to only listing running containers
<br>

Here is an example of using filters to remove containers (this example removes all containers starting with my-ubuntu)
<br>
$ docker rm $(docker ps --filter name=my-ubuntu* -q)
<br>

<b>Delete all Images</b>
Following command deletes all images, so again be careful –
<br>
$ docker rmi $(docker images -q)
<br>

<b>To delete by filtering on image name –</b>
<br>
$ docker rmi ($docker images *my-ubuntu*)
<br>

<b>Mapping folder from host to container</b>
To share folder from the host to a container, use the same -v option, but specify <host-folder-name>:<path-in-container> argument. 
<br>
$ docker run --rm -it -v ${PWD}:/src ubuntu
<br>
${PWD} tells docker to map present working directory.

<br>
<b>Using volumes for backup and restore</b>
Backing up data from one container and restoring it in another.
<br>
$ docker inspect my-db
<br>

$ docker run --rm --volumes-from my-db -v ${pwd}/backup-data:/backup-data ubuntu tar cvf /backup-data/my-db-volume.tar /var/lib/mysql
<br>
We are using –rm because we want to create a temporary container. The container will be terminated after the command is finished.
<br>

<b>To restore the data –</b>
<br>
$ docker run --rm --volumes-from my-new-db -v $(pwd)/data-backup:/backup-data ubuntu bash -c "cd / && tar xvf /backup-data/my-db-data.tar"
<br>
Here we are restoring the data into newly created my-new-db container (created with mysql base image). We are using volumes from the new db container, so /var/lib/mysql folder is available to the temporary container. 

<br>

<b>Creating image from container</b>
<br>
create a container from some base image
<br>
$ docker export -o /my-images/container1-image.tar container1
<br>
Specify output file path using -o option. The last argument is name of the container from which you want to create an image.
<br>
To create image from the exported file, use import command –
<br>
$ docker import /my-images/container1-image.tar container1-image
<br>
The above command will create image named container1-image from container1-image.tar file.
<br>
<b>Log in to CLI session using your Docker credentials</b>
<br>
$ docker login
<br>
 <b>Tag <image> for upload to registry</b>
  <br>
  $ docker tag <image> username/repository:tag
  <br>
  <b>Upload tagged image to registry</b>
  <br>
  $ docker push username/repository:tag
  <br>
  <b>Run image from a registry</b>
  <br>
  $ docker run username/repository:tag
  <br>
   
<h5> Services and Stacks Commands </h5>
<b>List stacks or apps</b>
<br>
$ docker stack ls 
<br>
<b>Run the specified Compose file</b>
<br>
$ docker stack deploy -c <composefile> <appname>
<br>
<b>List running services associated with an app</b>
<br>
$ docker service ls 
<br>
<b>List tasks associated with an app</b>
<br>
$ docker service ps <service>
<br>
<b>Inspect task or container</b>
<br>
$ docker inspect <task or container>
<br>
<b>List container IDs</b>
<br>
$ docker container ls -q 
<br>
<b>Tear down an application</b>
<br>
$ docker stack rm <appname>
<br>
<b>Take down a single node swarm from the manager</b>
<br>
$ docker swarm leave --force
<br>
  
<h5> Docker Swarms commands </h5>

<b>Create a VM (Mac, Win7, Linux)</b>
<br>
$ docker-machine create --driver virtualbox myvm1
<br>
<b>Create a VM - Win10</b>
<br>
$ docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1
<br>
<b>View basic information about your node</b>
<br>
$ docker-machine env myvm1  
<br>
<b>List the nodes in your swarm</b>
<br>
$ docker-machine ssh myvm1 "docker node ls"
<br>
<b>Inspect a node</b>
<br>
$ docker-machine ssh myvm1 "docker node inspect <node ID>"
<br>
<b>View join token</b>
<br>
$ docker-machine ssh myvm1 "docker swarm join-token -q worker"
<br>
<b>Open an SSH session with the VM; type "exit" to end</b>
<br>
$ docker-machine ssh myvm1
<br>
<b>View nodes in swarm (while logged on to manager)</b>
<br>
$ docker node ls
<br>
<b>Make the worker leave the swarm</b>
<br>
$ docker-machine ssh myvm2 "docker swarm leave"
<br>
<b>Make master leave, kill swarm</b>
<br>
$ docker-machine ssh myvm1 "docker swarm leave -f"
<br>
<b>list VMs, asterisk shows which VM this shell is talking to</b>
<br>
$ docker-machine ls
<br>
<b>Start a VM that is currently not running</b>
<br>
$ docker-machine start myvm1
<br>
<b>show environment variables and command for myvm1</b>
<br>
$ docker-machine env myvm1
<br>
<b>Deploy an app; command shell must be set to talk to manager (myvm1), uses local Compose file</b>
<br>
$ docker stack deploy -c <file> <app>
<br>
<b>Copy file to node's home dir (only required if you use ssh to connect to manager and deploy the app)</b>
<br>
$ docker-machine scp docker-compose.yml myvm1:~
<br>
<b>Deploy an app using ssh (you must have first copied the Compose file to myvm1)</b>
<br>
$ docker-machine ssh myvm1 "docker stack deploy -c <file> <app>"
<br>
<b>Disconnect shell from VMs, use native docker</b>
<br>
$ eval $(docker-machine env -u)
<br>
<b>Stop all running VMs</b>
<br>
$ docker-machine stop $(docker-machine ls -q)
<br>
<b>Delete all VMs and their disk images</b>
<br>
$ docker-machine rm $(docker-machine ls -q)
<br>
 <b>Useful information</b>
 <br>
 
* [`docker create`](https://docs.docker.com/engine/reference/commandline/create) creates a container but does not start it.
* [`docker rename`](https://docs.docker.com/engine/reference/commandline/rename/) allows the container to be renamed.
* [`docker run`](https://docs.docker.com/engine/reference/commandline/run) creates and starts a container in one operation.
* [`docker rm`](https://docs.docker.com/engine/reference/commandline/rm) deletes a container.
* [`docker update`](https://docs.docker.com/engine/reference/commandline/update/) updates a container's resource limits.

### Starting and Stopping

* [`docker start`](https://docs.docker.com/engine/reference/commandline/start) starts a container so it is running.
* [`docker stop`](https://docs.docker.com/engine/reference/commandline/stop) stops a running container.
* [`docker restart`](https://docs.docker.com/engine/reference/commandline/restart) stops and starts a container.
* [`docker pause`](https://docs.docker.com/engine/reference/commandline/pause/) pauses a running container, "freezing" it in place.
* [`docker unpause`](https://docs.docker.com/engine/reference/commandline/unpause/) will unpause a running container.
* [`docker wait`](https://docs.docker.com/engine/reference/commandline/wait) blocks until running container stops.
* [`docker kill`](https://docs.docker.com/engine/reference/commandline/kill) sends a SIGKILL to a running container.
* [`docker attach`](https://docs.docker.com/engine/reference/commandline/attach) will connect to a running container.
 
 ### Info

* [`docker ps`](https://docs.docker.com/engine/reference/commandline/ps) shows running containers.
* [`docker logs`](https://docs.docker.com/engine/reference/commandline/logs) gets logs from container.  (You can use a custom log driver, but logs is only available for `json-file` and `journald` in 1.10).
* [`docker inspect`](https://docs.docker.com/engine/reference/commandline/inspect) looks at all the info on a container (including IP address).
* [`docker events`](https://docs.docker.com/engine/reference/commandline/events) gets events from container.
* [`docker port`](https://docs.docker.com/engine/reference/commandline/port) shows public facing port of container.
* [`docker top`](https://docs.docker.com/engine/reference/commandline/top) shows running processes in container.
* [`docker stats`](https://docs.docker.com/engine/reference/commandline/stats) shows containers' resource usage statistics.
* [`docker diff`](https://docs.docker.com/engine/reference/commandline/diff) shows changed files in the container's FS.

## Networks

Docker has a [networks](https://docs.docker.com/engine/userguide/networking/) feature. Not much is known about it, so this is a good place to expand the cheat sheet. There is a note saying that it's a good way to configure docker containers to talk to each other without using ports. See [working with networks](https://docs.docker.com/engine/userguide/networking/work-with-networks/) for more details.

### Lifecycle

* [`docker network create`](https://docs.docker.com/engine/reference/commandline/network_create/)
* [`docker network rm`](https://docs.docker.com/engine/reference/commandline/network_rm/)

### Info

* [`docker network ls`](https://docs.docker.com/engine/reference/commandline/network_ls/)
* [`docker network inspect`](https://docs.docker.com/engine/reference/commandline/network_inspect/)

### Connection

* [`docker network connect`](https://docs.docker.com/engine/reference/commandline/network_connect/)
* [`docker network disconnect`](https://docs.docker.com/engine/reference/commandline/network_disconnect/)

You can specify a [specific IP address for a container](https://blog.jessfraz.com/post/ips-for-all-the-things/):

```
# create a new bridge network with your subnet and gateway for your ip block
docker network create --subnet 203.0.113.0/24 --gateway 203.0.113.254 iptastic

# run a nginx container with a specific ip in that block
$ docker run --rm -it --net iptastic --ip 203.0.113.2 nginx

# curl the ip from any other place (assuming this is a public ip block duh)
$ curl 203.0.113.2
```

## Images

Images are just [templates for docker containers](https://docs.docker.com/engine/understanding-docker/#how-does-a-docker-image-work).

### Lifecycle

* [`docker images`](https://docs.docker.com/engine/reference/commandline/images) shows all images.
* [`docker import`](https://docs.docker.com/engine/reference/commandline/import) creates an image from a tarball.
* [`docker build`](https://docs.docker.com/engine/reference/commandline/build) creates image from Dockerfile.
* [`docker commit`](https://docs.docker.com/engine/reference/commandline/commit) creates image from a container, pausing it temporarily if it is running.
* [`docker rmi`](https://docs.docker.com/engine/reference/commandline/rmi) removes an image.
* [`docker load`](https://docs.docker.com/engine/reference/commandline/load) loads an image from a tar archive as STDIN, including images and tags (as of 0.7).
* [`docker save`](https://docs.docker.com/engine/reference/commandline/save) saves an image to a tar archive stream to STDOUT with all parent layers, tags & versions (as of 0.7).

### Info

* [`docker history`](https://docs.docker.com/engine/reference/commandline/history) shows history of image.
* [`docker tag`](https://docs.docker.com/engine/reference/commandline/tag) tags an image to a name (local or registry).
 
 ## Registry & Repository

A repository is a *hosted* collection of tagged images that together create the file system for a container.

A registry is a *host* -- a server that stores repositories and provides an HTTP API for [managing the uploading and downloading of repositories](https://docs.docker.com/engine/tutorials/dockerrepos/).

Docker.com hosts its own [index](https://hub.docker.com/) to a central registry which contains a large number of repositories.  Having said that, the central docker registry [does not do a good job of verifying images](https://titanous.com/posts/docker-insecurity) and should be avoided if you're worried about security.

* [`docker login`](https://docs.docker.com/engine/reference/commandline/login) to login to a registry.
* [`docker logout`](https://docs.docker.com/engine/reference/commandline/logout) to logout from a registry.
* [`docker search`](https://docs.docker.com/engine/reference/commandline/search) searches registry for image.
* [`docker pull`](https://docs.docker.com/engine/reference/commandline/pull) pulls an image from registry to local machine.
* [`docker push`](https://docs.docker.com/engine/reference/commandline/push) pushes an image to the registry from local machine.
 
 
 ## Dockerfile

[The configuration file](https://docs.docker.com/engine/reference/builder/). Sets up a Docker container when you run `docker build` on it. Vastly preferable to `docker commit`.  

Here are some common text editors and their syntax highlighting modules you could use to create Dockerfiles:
* If you use [jEdit](http://jedit.org), I've put up a syntax highlighting module for [Dockerfile](https://github.com/wsargent/jedit-docker-mode) you can use.
* [Sublime Text 2](https://packagecontrol.io/packages/Dockerfile%20Syntax%20Highlighting)
* [Atom](https://atom.io/packages/language-docker)
* [Vim](https://github.com/ekalinin/Dockerfile.vim)
* [Emacs](https://github.com/spotify/dockerfile-mode)
* [TextMate](https://github.com/docker/docker/tree/master/contrib/syntax/textmate)
* [VS Code](https://github.com/Microsoft/vscode-docker)
* Also see [Docker meets the IDE](https://domeide.github.io/)

### Instructions

* [.dockerignore](https://docs.docker.com/engine/reference/builder/#dockerignore-file)
* [FROM](https://docs.docker.com/engine/reference/builder/#from) Sets the Base Image for subsequent instructions.
* [MAINTAINER (deprecated - use LABEL instead)](https://docs.docker.com/engine/reference/builder/#maintainer-deprecated) Set the Author field of the generated images.
* [RUN](https://docs.docker.com/engine/reference/builder/#run) execute any commands in a new layer on top of the current image and commit the results.
* [CMD](https://docs.docker.com/engine/reference/builder/#cmd) provide defaults for an executing container.
* [EXPOSE](https://docs.docker.com/engine/reference/builder/#expose) informs Docker that the container listens on the specified network ports at runtime.  NOTE: does not actually make ports accessible.
* [ENV](https://docs.docker.com/engine/reference/builder/#env) sets environment variable.
* [ADD](https://docs.docker.com/engine/reference/builder/#add) copies new files, directories or remote file to container.  Invalidates caches. Avoid `ADD` and use `COPY` instead.
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) copies new files or directories to container.  Note that this only copies as root, so you have to chown manually regardless of your USER / WORKDIR setting.  See https://github.com/moby/moby/issues/30110
* [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) configures a container that will run as an executable.
* [VOLUME](https://docs.docker.com/engine/reference/builder/#volume) creates a mount point for externally mounted volumes or other containers.
* [USER](https://docs.docker.com/engine/reference/builder/#user) sets the user name for following RUN / CMD / ENTRYPOINT commands.
* [WORKDIR](https://docs.docker.com/engine/reference/builder/#workdir) sets the working directory.
* [ARG](https://docs.docker.com/engine/reference/builder/#arg) defines a build-time variable.
* [ONBUILD](https://docs.docker.com/engine/reference/builder/#onbuild) adds a trigger instruction when the image is used as the base for another build.
* [STOPSIGNAL](https://docs.docker.com/engine/reference/builder/#stopsignal) sets the system call signal that will be sent to the container to exit.
* [LABEL](https://docs.docker.com/engine/userguide/labels-custom-metadata/) apply key/value metadata to your images, containers, or daemons.
<br>


</details>

# Important Resources
[What is DOCKER](https://www.redhat.com/en/topics/containers/what-is-docker)<br>
https://www.infoworld.com/article/3204171/docker/what-is-docker-docker-containers-explained.html <br>
[How to install Docker on Ubuntu 16.04 and 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04/)<br>
[Docker installation video](https://www.youtube.com/watch?v=hY34PpllKf4)<br>
[Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)<br>
[Docker Cheatsheet](https://github.com/wsargent/docker-cheat-sheet)<br>
[Provision and Manage Remote Docker Hosts with Docker Machine on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-provision-and-manage-remote-docker-hosts-with-docker-machine-on-ubuntu-18-04/)<br>
[Get Started with Docker](https://docs.docker.com/get-started/)<br>
[Docker Container](https://www.docker.com/resources/what-container/)<br>
https://www.docker.com/resources/what-container <br>
[Docker Compose](https://docs.docker.com/compose/)<br>
[Quickstart: Compose and Django](https://docs.docker.com/compose/django/)<br>
[Install Docker Compose](https://docs.docker.com/compose/install/)<br>
[Test Docker installation](https://docs.docker.com/get-started/)<br>
[Continuous Integration and Continuous Deployment (CI/CD)](https://www.docker.com/solutions/cicd)<br>
https://www.docker.com/why-docker
[Understanding Docker Build Args, Environment Variables and Docker Compose Variables](https://vsupalov.com/docker-env-vars/)<br>
[Docker ARG, ENV and .env - a Complete Guide](https://vsupalov.com/docker-arg-env-variable-guide/) <br>
[IMP- Docker project for Python, Django and Apache2 setup](https://github.com/ramkulkarni1/django-apache2-docker) <br>
[Docker Notes](http://ramkulkarni.com/blog/docker-notes/) <br>
[How to delete Docker containers from the command line](http://blog.baudson.de/blog/stop-and-remove-all-docker-containers-and-images) <br>
https://medium.com/the-code-review/docker-rm-how-to-stop-and-delete-containers-via-the-command-line-6a8fc2cc3f39
[IMP- Docker Cheat Sheet](https://github.com/sahanasj/docker-cheat-sheet)


# Notes:
* The docker-compose.yml - file describes the services that make your app.
* The Dockerfile - Docker can build images automatically by reading the instructions from a Dockerfile. It is a text document that contains all the commands a user could call on the command line to assemble an image. 
Best Practices: https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/
* The docker build - This command builds an image from a Dockerfile and a context.
https://docs.docker.com/engine/reference/builder/


# Troubleshoot
If incase, encounter any issues while installing docker on ubuntu 18.04, follow the below steps:

$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
<br>

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
<br>

$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic test"
<br>

$ sudo apt update
<br>

$ sudo apt install docker-ce
<br>
Reference link - https://askubuntu.com/questions/1030179/package-docker-ce-has-no-installation-candidate-in-18-04




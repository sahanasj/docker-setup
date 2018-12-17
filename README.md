# docker-setup

Installation of Docker on Ubuntu 18.04 and Use Docker

# Getting Started
<details>
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
Add the Docker repository to APT sources 
<br>
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

<br>
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

<details>
<summary>Quick Docker cheatsheet to start and stop docker services</summary>

<b>Using Systemctl:</b>

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

</details>

# Important Resources
[How to install Docker on Ubuntu 16.04 and 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04/)<br>
[Docker installation video](https://www.youtube.com/watch?v=hY34PpllKf4)<br>
[Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)<br>
[Docker Cheatsheet](https://github.com/wsargent/docker-cheat-sheet)<br>
[Provision and Manage Remote Docker Hosts with Docker Machine on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-provision-and-manage-remote-docker-hosts-with-docker-machine-on-ubuntu-18-04/)<br>



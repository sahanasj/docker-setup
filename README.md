# docker-setup

Installation of Docker on Ubuntu 18.04 and Use Docker

# Getting Started
<details>
<summary>Quick Docker Install on Ubuntu 18.04</summary>

```
***Prerequisites***
One Ubuntu 18.04 server set up with a non-root user with sudo privileges and a basic firewall configuration


*** Step 1 — Installing Docker ***
The Docker installation package available in the official Ubuntu 18.04 repository may not be the latest version. To get this latest version, install Docker from the official Docker repository. This section shows you how to do just that.
First, in order to ensure the downloads are valid, add the GPG key for the official Docker repository to your system:

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Add the Docker repository to APT sources
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

Next, update the package database with the Docker packages from the newly added repo:
$ sudo apt-get update

Make sure you are about to install from the Docker repo instead of the default Ubuntu 18.04 repo:
$ apt-cache policy docker-ce

You should see output similar to the follow:

<image>

Note: Notice that docker-ce is not installed, but the candidate for installation is from the Docker repository for Ubuntu 16.04 (xenial).

Finally, install Docker:
$ sudo apt-get install -y docker-ce

Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it's running:
$	sudo systemctl status docker

The output should be similar to the following, showing that the service is active and running:

<image>


Installing Docker now gives you not just the Docker service (daemon) but also the docker command line utility, or the Docker client.

*** Step 2 — Executing the Docker Command Without Sudo (Optional) ***
If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:
$	sudo usermod -aG docker ${USER}

To apply the new group membership, you can log out of the server and back in, or you can type the following:
$	su - ${USER}

You will be prompted to enter your user's password to continue. Afterwards, you can confirm that your user is now added to the docker group by typing:
$	id -nG

If you need to add a user to the docker group that you're not logged in as, declare that username explicitly using:
$	sudo usermod -aG docker username

*** Step 3 — Using the Docker Command ***
With Docker installed and working, now's the time to become familiar with the command line utility. Using docker consists of passing it a chain of options and commands followed by arguments. The syntax takes this form:

$	docker [option] [command] [arguments]

To view all available subcommands, type:
$	docker

To view system-wide information about Docker, use:
$	docker info

*** Step 4 — Working with Docker Images ***
Docker containers are run from Docker images. By default, it pulls these images from Docker Hub, a Docker registry managed by Docker

To check whether you can access and download images from Docker Hub, type:
$	docker run hello-world

In the output, you should see the following message, which indicates that Docker is working correctly:

You can search for images available on Docker Hub by using the docker command with the search subcommand. For example, to search for the Ubuntu image, type:
$	docker search ubuntu

The script will crawl Docker Hub and return a listing of all images whose name matches the search string. In this case, the output will be similar to this:

*** Note - To start and stop docker services: ***
Using Systemctl:

$ sudo systemctl status docker 
$ sudo systemctl stop docker
$ sudo systemctl start docker
$ sudo systemctl daemon-reload

[Or] 

$ sudo service docker status
$ sudo service docker stop
$ sudo service docker start

# Important Resources
How to install Docker on Ubuntu 16.04 and 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04/)<br>
[Docker installation video](https://www.youtube.com/watch?v=hY34PpllKf4)<br>
[How To Provision and Manage Remote Docker Hosts with Docker Machine on Ubuntu 18.04] (https://www.digitalocean.com/community/tutorials/how-to-provision-and-manage-remote-docker-hosts-with-docker-machine-on-ubuntu-18-04/)<br>



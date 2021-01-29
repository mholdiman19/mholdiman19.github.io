# Docker

## UDEMY Class Notes

### Section 1

* **Docker** is a platform that lets you package, develop and run applications in containers.
* a virutal environment on top of the OS kernel to capture all of its sw-libraries, dependencies, etc.

_insert image from notes here_

* isolated from other containers
* lightweight approach, more so than virtual machines.
* portability to major architectures and OS's
* able to achieve continuous integration & deployment for DevOps

#### Main Features

* create images and containers
* docker-compose for multi-container apps
* docker swarm to utilize multiple machines running Docker

#### Installing Docker on Ubuntu

1. Download Docker Install Script => `wget -qO- https://get.docker.com/ | sh`
2. `sudo usermod -aG docker $(whoami)`
3. Restart OS
4. Try `docker` and `docker container ls`
5. To verify your Docker version => `docker --version`



## Docker Essentials 

_Resource_: Learn Linux YouTube Series by Jay LaCroix => [Docker Essentials](https://youtube.com/playlist?list=PLT98CRl2KxKECHltRib03tG8pyKEzwf9t)

### Part 3 - Installing Docker on Windows 10, macOS and Ubuntu

**For Ubuntu**

1. Make sure that your system is the most up to date.
    * `sudo apt update`
    * `sudo apt dist-upgrade`
2. Run `systemctl status docker` to see if Docker is running.
    * If it is showing as disbled, then you can run `sudo systemctl enable docker`
    * If it is not started, then you can run `sudo systemctl start docker`
3. To confirm that Docker is working, you can run `sudo docker run hello-world`
4. To make sure that you don't always have to run commands with `sudo`, you can do `sudo usermod -aG docker <userid>`
5. Restart system after adding yourself to the Docker group.

### Part 4 - Running Containers 

* `docker images` => will show you all available images on your machine.
    * Since we ran the `hello-world` image in the previous step, the `docker image`should be listed in the results.
* `docker search <imagename>` => will show you all available images with the name ubuntu
* `docker pull <imagename>` => will download the image
* `docker run <imagename>` = will run the image you want to create your container in
    * Note if you run a container and there is nothing for it to do, then it will just exit.
    * For example, if you just type `docker run ubuntu`, then nothing will happen because you did not tell it do anything.
* `docker ps` => list of Docker images running on your machine.
* `docker ps -a` => list of Docker images that have been run on your machine.
* To attempt to keep a container running, you can run => `docker run -it ubuntu /bin/bash`
    * `it` => `i` stands for interactive; `t` stands for `tty` or terminal

### Part 5 - Making Containers Persist

* Using the same command as above => `docker run -it ubuntu /bin/bash`
* Add `-d` to keep it running in the background => `docker run -it -d ubuntu /bin/bash`
* `-d` stands for daemon (a service running in the background) 
* To confirm the container is still running, run `docker ps`
    * _Results_:CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
                b677c09360ba   ubuntu    "/bin/bash"   3 minutes ago   Up 3 minutes         naughty_jones
* How to attach yourselft to a container => `docker attach <containerID>`
    * _Results_: prompt changes to `root@<containerID>`
* How to exit a container while leaving the container running => `Ctrl+pq`

### Part 6 - Accessing Containerized Applications


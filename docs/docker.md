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




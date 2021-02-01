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

* Let's try running a different container => `docker run nginx`
* Nginx is a proxy and web server
* `docker run -it -d -p 8080:80 nginx`
    * `-p` means port
    * Here we are opening port 8080 on our host computer and opening port 80 on the docker container.
* Then, do `docker ps` to make sure that your container is running.
* Since nginx is a webserver, you can type `<ipaddress of host>:8080` in to a browser, and you will see the nginx main screen popup.
* Any computer on your network should be able to bring up the webpage.
* To see the Nginx container running do a `docker ps`
* To stop the container from running you can do => `docker stop <containerID>`
* Now do =>  `docker run -it -d --restart unless-stopped -p 8080:80 nginx`
* The `restart unless-stopped` is very helpful so you can do a `Ctrl+C` without stopping the container from running.

### Part 7: Creating Images

* Last video in the series.
* Create an Ubuntu image
    * `docker run -it ubuntu`
    * `apt update`
    * `apt dist-upgrade`
    * `apt install apache2`
    * To see if apache is running => `/etc/init.d/apache2 status`
    * To start it => `/etc/init.d/apache2 start`
    * Let's install vim => `apt install vim-nox`
* Now, lets save all of these changes, so we do not lose them.
    * Do, `docker ps` to obtain the Container ID.
    * Then, do `docker commit <containerID> <newname>:<versioninfo>`
    * My example => `docker commit 5db0e25d6ca0 ubuntu/apache-test:1.0`
    * You receive a sha256 hash.
    * Then do `docker images` and you should see your image listed.
* Now, lets stop everything and go back in and see if we can still get to our image.
    * `docker stop <containerID>`
    * Do `docker ps` to make sure nothing is running.
    * Since you have confirmed nothing is running, lets try to locate and use our image we created earlier.
    * `docker run -d -it -p 8080:80 <imagename>`
    * For my example, it would be `docker run -d -it -p 8080:80 ubuntu/apache-test:1.0`
    * Do `docker ps`
    * Since it is running, lets bring up a webpage, using same webpage we used earlier, which was `<IPaddress:8080>`
    * Doh, it does not work.  Why?
    * Because Apache is not running, as we did not create an entry point.
    * Lets add an entry point => `docker commit --change='ENTRYPOINT ["apachectl", "-DFOREGROUND"]' c26 ubuntu/apache-test:1.1`
    * Receive SHA256 hash again
    * Do `docker images`
    * You should see both of your images
    * Do `docker ps` to see your running containers
    * Stop the original container that is still running => `docker stop <containerID>`
    * Then recall the last command via the up arrow, just change the version from 1.0 to 1.1.
    * Hit enter.
* Do `docker ps` to see insure your image is running.
* Now, lets try to bring up the webpage again.
* You should now see the Apache2 Default page.
* Now, lets automate this entire process by creating text file, known as a **docker file**










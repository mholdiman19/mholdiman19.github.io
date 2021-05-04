# OpenSSH

Notes:  These are my notes on Jay LaCroix's YouTube video.

[Link to Video](https://youtu.be/YS5Zh7KExvE)

## Connecting to a Server via OpenSSH CLI

* OpenSSH client is on the majority of Linux distributions.
* Even though the client is installed on your system, it does not mean people can connect to you.  
* How to tell if you have the SSH client installed => `which ssh`  
    * Results => `/usr/bin/bash` (meaning it is already installed)  
    * If the SSH Client was not installed, then you could search via => `apt search openssh-client`  

* To connect to a SSH Server => `ssh <username>@<server_IP_address>`
* You will receive a key fingerprint message if you have not connected to the server previously.  
* To see what occured in your system, navigate to => `ls /home/mholdiman/ -a`  
* You will see you have a hidden directory called `.ssh`
* Navigate to that directory => `cd .ssh`  
* Lets look at the file called `known_hosts` => `cat known_hosts`  
* The file will show all the fingerprints for servers you have connected to previously.  
* Why is this important?  It helps you mitigate "Man in the Middle" attacks.
  * Man in the Middle attack means you wouldn't be connecting to the server you think you are connecting to.  

* What happens when you connect to a server behind the scenes?
    1. Connect to the server via `ssh`.  
    2. Since you are root, you have full access to the log files.  
    3. Navigate to `/var/log/`  
    4. You can watch the `auth.log` file by doing => `tail -f auth.log`

* This is useful to know, so you can watch log if someone cannot connect.

## Configuring a SSH Client

* Located => `~/.ssh/`
* Create file called `config`

```bash
Host "name"
  Hostname "IP Address"
  Port 22
  User "username"
```
__NOTE:__ For this to work for me, I had to add the host and hostname information to my `/etc/hosts` file.  

## Using Public/Private Keys

* It is better to use ssh keys than to just use a password.
* Best practice is to disable password authorization on a server.
* To create a ssh keypair => `ssh-keygen`
* It will automatically create the keys in the default location.  

    * Default Location => `~/.ssh`
    * The two keys created with the above command are `id_rsa` and `id_rsa.pub`.
    * Once the keys are created a random art image and the key fingerprint will show in the output.  

* The private key `id_rsa` and `id_rsa.pub` are required for the SSH connection to work.
* The public key `id_rsa.pub` needs to be copied to the server.
* To do this, you can do the following:  

    * `cat` the contents of the `id_rsa.pub` and copy and paste to the `authorized_keys` file on the server.
    * Use the command => `ssh-copy-id -i ~/.ssh/id_rsa.pub root@<Server_IP>`.  

* The SSH program will automatically create the `.ssh/` and the `authorized_keys` file if they do not already exist.  

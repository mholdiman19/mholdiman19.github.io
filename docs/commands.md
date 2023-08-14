# Linux CLI Commands

## Adding a User in Linux

* To add the user => `adduser <username>`
* To verify the new user was created => `ls /home` or `cat /etc/passwd`
* To add user to the sudoers group => `usermod -aG sudo <username>` then => `groups <username>`

## Changing Password via CLI

* To change your password => `passwd`
* To change someone else's password => `sudo passwd <user's name>`

## APT (`apt`) ##

### How to Prevent & Fix Package Dependency Errors in Ubuntu ###

* Update Package => `sudo apt update`
* Upgrade Packages => `sudo apt dist-upgrade`
* Clear Apt Package Cache => `sudo apt clean`
* Do a Mock Installation => `sudo apt install --dry-run "package name"`
* Remove Mock Installation => `sudo apt remove --dry-run "package name"`
* Fix Broken Installations => `sudo apt -f install`
* Configure Packages that Failed to Install => `sudo dpkg --configure -a`
* Use PPA-Purge (to install) => `sudo apt install ppa-purge`
* To Purge a PPA => `sudo ppa-purge "ppa:address"`
  * Example => `sudo ppa-purge ppa:geany-dev/ppa`
* Use Aptitude Package Manager => `sudo apt install aptitude`
  * _NOT_ the same as `apt`
* To Reinstall Ubuntu Desktop Package => `sudo apt install --reinstall ubuntu-desktop`
  * Pulls in essential packages that were installed by default
* To Remove or Disable PPAs Before Upgrading to a Newer Version of Ubuntu => `sudo add-apt-repository --remove "ppa:name"`
  * Use Synaptic Package Manager to Disable a PPA (not removing)
* To Search for a Software Package => `apt search <PACKAGE-NAME>`

## COPY (`cp`) ##

* `cp` => commande-line utility for copying files and directories on Unix and Linux systems
* Command Syntax => `cp [options] SOURCE... DESTINATION`
* To Copy a File => `cp file file_backup`
* To Copy a File to Directory => `cp file.txt /backup`
* To Force Copy to Prompt for Confirmation => `cp -i file.txt file_backup.txt`
* To Copy a Directory (including all files and subdirectories) => `cp -R Pictures Pictures_Backup`

## DHCP Client ##

* Use this command to force Ubuntu Server 20.04 LTS to request a DHCP Client
* `dhclient -r -v eth0 && rm /var/lib/dhcp/dhclient.* ; dhclient -v eth0`

## DPKG (`dpkg`) ##

* To Install a DEB Package => `sudo dpkg -i example.deb`
* If you get => `dpkg: error processing package`
  * Do => `sudo apt install -f`

## Expansion Shortcuts ##

__Resource Used__ => [Advanced Bash Scripting Tuturial](https://youtu.be/emhouufDnB4)

### Tilde Expansion

### Brace Expansion

* written with braces around an expression
* can help with repeated commands with different terms or interpolation within a range

__Example1__: `touch {apple,banana,cherry,durian}`
   
```bash
$ touch {apple,banana,cherry,durian}
$ ls
apple  banana  cherry  durian
```
__Example2__: `touch file_{1..10}`

```bash
$ touch file_{1..10}
$ ls
file_1  file_10  file_2  file_3  file_4  file_5  file_6  file_7  file_8  file_9
```

* If you go above 10, say to 1000, the files may not sort the way you want, so you should use _zero padding_.  [Example => `touch file_{01..1000}`]
* The above can also be completed with letters.

```bash
$ echo {A..z}
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z [  ] ^ _ ` a b c d e f g h i j k l m n o p q r s t u v w x y z
```

## GDEBI (`gdebi`) ##

* `gdeb` => command to install DEB packages that will automatically download and install any required dependencies.
  * May need to be installed => `sudo apt install gdebi-core`
* Once installed command syntax is => `sudo gdebi example.deb`

## IP (`ip`) ##

* To Up/Down an Interface
  * `ip link set dev eth0 down`
  * `ip link set dev eth0 up`
* Please reference `ip` [Command Cheat Sheet for RHEL](https://advantecho365-my.sharepoint.com/:b:/g/personal/michelle_holdiman_advantech_com/EXKdyKkk1jJOjx6LhiP9LUsBVZMdibcxfitKnMv-xJBBwA?e=0vueN7)
  * `addr` => displays IP addresses and property information
    * EX => `ip addr show dev enp0s25`
  * `link` => manage and display the state of all the network interfaces
    * EX => `ip link show dev enp0s25`
    * EX => `ip -s link` [shows statistics]
  * `route` => displays and alters the routing table
    * EX => `ip route`
  * `maddr` => manages and displays multicast IP addresses
    * EX => `ip maddr`
  * `neigh` => shows neighbor objects; also known as the ARP table for IPv4
    * EX => `ip neigh`
  * `help` => displays a list of commands and arguments for each subcommand
    * EX => `ip link help`
    * EX => `ip help`
    * EX => `ip addr help`
  * Adjusting and Viewing Routes
    * `route add` => adds an entry to the routing table
      * EX => `ip route add default via 192.168.1.1 dev enp0s25`
      * EX => `ip route add 192.168.1.0/24 via 192.168.1.1`
      * EX => `ip route add 192.168.1.0/24 dev enp0s25`
    * `route delete` => deletes a routing table entry
      * EX => `ip route delete 192.168.1.0/24 via 192.168.1.1`
    * `route replace` => replaces, or adds if not defined, a route
      * EX => `ip route replace 192.168.1.0/24 dev enp0s25`
    * `route get` => displays the route an address will take
      * EX => `ip route get 192.168.1.5`
  * Useful Networking Commands (Not Necessarily Provided from `ip` route)
    * `arping` => sends an ARP request to a neighbor host
      * EX => `arping -I enp0s25 192.168.19.8`
      * EX => `arping -D -I enp0s25 192.168.19.1` [Checks for duplicate MAC addresses]
    * `ethtool` => queries or controls network drive and hardware settings
      * EX => `ethtool -g eth0`
      * EX => `ethtool -i eth0`
      * EX => `ethtool -S eth0`

## IPTABLES (`iptables`)

* a firewall tool used to manage packet filtering & NAT rules
* frontend tool used to manage the Linux kernel's `netfilter` framework
* Please reference:
    * [A Tutorial for Controlling Network Traffic with IPtables](https://www.linode.com/docs/guides/control-network-traffic-with-iptables/)
    * [Understanding IPtables](https://www.linode.com/docs/guides/what-is-iptables/)
* Can use `iptables` to filter both incoming and outgoing packets as well as route network packets.

### Tables

* (def) a collection of chains that serve a particular function.
* 3 Main Tables
    * __Filter__ => used to control the flow of packets in and out of the system.
    * __NAT__ => used to redirect connections to other interface on the network.
    * __Mangle__ => used to modify packet headers.
* Each table has a __chain__ of rules.


|FILTER TABLE|NAT TABLE|MANGLE TABLE|
| :---: | :---: | :---: |
| INPUT CHAIN | OUTPUT CHAIN | INPUT CHAIN |
| OUTPUT CHAIN | PREROUTING CHAIN | OUTPUT CHAIN |
| FORWARD CHAIN | POSTROUTING CHAIN | FORWARD CHAIN |
|    |   | PREROUTING CHAIN |
|    |   | POSTROUTING CHAIN |



__NOTE:__ The __Filter Table__ is responsible for blocking or allowing connections and is the default filter in iptables.

### Chains

* (def) a list of rules that are processed in order.
* 5 main chains in iptables:
    * _Input_ => used to manage incoming packets/connections to service or protocol.
    * _Output_ => outgoing packet after it has been created/processed.
    * _Forward_ => forwards incoming packets from their source to destination (__routing__).
    * _Prerouting_ => after the packet enters the network interface.
    * _Postrouting_ => before the packet leaves the network interface after the routing decision has been made.

### Understanding Packet Flow

* Incoming packets are analyzed at each chain and are tested against a set of rules.
* If a rules is matched, the target is set.  
* Targets are the following:
    * ACCEPT => Stop processing and let the packet flow.
    * REJECT => Drops the packet with feedback.
    * DROP => Stops the processing at the current chain and drops the packet.
    * LOG => Similar to ACCEPT, but it is logged to `/var/log/messages`
* As an example, say you want to block all incoming connections to your web server on port 80.
* Example packet flow:
    * Add a rule to the incoming chain in the filter table.
    * Set the target to `REJECT`.  
    * If the target gets to the end of the chain without matching any rules, the default rule is used.
    * If there is no default rule, the packet is accepted.

### Installing IPtables

* `iptables` is an included utility by default.
* Recommendation is to disable or delete any rules you have before beginning or creating a new configuration.
* You _must_ uninstall any other firewall management utilities like UFW.
* To install => `sudo apt install iptables`
* Default config file for iptables => `/etc/sysconfig/iptables`.
* Can be modified using text editor of your choice.
    * EX => `vim /etc/sysconfig/iptables`

### Using IPtables 

#### Building IPtables Commands

* Some common command options.
* See [iptables man page.](https://manpages.debian.org/bookworm/iptables/iptables.8.en.html)
* EX => `sudo iptables -t filter -I INPUT -m tcp -p tcp --dport 80 -j REJECT`
* The above command blocks any incoming traffic to the web server.

#### Listing Chains

* To see all the available chains in the filter table by using the list command.
* EX => `sudo iptables -L` 
* EX => `sudo iptables -L -nv`
* This will display the `INPUT`, `OUTPUT` and `FORWARD` chains.

#### Specifying Default Policy

* If you have a fresh configuration or no predefined rules, you should set the default target policy.
* In the example below, the default policy is set to `ACCEPT`, which means all traffic is accepted by default.
* To set default policy:
```bash
sudo iptables --policy INPUT ACCEPT
sudo iptables --policy FORWARD ACCEPT
sudo iptables --policy OUTPUT ACCEPT
```
* To disable access, just use `DROP` or `REJECT` instead of `ACCEPT`.

#### Blocking & Allowing Connections From IP Addresses

* 192.168.1.1 is the example IP; replace with your IP.
* To block all incoming requests from an IP address:
> `sudo iptables -A INPUT -s 192.168.1.1 -j DROP`
* To block all incoming connections from an entire subnet
> `sudo iptables -A INPUT -s 192.168.1.1/24 -j DROP`
* To block all outgoing connections to a particular IP or subnet add the following `OUTPUT` chain
> `sudo iptables -I OUTPUT -s 192.168.1.1 -j DROP`

#### Blocking & Allowing Connections To Ports

* To block connections to ports and services, specify the protocol and the destination port.
* To block any incoming SSH connections to the server:
> `sudo iptables -I INPUT -p tcp --dport 22 -j DROP`
* To block any incoming connections to your web server: running on port 80
> `sudo iptables -I INPUT -p tcp --dport 80 -j DROP`
* To block an IP from connecting to a specific service:
> `sudo iptables -I INPUT -p tcp --dport 80 -s 10.10.10.1 -j DROP`
* Deeper dive into the `iptables` command to block all traffic:
> `iptables -A INPUT -j DROP -p tcp --destination-port 110 -i eth0`

    * `-A` => will add or append the rule to the end of the chain.
    * `INPUT` => will add the rule to the table.
    * `DROP` => packets will be discarded.
    * `-p tcp` => means the rule will only drop TCP packets.
    * `--destination-port 110` => filters packets targeted to port 110.
    * `-i eth0` => means this rule will only impact packets arriving on the _eth0_ interface.

__NOTE:__ `iptables` does NOT recognize aliases on the network interface.  If you have virtual interfaces, then you will have to specify the destination IP address.
> `iptables -A INPUT -j DROP -p tcp --destination-port 110 -i eth0 -d 192.168.100.0`


#### Saving Changes

* To save the changes you have made to your rule-set, so they are persistent:
>  `sudo /sbin/iptables-save`

#### Deleting & Clearing Rules

* If you want to delete a specific rule, you need to determine the rule line number.
* To do this, list the chains and the rules with the following options: 
> `sudo iptables -L --line-numbers`
* The above lists the relevant line numbers for each rule.
* After determining the line number, you can delete with the following:
> `sudo iptables -D INPUT 3`
* To clear all the rules and start over:
> `sudo iptables -F`

## LINKS (`ln`)

* `ln` creates hard and symbolic links
* `ln <filename> <link_name>`

### Hard Link

* `ln <filename> <linkname>`
* original way of creating links
* creates an additional link to a file
* cannot reference a directory

### Symbolic Link

* more modern approach to links
* think of it as a 
* `ln -s <filename> <link_name>`
     
## MOVE (`mv`)
  
* Moves files
* To move a file, do the following:
    - `mv source_file... target_dir`

## Removing Crash Report Files ##

* Crash report files are located in => `/var/crash`
* To remove them, do the following:
    - `cd /var/crash/`
    - `ls`
    - `sudo rm /var/crash`

## SECURE COPY (`scp`) ##

  Resource => [How to Use SCP Command to Securely Transfer Files](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/)

  Description:  __Secure Copy__ `scp` is a command line utility that allows you to securely copy files and directories between two locations.

  Command Syntax:

  * `scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2`
  * `OPTION`- `scp options` such as cipher, ssh configuration, ssh port, limit, recursive copy...etc.
  * `[user@]SRC_HOST:]file1` = Source File
  * `[user@]DEST_HOST:]file2` = Destination File

## System Log (rsyslog)

__REFERENCE__:  [How to Create a Centralized Log Server with Rsyslog](https://www.tecmint.com/create-centralized-log-server-with-rsyslog-in-centos-7/#:~:text=The%20syslog%20server%20on%20a,messages%20can%20send%20their%20logs.)

* stored in `/var/log`
* can act as a client or a server
* Ex of syslog log message scheme:  `type (facility).priority (severity) destination(where to send the log)`
    - A __facility__ is represented by the internal system processes that generates the messages.
    - In Linux interal processes (aka "facilities") that generate logs are standardized as follows:
        - __auth__ => messages generated by authentication processes (logins).
        - __cron__ => messages generated by scheduled processes (crontab).
        - __daemon__ => messages generated by daemons (internal services).
        - __kernel__ => messges generated by the Linux kernel.
        - __mail__ => messages generated by a mail server.
        - __syslog__ => messages generated by the rsyslog daemon itself.
        - __lpr__ => messages generated by local printers or a print server.
        - __local0-local7__ => custom messages definted by an administrator (local7 is usually assigned for Cisco or Windows).
    - The __priority__ (severity) levels are standardized as well.  
    - Each priority is assigned with a standard abbreviation and a number as described below.  
        - __emerg__ => Emergency - 0
        - __alert__ => Alerts - 1 
        - __err__ => Errors - 3
        - __warn__ => Warnings - 4
        - __notice__ => Notification - 5
        - __info__ => Information - 6
        - __debug__ => Debugging - 7
    - 3rd part of the syslog schema is represented by the __destination__ directive.  
    - Rsyslog daemon can send log messages to be written in a file on a local filesystem (ex. `/var/log`), it can be piped to another local process, sent to a local user console (ex. to `stdout`), sent via a message to a remote syslog server via TCP/UDP protocol, or even discard the message (ex. `/dev/null`)
* To check if the rsyslog service is installed and/or running => `systemctl status rsyslog.service`
* If not running => `systemctl start rsyslog.service`
* If not installed => `sudo apt-get install rsyslog`
* To configure rsyslog => `sudo vim /etc/rsyslog.conf`
* To confirm service is running on configured ports => `ss -tunelp | grep 514`



## TCPDUMP (`tcpdump`)

__REFERENCE__:  [12 TCPDUMP Commands - A Network Sniffer Tool](https://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/)

* Packer sniffer tool
* Offers the ability to save the tcpdump output to a `pcap` file.
    - Example => `tcpdump -i eth1 -s 65535 -w <filename>.pcap`
* Command Syntax:
    - From a specific interface => `tcpdump -i eth0`
    - Capture specified amount of packets => `tcpdump -c 5 -i eth0`
    - To display available interfaces => `tcpdump -D`
    - To capture and save packets in a file => `tcpdump -w <filename> -i eth0`
    - Read captured packets file => `tcpdump -r <filename>`
    - Capture IP address packets => `tcpdump -n -i eth0`
    - To capture only TCP packets => `tcpdump -i eth0 tcp`
    - To capture packets on a specific port => `tcpdump -i eth0 port 22`
    - To capture packets from a source IP => `tcpdump -i eth0 src <IP address>`
    - To capture packets from a destination IP => `tcpdump -i eth0 dst <IP address>`

## TREE (`tree`)

* Lists the content of directories in a tree-like format
* To run `tree` in a directory that requires root user permissions => `sudo tree`
* To display contents, while including hidden files, use the `-a` flag => `sudo tree -a`
* To see the full path prefix => `sudo tree -f`
* To see the subdirectories, minus the files in them => `sudo tree -d`
* To specify the maximum display depth of the directory, use the `-L` flag => `sudo tree -L 2`
* To only display files that match a specific wild-card pattern, user the `-P` flag => `sudo tree -P cata*`
* To eliminate empty directories, you can use the `--prune` option => `sudo tree --prune`
* If you would like to see the file permissions, then do => `sudo tree -p`
* If you would like to redirect the output to a text file => `sudo tree -o <filename>`

## Customizing Your Terminal

* 


## Syncthing Install & Configuration ##

* Downloaded install file at [Syncthing Downloads](https://syncthing.net/downloads)
  * Did the install via the CLI below location to download the .deb file
* Resource I used to install and configure this was listed on Journal Date 20200917
* Added `systemd` unit
  * `wget https://raw.githubusercontent.com/syncthing/syncthing/main/etc/linux-systemd/system/syncthing%40.service`
  * `sudo chown root: syncthing@.service`
  * `sudo mv syncthing@.service /etc/systemd/system`
  * `sudo systemctl daemon-reload`
* Enable & Start the Unit
  * `sudo systemctl enable syncthing@<user>`
  * `sudo systemctl start syncthing@<user>`
* Access the Web GUI for Synchting
  * http://localhost:8384
* Allow connections ot the Web GUI from Network Devices
  * Open the configuration file and edit it
    * `nano /home/<user>/.config/syncthing/config.xml`
    * Change the line => `<address>127.0.0.1:8384</address>`
    * To `<address>0.0.0.0:8384</address>`
  * Restart Syncthing
    * `sudo systemctl restart syncthing@<user>`
* NOTE:  Now, you should be able to access the Web GUI and add shared folders.  Make sure you set up a username and password in the GUI, to keep it safe.

## To See Available Services in Router Kernel ##

* `ls /etc/init.d/`

## To Change Network Settings in Ubuntu via Netplan ##

[Link to Article](https://netplan.io/examples/)

* Update the YAML file => `/etc/netplan/`
* Example of YAML File => `/home/userve/Documents/yamlexample.txt`


## To See Partitions & Check Disk Space ##

* `sudo fdisk -l`

## To Check Hard Drive Disk Health via CLI ##

* Install `smartmontools` => `sudo apt install smartmontools`
* Determine which drives you want to check => `sudo fdisk -l`
  * Above command will give you a list of all drives and partitions.
* Three Possible Tests
  * Short Test => Sufficient for detecting issues
  * Long Test => Used if you have concerns, as it examines the whole disk
  * Conveyance Test => Used to test if damage occured during tranportation of the device from the manufacturer

## To Check Hardware Information on Linux ##

* To see info about the cpu and processing units => `lscpu`
* A report that lists detailed and brief information regarding multiple differenct hardware units, such as cpu, memory, disk, usb controllers, network adapters, etc => `sudo lshw -short`
* General purpose utility that can report detailed and brief info about multiple different hardware components => `hwinfo --short`

## To Check Power (Battery) Information via CLI ##

[Link to Article](https://www.cyberciti.biz/faq/linux-laptop-battery-status-temperature/)

### UPower

* Description:  A command line tool for UPower which provides an interface to enumerate power sources on the system and control system-wide power management.  
* Using the `upower` command => `upower -i /org/freedesktop/UPower/devices/battery_BAT0`

### ACPI

* Description:  Shows battery status and other ACPI information from /proc and /sys file system.
* To check the battery => `acpi -V`
* To just see status => `acpi`
* To see the AC adapter information => `acpi -a`
* To show thermal information => `acpi -t`
* To show thermal information in Fahrenheit => `acpi -tf`
* You can browse the same information by going to => `cd /proc/acpi/` and doing, `ls -al`

### Via Directory ###

* Description:  Stores ACPI information about your first battery.
* Command => `ls -l /sys/class/power_supply/BAT0`

### Via GUI ###

* Description:  The GUI program for the gnome power management infrastructure.  It allows users to visualize their power consumption of laptop hardware.  
* Command => `gnome-power-statistics`


## How To Use Workspaces ##

* Open the Activies Window
* Use `Control+Alt+Up` to move to the workspace shown above the current workspace in the workspace selector.
* Use `Control+Alt+Down` to move to the workspace shown below the current workspace in the workspace selector.

## How To Remove Directories & Files in Linux ##

* You can use the Gnome GUI
* You can delete directories using `rmdir`, `rm` and `find`
* __NOTE__ You can recover files when you delete them using the GUI, but not when using the command line.
* To delete a directory in Linux filesystems, you are required to have write permission on the directory and its contents.  If not, you will get "Operation Not Permitted" error.
* Directory names with a space in them must be escated with a backslash `/`.

# Removing Directories with `rmdir` #

* To remove a directory, you can use the `rmdir` command line utility for deleting __empty__ directories.
  * Type the command followed by the name of the directory you want to remove.
  * `rmdir <directory name>`
  * If the directory is not empty, you will receive the following error:
    * `rmdir: failed to remove <directory name>: No such file or directory`
* In the above case you will need to use the `rm` command or manually remove the directory contents before you delete the directory using `rmdir`.
* By default, when used without an option `rm` does not remove directories.  

# Removing Directories with `rm` #

[Link to Article](https://linuxize.com/post/remove-directory-linux/)

* `rm` is a command-line utility for deleting files and directories.
* Unlike `rmdir` the `rm` can delete both empty and non-empty directories.
* By default, when used without any option `rm` does not remove directories.  
* To delete and empty directory, use the `-d` `(--dir)` option and to delete a non-empty directory, and all of its contents use the `-r` `(--recursive or -R)` option.
  * To delete a directory with all of its contents you would type:
  * `rm -r <directory name>`
* If a directory or a file within the directory is write-protected, you will be prompted to confirm the deletion.  
  * To remove a directory without being prompted, use the `-f` option.
  * `rm -rf <directory name>`


## 10 Handy SystemD Commands: A Reference ##

[Link to Article](https://www.redhat.com/sysadmin/systemd-commands)

* From `systemd` man page => a unit file is a plain text inistyle file that encodes information about a service, a socket, a device, a mount point, an automount point, a swap file or a partition, a start-up target, a watched file system path, a timer controlled and supervised by `systemd`.
* `systemd` => a resource management slice, or a group of externally created processes.
* `systemctl list-unit-files`
  * lists all unit files
* You can `grep` to see just the enabled services.
  * `$ systemctl list-unit-files | grep enabled`
  * `$ systemctl list-unit-files | grep disabled`

  * __Example Output Below__

  | Unit File | State | Vendor Preset |
  | --------- | ----- | ------------- |
  | proc-sys-fs-binfmt_misc.mount | disabled | enabled |
  | acpid.service | disabled | enabled |
  | brltty.service | disabled | enabled |      
  | console-getty.service | disabled | disabled |
  | debug-shell.service | disabled | disabled |
  | fwupd-refresh.service | static | disabled |
  | openvpn3-autoload.service | disabled | enabled

* These unit files, located under `/lib/systemd/system`, are roughly the equivalent to the legacy init scripts that were located under `/etc/rc.d/init.d`.
* If you or your software installation created `init` scripts, a corresponding `systemd` unit file is mapped for you.  
  * Additional information can be found at `/etc/rc.d/init.d/README`.

## Wildcards ##

* An asterick (`*`) will match any characters with your query.
* A question mark (`?`) will match any single character.
* An exclamation (`!`) plus your sting of characters inside brackets will search for the string => `[!abc]`
* A (`:`) in front of and behind a string closed in double brackets will search for the specified class => `[[:abc:]]`

## How To Create Your Own Linux Commands

__Resource Used:__ [How to Create Your Own Commands in Linux(https://www.freecodecamp.org/news/how-to-create-your-own-command-in-linux/)]

* By using the `alias` command, you can create your own commands.
* Command syntax => `alias [alias-name[=string]...]`
* Example Scenerio:  You go to your `Videos` directory regularly, so you create an `alias` to get the `Videos` directory faster.
* Command example => `alias cdv="cd Videos"`

## How To View The Alias Command You Created

* Maybe your memory is not the greatest, so you cannot remember all of the `alias` commands you have created.
* To view a list of your `alias` commands => `alias -p`
* Please see an example of my results below:

```text
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
```
## Removing an Alias Command

* So, you don't use your `alias` as much as you thought you would.
* In that case, lets remove it.
* You can remove the `alias` by doing => `unalias alias_name`

## Removing All Alias Commands

* To remove all of your `alias` commands, you can do the following:  `unalias -a`
* Sad news about the `alias` command; they are not permanent.
* They can only be used for that terminal session.

## Creating a Permanent Alias

* To create a permanent `alias` command, you have to add the `alias` command to the shell configuration file.
* Common shells:
  * Bash => `~/.bashrc`
  * Zsh => `~/.zshrc`
  * Fish => `~/.config/fish/config.fish`

* Most Linux distros use `bash`.
* So how do we do this?
  * Open `~/.bashrc` using nano or Vim. 

```bash
sudo nano ~/.bashrc
```

  * Go to the bottom of the file.
  * Add the following `alias cdv="cd Videos"`
  * Save and exit out of the file.
  * Close and reload the terminal.
  * Do `alias -p` to confirm your alias is listed.
  * Please see results below.

```text
alias cdv='cd Videos'
```






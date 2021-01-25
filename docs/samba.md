# Installing & Configuring Samba

1. Update first => `sudo apt update`
2. To install => `sudo apt install samba`
3. To check version information => `samba --version`
4. To see where Samba is installed => `whereis samba`
5. Create a directory for Samba to share => `mkdir ~/<username>/sambashare/`
6. Location of Samba configuration file => `/etc/samba/smb.conf`
7. Example of Samba configuration file:

    [sambashare]
        comment = Samba on Ubuntu
        path = /home/<username>/sambashare
        read only = no
        browsable = yes

8. To setup a Samba password => `sudo smbpasswd -a username`

## Connecting to a Share 

* In Ubuntu:  Open up the default file manager and click _Connect to Server_ then enter => `smb://ip-address/sambashare`
* In Windows: Open File Manager and edit the file path to => `\\ip-address\sambashare`
  * NOTE:  `ip-address` => Samba server IP address & `sambashare` is the name of the share

*RESOURCE*:

[Installing and Configuring Samba](https://ubuntu.com/tutorials/install-and-configure-samba#4-setting-up-user-accounts-and-connecting-to-share)

### My Samba Configuration

    [homes]
       comment = Home Directories
       browseable = yes
       read only = no
       create mask = 0700
       directory mask = 0700
       valid users = %S
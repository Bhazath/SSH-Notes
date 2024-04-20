#  SSH
---

OpenSSH is the tool of choice for managing Linux installations remotely - and is indispensable in DevOps, Cloud, System Administration, Hosting, and more. Since it's so widely used, you should definitely learn it. In this video, I go over all the basics you need to use OpenSSH in your workflow. This includes understanding the difference between the client and server binaries, how to connect, config files, keys, and more!

## 1) Connecting to a server via OpenSSH
---
### to see ssh, is installed in linux 
``` bash
$ which ssh
//usr/bin/ssh
```
### OpenSSH is a specific implementation of the SSH protocol suite. It includes a set of tools such as ssh, scp, and sftp, which are widely used for secure remote access, file transfer, and management of network devices. OpenSSH is open-source and is maintained by the OpenBSD project.

### To install openssh-client in linux
```bash
$ apt search openssh-client

$ apt install openssh-client
```
### To connect a ssh remote device
``` bash
$ ssh root@<IP>
```

### .ssh is whare ssh config are stored, key and known hosts file 
``` bash
$ cd .ssh/
$ ls
id-ed25519 id_ed25519.pub known_hosts
```
Known_hosts file is where the ssh finger print are stored 

``` bash
$ /var/log/auth.log 
```
(auth.log) Contains system authorization information, including user logins and authentication machinsm that were used.

 ## 2) Configuring the OpenSSH Client

To configuring the Openssh ~/.ssh/ creat a config file .ssh folder
Contains system authorization information, including user logins and authentication machinsm that were used.
``` bash
                    # Config in ~/.ssh
Host <any name>
  Hostname <IP>
  Port 22
  User root
```
``` bash
$ ssh <host <any name>>
```
You can add multiple server to .ssh/config file 
``` bash
Host <any name>
  Hostname <IP>
  Port 22
  User root

Host server2
  Hostname <IP>
  Port 22
  User GOST
```
## 3) Using public/private keys

### How to create a SSH Key
``` bash

User@Admin-Gost:~/.ssh$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/gost/.ssh/id_rsa):        # crating a defalt key in ~/user/.ssh/
Enter passphrase (empty for no passphrase):                          # added layer of securety (password for key)
Enter same passphrase again:
Your identification has been saved in /home/gost/.ssh/id_rsa
Your public key has been saved in /home/gost/.ssh/id_rsa.pub          #it will create .pub for same key
The key fingerprint is:
SHA256:W8MpYmY1Osp2m8V2fzX9sQte7NYt644ZQ1Ob9jis5Qk gost@Admin-Gost
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|                 |
|        o     .  |
|       o o . . o |
|      B S = o + .|
|   . = + + o +.=o|
|    + . = . E.=+O|
|   . . = . ..X*=+|
|      o     ==B=.|
+----[SHA256]-----+
user@Admin-Gost:~/.ssh$ ls
config  id_rsa  id_rsa.pub  known_hosts  known_hosts.old
```
in here id_rsa is a private key
and id_rsa.pub is a public key

### how to connect server with public key

Connect to a remote server, Creat authorized_keys .ssh file in remote server and 
``` bash
$ touch authorized_key #in .ssh/
```
Past the Public key in authorized_keys 
you can easyly login without password 

To check what is going while connecting to remote server 
```
$ ssh -v <user@[IP]>
```
```
user@Admin-Gost:~/.ssh$ ssh nanu
Enter passphrase for key '/home/gost/.ssh/id_rsa':          # User Passphrase for securty keys
```
```
ssh-copy-id -i ~/.shh/id_rsa.pub root@[IP]  # -i for input file 
```
It will automatically created .ssh in remote server 
add the public key in authorized_keys file

## 4) Managing SSH keys

```
ssh-keygen -t ed25519 -C "gost" # more seurity, -t for type, -C for commant
```

- -t ed25519 is more secrity and normal ssh keys
- -C is for comment in the end of the Public key, if don't enter it will take default ( your user name and computer name by default) # it very usefull in finding keys 

```
$ ssh -i ~/.ssh/<name id> root@[IP]  # -i input file, using privat key to login
```
it will prompit for the passphrase 





## 5) SSH Server Configuration


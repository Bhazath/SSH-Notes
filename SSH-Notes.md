#  SSH
---

OpenSSH is the tool of choice for managing Linux installations remotely - and is indispensable in DevOps, Cloud, System Administration, Hosting, and more. Since it's so widely used, you should definitely learn it. In this video, I go over all the basics you need to use OpenSSH in your workflow. This includes understanding the difference between the client and server binaries, how to connect, config files, keys, and more!

## Connecting to a server via OpenSSH
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
Known_hosts file is where the ssj finger print are stored 






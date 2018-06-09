---
layout: post
title: "Configure SSH"
date: 2018-06-09 12:09:00 +0800
summary: configure ssh
slug: configure-ssh
categories: linux
---
_Problem_

You work with a remote server (linux machine) everyday, and you're tired of typing passwords over and over again. Even worse, sometimes you just can't get password right! 

_Solution_

Suppose your local machine is MacOS or Linux. First, you need to generate a pair of SSH key in the local 
```bash
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/hu/.ssh/id_rsa): # press Enter
Enter passphrase (empty for no passphrase): # press Enter
Enter same passphrase again: # press again
Your identification has been saved in .ssh/id_rsa
Your public key has been saved in .ssh/id_rsa.pub.
```
The private key is `.ssh/id_rsa` and public key is `.ssh/id_rsa.pub`. Now copy your public key to remote machine. You will be prompted to enter the password. Here `-i .ssh/id_rsa.pub` can be omitted because it is the "standard" ssh key.

```bash
ssh-copy-id user@host -i .ssh/id_rsa.pub
```

Your public key has been copied to the `~/.ssh/authorized_keys` file on the remote server. Now create an alias for the server in `~/.ssh/config`
```config
Host *
   ServerAliveInterval 300
   ServerAliveCountMax 15
   
Host mars
    HostName <ip_address>
    Port <port_number>
    User root
```

Next time you want to log in the server, simply type
```bash
ssh mars
```

To copy a file to the server, type
```bash
scp /path/to/file mars:/path/on/remote/machine
```




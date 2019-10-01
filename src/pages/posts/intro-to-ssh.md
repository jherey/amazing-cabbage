---
title: Intro to SSH
date: 2019-10-01T18:03:03.950Z
thumb_img_path: /images/ssh.png
template: post
---
If you're one of many software developers that have come across "ssh into a server" and have no idea what that means, then this post is for you. I think other people have this experience, I'll be reading a tutorial or watching a series and the tutor just asks you to SSH into your remote server and I'm like "what does that even mean?", you'll be absolutely correct if you guessed that was the end of the tutorial for me. 

This tutorial will try to explain what it means and why you should use it. I'll try to keep this as simple as possible so that anybody can read this and get a little grasp about what SSH means. I'll like to state that if you're looking for a deep explanation of SSH, then this post isn't for you. 

## What is SSH?

SSH stands for Secure Shell (Protocol). It's a network protocol (set of rules) to achieve secure login from one computer to another (server) over an unsecured network. It enables network administrators or developers to execute shell commands on their server directly from your local computer. SSH uses the Transmission Control Protocol (TCP). TCP simply means a connection stays alive until both applications have finished exchanging data or message requests. SSH can transmit data, commands and files.

Connections can be secured with password authentication or an asymmetrical key system i.e using private and public keys.

There are two parts of an SSH key:

1. **_Private key:_** it is very important that this is kept secret, it should never leave your computer. A good way to keep this safe is using a passphrase on the private key. The private key is used to decipher the public key.
2. **_Public key:_** as the name implies, this can be put anywhere. This is basically the key you put on remote servers like Digital Ocean, GitHub, AWS, etc so it knows who is talking to. The public key can only be unlocked by the private key.



## How to get your SSH Key?

On Mac and Linux, ssh is pre-installed into the terminal but on Windows, you'll have to install a third party ssh client like [putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). 

To get your ssh key, open your terminal and run:

```
cat ~/.ssh/id_rsa.pub 
```

If you don't know the location of your key, run:

```
ssh-agent sh -c 'ssh-add; ssh-add -L'
```

If no key is returned, you'll have to generate new keys using:

```
ssh-keygen
```



## How it works?

This will be a high level explanation of how SSH connections work.

![how ssh works image](/images/how_ssh_works.png)

* The client sends a request (initiates a TCP connection) to a server using an IP address or public domain.
* Server responds with the public key it has so the client, having the private key can verify it's the intended host.
* If successfully verified, connection is established. 



## Basic SSH Commands

* To connect to a server


```
ssh user@serverip
```

* Creates an ssh key pair for authentication


```
ssh-keygen
```

* For running terminal commands:


```
ssh hostname command
```

```
e.g ssh mysite.com ls tmp
```



## Why use SSH?

* _**Secure File Transfer:**_ ssh allows you copy files from your server to your local machine securely and vice versa. This is really important for secret data like login credentials, environment variables, etc.
* **_Same linux commands:_** you don't have to cram different set of commands. One can run commands easily on your remote server like it's a local one.
* Secure or confidential user access: a client can be assured of secured connection to a remote server even in an unsecured network.
* **_Non-platform agnostic:_** it can be used on any major OS platform like Linux, Windows and Mac.

In conclusion, this is just the basics as SSH is so much deeper than the explanation I've given here, I've tried to keep it as basic as possible. I'll advise you search online to further your understanding and learn how it works under the hood, algorithm used, etc. I know many of you are anxious saying "Jerry enough of the sermon, I want to get my hands dirty". I'm begging for some patience as it'll all come together when I walk you through deploying a Node.js server and "sshing" into a Digital Ocean droplet.

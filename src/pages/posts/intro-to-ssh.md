---
title: Intro to SSH
date: 2019-10-01T18:03:03.950Z
thumb_img_path: /images/ssh.png
template: post
---
If you're one of many software developers that have come across _"ssh into a server"_ and have no idea what that means, then this post is for you. I think other people have this experience where you'll be reading a tutorial or watching a series and the tutor tells you to SSH into your remote server and I'm like _"what does that even mean?"_, people just assume you know it. You'll be absolutely correct if you guessed that was the end of the tutorial for me. 

This post will try to explain what it means and why you should use it. I'll try to keep this as simple as possible so anyone can read this and get a little grasp of what SSH means. I'll like to state that if you're looking for a deep explanation of SSH, then this post isn't for you. 



## What is SSH?

SSH stands for Secure Shell (Protocol). It's a network protocol (set of rules) to achieve secure login from one computer to another (server) over an unsecured network. It enables network administrators or developers to execute shell commands on their servers directly from a local computer. SSH uses the Transmission Control Protocol (TCP). TCP simply means a connection stays alive until both applications have finished exchanging data or message requests. SSH can transmit data, commands, and files.

Connections can be secured with password authentication or an asymmetrical key system i.e using private and public keys.

There are two parts of an SSH key:

1. **_Private key:_** it is very important that this is kept a secret, it should never leave your computer. A good way to keep this safe is by using a passphrase on the private key. The private key is used to decipher the public key.
2. **_Public key:_** as the name implies, this is the key you copy to remote servers. The public key can only be deciphered by the private key associated with it.

From cloud services like AWS, GCP, Digital Ocean to git versioning systems like GitHub and Gitlab, ssh keys can be added to them for secured connection to deploy or push code.



## How to get your SSH Key?

On Mac and Linux, ssh is pre-installed into the terminal but on Windows, you'll have to install a third-party ssh client like [putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). 

To get your ssh key, open your terminal and run:

```
cat ~/.ssh/id_rsa.pub 
```

If you don't know the location of your key, run:

```
ssh-agent sh -c 'ssh-add; ssh-add -L'
```

If no key is returned, generate new a new key using:

```
ssh-keygen
```



## How it works?

This will be a high level explanation of how SSH connections work.

![how ssh works image](/images/how_ssh_works.png)

* The client sends a request (initiates a TCP connection) to a server using an IP address or public domain (website address).
* The server responds with the public key it has so the client, having the private key can verify it's the intended host.
* If successfully verified, a connection is established. 

The ssh-agent handles all of the authentication and the app making the request doesn't bother about it. 



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
e.g ssh mysite.com ls <folder_name>
```



## Why use SSH?

* _**Secure File Transfer:**_ ssh allows file copying from a server to your local machine securely and vice versa. This is really important for secret data like login credentials, environment variables, etc.
* **_Linux commands:_** you don't have to cram different sets of commands. One can run commands easily on your remote server like it's a local one.
* **Secure or confidential user access:** a client can be assured of a secured connection to a remote server even in an unsecured network.
* **_Multiple platform support:_** it can be used on any major OS platforms like Linux, Windows, and Mac.

In conclusion, this is just the basics as SSH is so much deeper than the explanation I've given here, I've tried to keep it as basic as possible. I'll advise you search online to further your understanding and learn how it works under the hood, the algorithm used, etc. I know many of you are anxious saying _"Jerry, enough of the sermon, I want to get my hands dirty"_. I'm begging for some patience as it'll all come together when I walk you through deploying a Node.js server and _"sshing"_ into a Digital Ocean droplet.

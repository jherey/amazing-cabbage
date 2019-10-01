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

\* Screenshot sshing into a server.

There are two parts of an SSH key:

1. Private key: it is very important that this is kept secret, it should never leave your computer. A good way to keep this safe is using a passphrase on the private key.
2. Public key: as the name implies, this can be put anywhere. This is basically the key you put on remote servers like Digital Ocean, GitHub, AWS, etc so it knows who is talking to. The public key can only be unlocked by the private key.



## How to get your SSH Key?

On Mac and Linux, ssh is pre-installed but on Windows, you'll have to install an ssh client like [putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). 

## How it works?

1. The client sends a request with the public keys it has to a server.

2. 

## Basic SSH Commands

## Why use SSH?

* Secure File Transfer: ssh allows you copy files from your server to your local machine securely and vice versa. This is really important for secret data like login credentials, environment variables, etc.
* Same linux commands: you don't have to cram different set of commands. One can run commands easily on your remote server like it's a local one.
* Secure or confidential user access: a client can be assured of secured connection to a remote server even in an unsecured network.

In conclusion, this is just the basics as SSH is so much deeper than the explanation I've given here, I've tried to keep it as basic as possible. I'll advise you search online to further your understanding and learn how it works under the hood, algorithm used, etc. I know many of you are anxious saying "Jerry enough of the sermon, I want to get my hands dirty". I'm begging for some patience as it'll all come together when I walk you through deploying a Node.js server and "sshing" into a Digital Ocean droplet.

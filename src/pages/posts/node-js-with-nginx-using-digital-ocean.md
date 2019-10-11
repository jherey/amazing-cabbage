---
title: Node.js with Nginx using Digital Ocean
date: 2019-10-11T14:31:57.858Z
template: post
---
In this tutorial, I'll be walking you through how to deploy a Node.js app to Digital Ocean, using Nginx as a reverse proxy and add SSL certificates for security. For this tutorial, we'll be deploying a very simple Node.js project. Here is a [link](https://github.com/jherey/basic_node_project) to the project. If you don't have a Digital Ocean account, simply go to [digitalocean.com](www.digitalocean.com) or use my referral link  to create an account.Proceed to create a droplet. A droplet in Digital Ocean is just a server. I'll be using a Ubuntu server.

1. Create a ubuntu Digital Ocean droplet, I have a blog post [here](https://jherey.netlify.com/posts/creating-an-ubuntu-digital-ocean-droplet/) on how to create one. Copy the IP address of the droplet as we'll ssh into it.
   ![](/images/screenshot-2019-10-11-at-3.51.03-pm.png)
2. SSH into the server by running the command `ssh root@<ip_address>`. \
   You'll be asked to confirm your connection, type "yes".

   ![](/images/screenshot-2019-10-11-at-3.40.49-pm.png)
   For real world applications, I'll advise you create a new user and even delete the root user. I'll be using the root user as this is just a simple tutorial.
3. Update the ubuntu packages by running:\
   `apt update`\
   If you're using non-root user, remember you'll run the command with `sudo`.

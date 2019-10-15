---
title: Creating an Amazon EC2 Instance
date: 2019-10-15T13:22:26.516Z
thumb_img_path: /images/screenshot-2019-10-15-at-4.45.50-pm.png
template: post
---
This tutorial will be about creating an Amazon EC2 instance similar to my previous [article](https://jherey.netlify.com/posts/creating-an-ubuntu-digital-ocean-droplet/) on creating a Digital Ocean droplet.

EC2 is a virtual computing environment which provides resizable compute capacity in the cloud. It is designed to make scaling web applications easy. EC2 instances can be launched with a variety of operating systems like Ubuntu, Microsoft Server, CentOS, etc.

Steps

Create an account or sign-in to AWS.

Select a region where you want your server to be located. Regions help to optimise latency and minimise costs.

![](/images/screenshot-2019-10-15-at-4.31.50-pm.png)

1. Click on "Services" in the top-left corner and search for "EC2"

![](/images/screenshot-2019-10-15-at-2.31.39-pm.png)

Create an instance

![](/images/screenshot-2019-10-15-at-2.46.36-pm.png)

Choose an Amazon Machine Image (AMI): the Amazon Linux AMI is a very good option as it comes with a wide variety of installed programs like Python, Docker, etc. I'll be choosing a Ubuntu Server image as it's general purpose and goes with my other tutorial on Digital Ocean.

![](/images/screenshot-2019-10-15-at-2.57.29-pm.png)

Choose an Instance Type: this involves the number of CPU, processor type and speed you want your server to run on. I'll select the default t2.micro for demo. Click on "Next: Configure Instance Details"

![](/images/screenshot-2019-10-15-at-2.59.50-pm.png)

Configure Instance Details: I'll leave it as default and use just one instance. Click "Next: Add Storage".

Storage: this involves storage options and size for your EC2 instance. Click on "Next: Add Tags". Click on "Next: Configure Security Group"

Configure Security Group: here we define firewalls and network settings we want on the instance. I setup ssh, http and https connections. Click on "Add rule" to add new rules. Click on "Review and Launch".

![](/images/screenshot-2019-10-15-at-3.15.58-pm.png)

Review EC2 Instance: this is just a preview stage so you can take a final look at your instance before creation and edit if necessary. Yours should look exactly like this if you're following my steps. Click on "Launch".

![](/images/screenshot-2019-10-15-at-3.22.10-pm.png)

Create SSH keys: AWS will require you to create new ssh keys or use an existing one if you have that setup. I'll be creating a new ssh key. It'll automatically download the keys to your system. Click on "Download Key Pair" after creating a key pair name.

![](/images/screenshot-2019-10-15-at-4.19.05-pm.png)

Click on "Launch Instances".

Scroll down and click on "View Instances" on the bottom right corner of the page.

![](/images/screenshot-2019-10-15-at-4.24.10-pm.png)

Connecting to your EC2 Instance

Click on "Connect" so you can ssh into your ec2 instance

![](/images/screenshot-2019-10-15-at-4.37.29-pm.png)

Follow the instructions and you should successfully connect to your instance.

![](/images/screenshot-2019-10-15-at-4.41.23-pm.png)



Thanks for reading!
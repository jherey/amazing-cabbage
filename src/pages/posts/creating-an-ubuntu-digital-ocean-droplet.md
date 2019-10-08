---
title: Creating an Ubuntu Digital Ocean Droplet
date: 2019-10-08T09:24:51.308Z
thumb_img_path: /images/do.png
template: post
---


Why Digital Ocean?

Amazon Web Services (AWS), Microsoft Azure and Google Cloud Platform (GCP) are Cloud services that not only provide Linux hosting to deploy apps, but also auto scaling, load balancers, databases, etc. On the other hand, it's expensive, complex for a beginner to understand and mostly need some form of experience and expertise to navigate. I'll recommend them for very large enterprise applications because they provide everything an app will most likely need.

Digital Ocean (DO) is an Infrastructure as a Service (IaaS) platform. Digital Ocean is more beginner friendly and can serve small to medium scale enterprises efficiently. I've read where large scale apps have been built with DO and it has scaled well. It has a very simple pricing model and it's far less expensive compare to the cloud based platforms.

Why not Heroku? Heroku is a Platform as a Service (PaaS) that provides a hosting for your servers alone. Any other service an app needs like Redis, Kubernetes, MongoDB, etc will have to be gotten from a  different provider. Although it has PostgreSQL, it doesn't scale well. It's best for really small apps.

What is a Droplet?

> DigitalOcean Droplets are Linux-based virtual machines (VMs) that run on top of virtualized hardware. Each Droplet you create is a new server you can use, either standalone or as part of a larger, cloud-based infrastructure - 
>
> [digitalocean.com](digitalocean.com)
>
>

It's basically a server one can spin up to run any project, databases, containerization softwares like Docker, 

Steps to Create a Droplet

1. Create an account on Digital Ocean from [www.digitalocean.com](www.digitalocean.com) or use my [referral link](https://m.do.co/c/fdf6b4e6a1b9) which gives you $50 in credit to run apps for two months.
2. Click on "New Droplet" or "Create" on the top right and select "Droplets".
3. Choosing an Image: an image is the platform where we want our application to run on. Popular options are Ubuntu, Fedora and CentOS. Explaining what these Linux servers are is beyond the scope of this tutorial.
   ![choosing an image](/images/screenshot-2019-10-08-at-11.20.30-am.png)
4. Choosing a plan and pricing: I'll be selecting the Standard plan. If you'll be following this tutorial for learning purposes and don't need a CPU intensive and optimised server, then the Standard plan is your best bet. Also, select a pricing as small as possible so you don't use all of your credit. Here, I'm going for the $5 a month plan.
   ![](/images/screenshot-2019-10-08-at-11.32.03-am.png)
5. Choosing a region: pick a region closest to where you are or where your users will most likely be located. It might be a small time difference but it helps to deliver data faster if you're closer to the server.
   ![](/images/screenshot-2019-10-08-at-11.37.21-am.png)
6. Authentication: I'll be using ssh to login to my DO droplet, I'll advise you do the same. If you don't know anything about ssh keys, kindly refer to a previous [post](https://jherey.netlify.com/posts/intro-to-ssh/) of mine.
   ![authenticating with ssh](/images/screenshot-2019-10-08-at-11.56.45-am.png)
7.

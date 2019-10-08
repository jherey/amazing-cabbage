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
3. Choose an Image
   ![choosing an image](/images/screenshot-2019-10-08-at-11.20.30-am.png)

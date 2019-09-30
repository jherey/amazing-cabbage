---
title: Proxy and Reverse Proxy
date: 2019-09-30T13:49:39.133Z
thumb_img_path: /images/proxy.jpg
template: post
---
> From the Oxford Dictionary, the word "proxy" means the authority to represent someone else.

# **Proxy**

In programming, a proxy hides the identity of the client. The server does not know who the client is. A good example of proxies are ISPs (Internet Service Providers), when you make a request to "google.com", it gets to your ISP and your ISP sends the request to get the data, the server won't know who the client is or where the client is making the request from.

![](/images/screenshot-2019-09-30-at-4.14.07-pm.png)

## Advantages of a Proxy Server

* Blocking unwanted sites: ISPs use this to block some sites from being reached. This is used by the government and companies to block websites.
* Anonymity: the server cannot know who's making the requests.
* Caching: this can help performance as static files can be cached and sent back to clients when needed much faster.
* Geofencing: 

# Reverse Proxy

Reverse proxy on the other hand, the client doesn't know which server it is connecting to.

Based on whatever algorithm is used by the reverse proxy server, it selects the server to get the data from. A common algorithm is the Round Robin Algorithm (just loop through the available servers and direct requests to each individual server). These activities are internal to the system and the client won't need to bother which server is returning the data.

![](/images/reverse_proxy.png)

## Advantages of Reverse Proxy

* **Load Balancing:** a big advantage of using reverse proxies is load balancing requests to different servers. This is really important in today's world where speed and performance are in the forefront of software development.
* **Canary deployment:** this involves running multiple versions of your app and routing specific users to those versions. This is very helpful when pushing out big changes to users.
* **Caching:** this is a complex architecture to accomplish as it must be done with care, else clients get outdated data. A simple technique used is time-based caching.
* **Isolating Internal Traffic:** the servers can be configured to run containers, virtual machines, different ports, etc, no one really cares. It completely isolates the backend logic from the users. The ports can be made to run only internally and not expose them to the outside world, it makes deployment of servers very flexible.
* **Security**

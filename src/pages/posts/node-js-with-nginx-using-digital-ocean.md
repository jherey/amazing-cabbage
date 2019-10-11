---
title: Node.js with Nginx using Digital Ocean
date: 2019-10-11T14:31:57.858Z
template: post
---
In this tutorial, I'll be walking you through how to deploy a Node.js app to Digital Ocean, using Nginx as a reverse proxy, using firewalls, and SSL certificates for security. I'll be deploying a very simple Node.js project ([link here](https://github.com/jherey/basic_node_project)).

## **Steps**

1. **Create a droplet:** I have a blog post [here](https://jherey.netlify.com/posts/creating-an-ubuntu-digital-ocean-droplet/) on how to create one. Copy the IP address of the droplet as we'll ssh into it.
![](/images/screenshot-2019-10-11-at-3.51.03-pm.png)

2. **SSH into the server** 

```
ssh root@<ip_address>
```

You'll be asked to confirm your connection, type **_"yes"_**.


![ssh into droplet](/images/screenshot-2019-10-11-at-3.40.49-pm.png)

3. **Creating a new user:** for big, real world applications, I'll advise you create a new user and even delete the root user for security reasons, so no one will have root access to your server. I'll be using the root user as this is just a simple tutorial.

4. **Update packages:** since it's a fresh ubuntu server, we'll need to update the packages.

```
apt update
```

If you're using non-root user, remember you'll run the command with `sudo`.

5. **Install Node:** 

```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -  # get the latest version of Node.js. This uses curl to access the url and pipes it to bash to use the standard output. The flag -s (silent) allows for few log outputs in the console and L (location) jumps through http redirects. 
```

```
apt install nodejs  # install node
```

\
At this point you should be able to successfully check your npm and node versions.

![node version](/images/screenshot-2019-10-11-at-4.51.53-pm.png)

6. **Add project to server:** You can clone your repo using ssh or https, I'll be using https as it'll get long adding GitHub ssh keys to our server.

```
git clone <project_url>
```

![cloning project](/images/screenshot-2019-10-11-at-4.57.53-pm.png)

At this point, you should be able to start your application and go to your browser to see it working with your server IP.

```
node index.js
```

![app live](/images/screenshot-2019-10-11-at-5.05.58-pm.png)

7. **PM2 Setup:** We'll be adding PM2 so we can run our application as a background process, right now we can't run any commands without stopping the application, you can check pm2's docs [here](http://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/).

```
npm install -g pm2 # install pm2pm2 start <entry_file> # start app
```

Your app should be back online with the terminal console free.

![pm2 start](/images/screenshot-2019-10-11-at-5.31.00-pm.png)

```
pm2 startup ubuntu # Restart app when server reboots. This ensures that whenever your server restarts, your app restarts as well.
```

8. **Enable firewall**

```
ufw enable # enable firewallufw allow ssh  # this allows the firewall accept ssh connections (port 22)ufw allow http # allow port 80 to be accessedufw allow https # allow port 443
```

![](/images/screenshot-2019-10-11-at-5.51.37-pm.png)

9. **Setup Nginx:** Nginx is a reverse proxy web server that allows us access our app with just the IP (in my case 167.99.85.114). Http and https requests are automatically suffixed by the appropriate port i.e 80/443.

```
nano /etc/nginx/sites-available/default
```

_Scroll down to location and add the following_

```
proxy_pass http://localhost:3000; # your aplication port
```

```
proxy_http_version 1.1;
```

```
proxy_set_header Upgrade $http_upgrade;
```

```
proxy_set_header Connection 'upgrade';
```

```
proxy_set_header Host $host;
```

```
proxy_cache_bypass $http_upgrade;
```

If you've got a domain name, add it to the "_server_name"_ field. This will look like:

`server_name jeremiaholufayo.com www.jeremiaholufayo.com`

Exit by pressing _Ctrl + X_ and then _Enter_ on Mac.

![](/images/screenshot-2019-10-11-at-6.09.13-pm.png)

```
nginx -t # Verify if your config is correctservice nginx restart # restart nginx to use new data
```

10. **Add Domain to Digital Ocean:** if you've got a domain, you'll need to add it by clicking on the Networking button by the left tab. Add your domain, then go ahead to create the record

![creating a record](/images/screenshot-2019-10-11-at-6.57.43-pm.png)

 Proceed to your domain service provider to add the DNS provided by Digital Ocean; **_ns1.digitalocean.com, ns2.digitalocean.com, ns3.digitalocean.com._**\
11. **Adding SSL Certificates:** 

```
add-apt-repository ppa:certbot/certbot
```

```
apt-get update
```

```
apt-get install python-certbot-nginx
```

```
certbot --nginx -d yourdomain.com -d www.yourdomain.com
```

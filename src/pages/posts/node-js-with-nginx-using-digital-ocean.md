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
4. Then we install Node in our server.\
   Firstly, get the latest version of Node.js by running \
   `curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`\
   `apt install nodejs`\
   The first command uses curl to access the url and pipes it to bash to use the standard output. The flag -s (silent) meaning few log outputs in the console and L (location) means jump through http redirects. \
   At this point you should be able to successfully check your npm and node versions.
   ![](/images/screenshot-2019-10-11-at-4.51.53-pm.png)
5. Add project to server. You can clone your repo using ssh or https, I'll be using https as it'll get long adding GitHub ssh keys to our server. Run:\
   git clone <project_url>
   ![](/images/screenshot-2019-10-11-at-4.57.53-pm.png)
6. At this point, you should be able to start your application and go to your browser to see it working with your server IP.
   ![](/images/screenshot-2019-10-11-at-5.05.58-pm.png)
7. Install PM2. We'll be adding PM2 so we can run our application as a background process, right now we can't run any commands without stopping the application, you can check the docs [here](http://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/). Run:\
   npm install -g pm2\
   pm2 start <entry_file>\
   Your app should be back online with the terminal console free.
   ![](/images/screenshot-2019-10-11-at-5.31.00-pm.png)
8. Restart app when server reboots. This ensures that whenever your server restarts, your app restarts as well.\
   pm2 startup ubuntu
9. Enable firewall\
   ufw enable\
   ufw allow ssh  # this allows the firewall accept ssh connections (port 22)\
   ufw allow http # allow port 80 to be accessed\
   ufw allow https # allow port 443
   ![](/images/screenshot-2019-10-11-at-5.51.37-pm.png)
10. Setup Nginx. Nginx is a reverse proxy that allows us access our app with just the IP (in my case 167.99.85.114)\
    nano /etc/nginx/sites-available/default
    Scroll down to location and add the following
    proxy_pass http://localhost:3000; # your aplication port
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    ![](/images/screenshot-2019-10-11-at-6.09.13-pm.png)
    \
    Verify if your config is correct by running:\
    nginx -t
11.

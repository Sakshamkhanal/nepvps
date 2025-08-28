---
title: "How to Install Nginx on Ubuntu 20.04"
date: 2025-08-18
author: "Saksham"
description: "Learn how to install and configure Nginx on Ubuntu 20.04, including setting up server blocks and adjusting firewall settings."
categories: ["Web Server"]
tags: ["Nginx", "Ubuntu 20.04", "Web Server", "Linux"]
featured_image: "/images/blog/nginx.jpg"
---

{{< toc >}}

## Introduction

Nginx is a high-performance web server and reverse proxy server. It's widely used for serving static content and as a reverse proxy for dynamic content. This guide will walk you through installing Nginx on Ubuntu 20.04, configuring server blocks, and adjusting firewall settings.

## Prerequisites

Before you begin, ensure you have:

- A server running Ubuntu 20.04.
- A non-root user with `sudo` privileges.
- A domain name pointed to your server's IP address (optional but recommended).

## Step 1: Install Nginx

Start by updating your package index:

```bash
sudo apt update
```

Then, install Nginx:

```bash
sudo apt install nginx
```

Once installed, Nginx should start automatically. Verify its status:

```bash
sudo systemctl status nginx
```

## Step 2: Adjust the Firewall

If you're using UFW (Uncomplicated Firewall), allow 'Nginx Full' to permit both HTTP and HTTPS traffic:

```bash
sudo ufw allow 'Nginx Full'
```

Check the status of UFW to confirm the changes:

```bash
sudo ufw status
```

## Step 3: Check Your Web Server

To ensure Nginx is serving content, open a web browser and navigate to your server's IP address. You should see the default Nginx welcome page.

Alternatively, use `curl` to check from the command line:

```bash
curl http://localhost
```

## Step 4: Set Up Server Blocks

Server blocks allow you to host multiple websites on a single server. To create a new server block:

1. Create a directory for your domain:

```bash
sudo mkdir -p /var/www/your_domain/html
```

2. Set the correct permissions:

```bash
sudo chown -R $USER:$USER /var/www/your_domain/html
```

3. Create a sample `index.html` file:

```bash
nano /var/www/your_domain/html/index.html
```

Add the following content:

```html
<html>
    <head>
        <title>Welcome to your_domain!</title>
    </head>
    <body>
        <h1>Success! The your_domain server block is working!</h1>
    </body>
</html>
```

4. Create a new server block configuration file:

```bash
sudo nano /etc/nginx/sites-available/your_domain
```

Add the following configuration:

```nginx
server {
    listen 80;
    listen [::]:80;

    root /var/www/your_domain/html;
    index index.html;

    server_name your_domain www.your_domain;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

5. Enable the server block by creating a symbolic link:

```bash
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
```

6. Test the Nginx configuration for syntax errors:

```bash
sudo nginx -t
```

7. Reload Nginx to apply the changes:

```bash
sudo systemctl reload nginx
```

## Conclusion

You've successfully installed Nginx on Ubuntu 20.04 and set up a basic server block. From here, you can further configure Nginx to serve dynamic content, set up SSL with Let's Encrypt, or deploy applications.

For more detailed information, refer to the original DigitalOcean tutorial: [How to Install and Configure Nginx on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04).

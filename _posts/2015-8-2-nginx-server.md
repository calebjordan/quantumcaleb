---
title: Setting up NGINX for Jekyll
layout: post
tags: Software Jekyll
---

To setup an nginx server to host your static jekyll blog, make sure apache is turned off. Edit `/etc/nginx/nginx.conf', and add the following **inside** the http section. This is assuming your files are located in /var/www

```
server {

    ## Give Domain name
    server_name quantumcaleb.com www.quantumcaleb.com;

    ## Define custom path for Nginx site log
    access_log /var/log/nginx/example.com-access.log;
    error_log /var/log/nginx/example.com-error.log;

    ## Give absolute path of Web root where your website files/dir are saved
    root /var/www;

    ## Define the index file
    index index.html;
    autoindex off;

    ## Setting Compression
  
    gzip on;
    gzip_disable "msie6";
    gzip_min_length 1100;
    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_buffers 16 8k;
    gzip_http_version 1.1;
    gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;

    ## Define 404 pages URL
    location / {
     try_files $uri $uri/ =404; 
   }

    # Disable favicon.ico logging
    location = /favicon.ico {
        log_not_found off;
        access_log off;
    }

    # Allow robots and disable logging
    location = /robots.txt {
        allow all;
        log_not_found off;
        access_log off;
    }

    # Disable static content logging and set cache time to max
    location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
        expires 365d;
        log_not_found off;
    }

    # Deny access to htaccess and htpasswd files
    location ~ /\.ht {
        deny  all;
    }
}
```
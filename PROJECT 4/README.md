
# WEB STACK IMPLEMENTATION - DEPLOYING LEMP STACK (Linux, NGINX, MySQL and PHP) ON AWS

A LEMP Stack application is an application which as opposed to a LAMP stack application makes use of Nginx as the web server for hosting the web application. NGINX is an open source software for web serving, reverse proxying, caching, load balancing, media streaming, and more.

## Creating an Ubuntu EC2 Instance
Login to AWS Cloud Service console and create an Ubuntu EC2 instance. The virtual machine is a linux operating system which serves as the backbone for the LEMP Stack web application. 

![ec2 instance launch ](Images%5Cec2_launch_instance.PNG)

## Installing NGINX
Run a `sudo apt update` to download package information from all configured sources.

![sudo_update](Images%5Capt_update.PNG)

Then use the command `sudo apt install nginx -y` to install nginx

![install_nginx](Images%5Cinstall_nginx.PNG)


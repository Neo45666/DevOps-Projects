# Implementing LVM on LInux servers (Web and Database servers)
This project involves being tasked to prepare storage infrastructure on two Linux servers and implement a basic web solution using WordPress. WordPress is a free and open-source content management system written in PHP and paired with MySQL or MariaDB as its backend Relational Database Management System (RDBMS).

This project consist of two parts:

1. Configure storage subsystems for Web and Database servers based on Linux OS. The focus of this part is to provide practical experience of working with disks, partitions and volumes in Linux.

2. Install Wordpress and connect it to a remote MySQL database server. This part of the project will solidify your skills of deploying Web and DB tiers of Web solution. 

## Three-tier Architecture

Three-tier Architecture is a client-server software architecture pattern that comprise of 3 seperate layers.

1. Presentation Layer: This is the user interface such as the client server or browser on your laptop.

2. Business Layer: This is the backend program that implements business logic. Application or Webserver.

3. Data Access or Management Layer: This is the layer for computer data storage and data access. Database server or File system Server such as FTP server or NFS Server.

To implement LVM on Linux xservers follow the steps:

Step 1 - Prepare a Web Server

Launch and Ec2 instance that will serve as "Web Server". Create 3 volumes in the same AZ as your Web Server EC2, each of 10GB.

2. Attach all three volumes one by one to your Web Server EC2 instance.

3. Use `lsblk` command to inspect what block devices are attached to the server. All devices in Linux reside in /dev/ directory. Inspect it with `ls /dev/` and make sure you see all 3 newly created block devices there - their names will likely be `xvdf`,  `xvdf` , `xvdg`

4. Use `df -h` command to see all amounts and free space on your server. 

5. Use `gdisk` utility to create a single partition on each of the 3 disks.


`sudo gdisk /dev/xvdf`




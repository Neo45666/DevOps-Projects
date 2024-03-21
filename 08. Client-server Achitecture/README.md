# Implement a Client-Sever Architecture using MySQL Database Management System (DBMS)

This project explores the intricacies of client-server architecture using MySQL as the RDBMS. 
Client-Server refers to an architecture in which two or more computers are connected together over a network to send and receive requests between one another. In their communication each machine has its role: the machine sending requests is usually reffered to as "Client" and the machine responding (sering) is called "Server". 
A simple diagram of Web Client-Server architecture is presented below: 

![Client-Server](./images/Client-Server_illustration.PNG)

In the example above, a machine that is trying to access a Web site using a Web browser or simply ‘curl’ command is a client and it sends HTTP requests to a Web server (Apache, Nginx, IIS or any other) over the Internet. If we extend this concept further and add a Database Server to our architecture, we can get this picture

![](./images/Client-Server_illustration.PNG)

The Web Server has a role of a "Client" that connects and reads/writes to/from a Database (DB) Server (MySQL, MongoDB, Oracle, SQL Server or any other), and the communication between them happens over a Local Network (it can also be an Internet connection, but it is a common practice to place Web Server and DB Server close to each other in a local network).
Essentially, it is sending requests to the remote server, and in turn, would be expecting some kind of response from the remote server. Let’s take a very quick example and see Client-Server communicatation in action. Open up your Ubuntu or Windows terminal and run the curl command:

`curl -Iv www.bing.com`

Note: If your Ubuntu does not have ‘curl’, you can install it by running sudo apt install curl In this example, your terminal will be the client, while www.bing.com will be the server.

See the response from the remote server in the below output. You can also see that the requests from the URL are being served by a computer with an IP address 204.79.197.200 on port 80

![](./images/server_port_80.PNG)

## TO DEMONSTRATE A BASIC CLIENT-SERVER USING MYSQL RELATIONAL DATABASE MANAGEMENT SYSTEM (RDBMS), FOLLOW THE BELOW INSTRUCTIONS:

1. Create and configure two Linux-based virtual servers (EC2 instances in AWS).

`Server A name - mysql-server` and `Server B name - mysql-client`

![](./images/mysql_instances.PNG)

On mysql-server Linux Server install MySQL Server software.
`sudo apt update`

Then install the mysql-server package:
`sudo apt install mysql-server`

Ensure that the server is running using the systemctl command:
`sudo systemctl start mysql.service`

`sudo systemctl status mysql.service`

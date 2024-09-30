When we access a website in the Internet we use an URL and we do not really know how many servers are out there serving our requests, this complexity is hidden from a regular user, but in case of websites that are being visited by millions of users per day (like Google or Reddit) it is impossible to serve all the users from a single Web Server (it is also applicable to databases, but for now we will not focus on distributed DBs).

Each URL contains a domain name part, which is translated (resolved) to IP address of a target server that will serve requests when open a website in the Internet. Translation (resolution) of domain names is perormed by DNS servers, the most commonly used one has a public IP address 8.8.8.8 and belongs to Google. You can try to query it with nslookup command:
`nslookup 8.8.8.8`
`Server:  UnKnown`
`Address:  103.86.99.99`

`Name:    dns.google`
`Address:  8.8.8.8`

When you have just one Web server and load increases - you want to serve more and more customers, you can add more CPU and RAM or completely replace the server with a more powerful one - this is called "vertical scaling". This approach has limitations - at some point you reach the maximum capacity of CPU and RAM that can be installed into your server.

Another approach used to cater for increased traffic is "horizontal scaling" - distributing load across multiple Web servers. This approach is much more common and can be applied almost seamlessly and almost infinitely (you can imagine how many server Google has to serve billions of search requests).

Horizontal scaling allows to adapt to current load by adding (scale out) or removing (scale in) Web servers. Adjustment of number of servers can be done manually or automatically (for example, based on some monitored metrics like CPU and Memory load).

Property of a system (in our case it is Web tier) to be able to handle growing load by adding resources, is called ["Scalability"](https://en.wikipedia.org/wiki/Scalability).

In our set up in Project-7 we had 3 Web Servers and each of them had its own public IP address and public DNS name. A client has to access them by using different URLs, which is not a nice user experience to remember addresses/names of even 3 server, let alone millions of [Google servers](https://en.wikipedia.org/wiki/Google_data_centers).

In order to hide all this complexity and to have a single point of access with a single public IP address/name, a [Load Balancer](https://en.wikipedia.org/wiki/Load_balancing_(computing)) can be used. A Load Balancer (LB) distributes clients' requests among underlying Web Servers and makes sure that the load is distributed in an optimal way.

**Side Self Study:**
Read about different [Load Balancing concepts](https://www.nginx.com/resources/glossary/load-balancing/) and difference between [L4 Network LB](https://www.nginx.com/resources/glossary/layer-4-load-balancing/) and [L7 Application LB](https://www.nginx.com/resources/glossary/layer-7-load-balancing/).

Let us take a look at the updated solution architecture with an LB added on top of Web Servers (for simplicity let us assume it is a software L7 Application LB, for example - [Apache](https://httpd.apache.org/docs/2.4/mod/mod_proxy_balancer.html), [NGINX](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/) or [HAProxy](http://www.haproxy.org))

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project8/Tooling-Website-Infrastructure-wLB.png" width="936px" height="550px">

In this project we will enhance our **Tooling Website** solution by adding a Load Balancer to disctribute traffic between Web Servers and allow users to access our website using a single URL.

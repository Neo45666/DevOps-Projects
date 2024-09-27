# DEVOPS TOOLING WEBSITE SOLUTION
## Side Self Study

Read about Network-attached storage (NAS), Storage Area Network (SAN) and related protocols like NFS, (s)FTP, SMB, and iSCSI. Explore what Block-level storage is and how it is used by Cloud Service providers, and know the difference from Object storage. On the example of AWS services understand the difference between Block Storage, Object Storage and Network File System.

## Setup and technologies for this project
As a member of a DevOps team, you will implement a tooling website solution which makes access to DevOps tools within the corporate infrastructure easily accessible. In this project you will implement a solution that consists of following components:

1. Infrastructure: AWS
2. Webserver Linux: Three Red Hat Enterprise Linux 8
3. Database Server: One Ubuntu 20.04 + MySQL
4. Storage Server: One Red Hat Enterprise Linux 8 + NFS Server
5. Programming Language: PHP
6. Code Repository: GitHub On the diagram below you can see a common pattern where several stateless Web Servers share a common database and also access the same files using Network File Sytem (NFS) as a shared file storage. Even though the NFS server might be located on a completely separate hardware – for Web Servers it look like a local file system from where they can serve the same files.

![nfs_achitecture](./images/nfs_achitecture.PNG)

It is important to know what storage solution is suitable for what use cases, for this – you need to answer the following questions: what data will be stored, in what format, how this data will be accessed, by whom, from where, how frequently, etc. Based on this you will be able to choose the right storage system for your solution.

In this project you will implement a solution that consists of following components:

1. **Infrastructure**: AWS  
2. **Webserver Linux**: Red Hat Enterprise Linux 8  
3. **Database Server**: Ubuntu  20.04 + MySQL
4. **Storage Server**: Red Hat Enterprise Linux 8 + NFS Server 
5. **Programming Language**: PHP   

## For Rhel 8 server use this ami `RHEL-8.6.0_HVM-20220503-x86_64-2-Hourly2-GP2 (ami-035c5dc086849b5de)`

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/AMI-prj7.PNG" width="936px" height="550px">

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/public+images+prj7.PNG" width="936px" height="550px">

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/search+for+AMI.PNG" width="936px" height="550px">

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/launch+instance+from+template.PNG" width="936px" height="550px">

![](./images/AMI-prj7.PNG)

![](./images/public%20images%20prj7.PNG) ![](./images/search%20for%20AMI.PNG)

![](./images/launch%20instance%20from%20template.PNG)

On the diagram below you can see a common pattern where several stateless Web Servers share a common database and also access the same files using [Network File Sytem (NFS)](https://en.wikipedia.org/wiki/Network_File_System) as a shared file storage. Even though the NFS server might be located on a completely separate hardware - for Web Servers it look like a local file system from where they can serve the same files.

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/Tooling-Website-Infrastructure.png" width="936px" height="550px">

It is important to know what storage solution is suitable for what use cases, for this - you need to answer following questions: what data will be stored, in what format, how this data will be accessed, by whom, from where, how frequently, etc. Base on this you will be able to choose the right storage system for your solution. 


## STEP 1 – PREPARE NFS SERVER

1. Spin up a new EC2 instance with RHEL Linux 8 Operating System.
   Based on your LVM experience from the three-tier architecture project, Configure LVM on the Server.

   However, Instead of formatting the disks as ext4, you will have to format them as xfs
![](./images/lvmsetup1.PNG)

![](./images/lvmsetup2.PNG)

![](./images/lvmsetup3.PNG)

![](./images/lvmsetup4.PNG)

![](./images/lvmsetup6.PNG)

2. Based on your LVM experience from [Project 6](https://dareyio-pbl-progressive.readthedocs-hosted.com/en/latest/project6.html), Configure LVM on the Server.

- Instead of formating the disks as `ext4` you will have to format them as [`xfs`](https://en.wikipedia.org/wiki/XFS)

- Ensure there are 3 **Logical Volumes**. `lv-opt` `lv-apps`, and `lv-logs`

- Create mount points on `/mnt` directory for the logical volumes as follow:
     Mount `lv-apps` on `/mnt/apps`  - To be used by webservers
     Mount `lv-logs` on  `/mnt/logs` - To be used by webserver logs
     Mount `lv-opt`  on  `/mnt/opt`  - To be used by Jenkins server in [Project 8](https://dareyio-pbl-progressive.readthedocs-hosted.com/en/latest/project8.html)

4. Install NFS server, configure it to start on reboot and make sure it is u and running

```
sudo yum -y update
sudo yum install nfs-utils -y
sudo systemctl start nfs-server.service
sudo systemctl enable nfs-server.service
sudo systemctl status nfs-server.service
```

5. Export the mounts for webservers' `subnet cidr` to connect as clients. For simplicity, you will install your all three Web Servers inside the same subnet, but in production set up you would probably want to separate each tier inside its own subnet for higher level of security.
To check your `subnet cidr` - open your EC2 details in AWS web console and locate 'Networking' tab and open a Subnet link:

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/EC2_subnet.png" width="936px" height="550px">


Make sure we set up permission that will allow our Web servers to read, write and execute files on NFS:
```
sudo chown -R nobody: /mnt/apps
sudo chown -R nobody: /mnt/logs
sudo chown -R nobody: /mnt/opt

sudo chmod -R 777 /mnt/apps
sudo chmod -R 777 /mnt/logs
sudo chmod -R 777 /mnt/opt

sudo systemctl restart nfs-server.service
```

Configure access to NFS for clients within the same subnet (example of Subnet CIDR - `172.31.32.0/20` ):

```
sudo vi /etc/exports

/mnt/apps <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)
/mnt/logs <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)
/mnt/opt <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)

Esc + :wq!

sudo exportfs -arv
```

6. Check which port is used by NFS and open it using Security Groups (add new Inbound Rule)

```
rpcinfo -p | grep nfs
```

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/nfs_port.png" width="936px" height="550px">


**Important note:** In order for NFS server to be accessible from your client, you must also open following ports: TCP 111, UDP 111, UDP 2049

<img src="https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/project7/nfs_port_open.png" width="936px" height="550px">






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








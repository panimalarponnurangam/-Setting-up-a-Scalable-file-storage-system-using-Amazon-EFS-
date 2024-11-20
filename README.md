 # EX:04 SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
  ## AIM
  To set up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones, enabling shared access to data.
  
## PROBLEM STATEMENT
 This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.

## ALGORITHM
 ### Steps 1: Launch Two EC2 Instances in Different Availability Zones
Go to the EC2 service in the AWS Management Console.
Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.
Assign each instance a security group that allows NFS access on port 2049.

 
 ### Steps 2: Set up a security group for EFS.
Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.
Attach this security group to the EFS file system to permit access from both instances.
 
 ### Steps 3: Create an EFS File System
In the AWS Console, navigate to the EFS service and select Create file system.
Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.
Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).

 
 ### Steps 4: Configure EC2 Instances to Access EFS
 ## INSTANCE 1
SSH into the first EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory and create a sample file:

## INSTANCE 2
SSH into the second EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory, list files, and view the content of the file created on Instance 1
## COMMANDS
## EC2 INSTANCE 1
````
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
````
## EC2 INSTANCE 2
````
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  # Verify shared access by reading content created in Instance 1
````


## OUTPUT
### REG NUMBER:212222110031
### NAME: PANIMALAR P
 ![image](https://github.com/user-attachments/assets/2dff6b05-5749-40f1-b2f8-c11fdf3292ad)

  ![image](https://github.com/user-attachments/assets/07ab0dc1-f750-4990-a1f3-14951b48abdb)
  ![image](https://github.com/user-attachments/assets/acc1cba8-689c-4423-82b5-5ec6ce49572f)

 ![image](https://github.com/user-attachments/assets/98bdd43a-ab5b-4984-84cc-e8f1b94441a5)
![image](https://github.com/user-attachments/assets/4637e706-6662-4eaf-bbad-4b9a6e55d286)

 ![image](https://github.com/user-attachments/assets/585a89dc-5f7a-4057-9c97-fb933eaa0da8)
 
 
 

## RESULT
 
Thus, The setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones, enabling shared access to data is executed successfully.
  



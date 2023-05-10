## EFS (Amazon Elastic File System)

Amazon’s Elastic File System (EFS) is a scalable storage solution that can be used for general purpose workloads. An EFS can be attached to multiple Amazon Web Services (AWS) compute instances and on-premises servers, providing a common resource for applications and data storage in many different environments.

An EFS is a Network File System (NFS) that organizes data in a logical file hierarchy. Data is stored in a path-based system, where data files are organized in folders and sub-folders.

Mapped file server drives and detachable USB drives both use hierarchical file systems, so the concept should be familiar to anyone who has ever dealt with personal computers and servers.

EFSs are ideal candidates for storing:

* Organizational data
* File server
* Individual data
* Application data
Amazon states that a single EFS can be simultaneously connected to thousands of Elastic Compute Cloud (EC2) instances or on-premise resources, allowing you to share EFS data with as many resources as needed.

Access to shared EFS folders and data is provided through native operating system interfaces.
### Advantages to using an EFS
An Amazon EFS is elastic. That means its storage capacity can be automatically scaled up (add more storage) or scaled down (shrink storage capacity) as folders and files are added to or removed from the system. This is a major advantage over traditional storage solutions—you can add or remove capacity without disrupting users or applications.

Importantly, EFS storage is permanent. When attached to an AWS compute instance, data will not disappear when that instance is relaunched.
### Disadvantages to using an EFS
Amazon EFSs do have a couple limitations:

1. **No Windows instances**. Amazon EFSs are not supported on AWS Windows EC2 instances. EFS volumes can only be used with non-Windows instances, such as Linux, that support NFS volumes.
2. **No system boot volumes**. Amazon EFS volumes also cannot be used for system boot volumes. AWS EC2 instances must use Elastic Block Store (EBS) volumes for booting their systems. EBS volumes are like EFS volumes with one exception. An EBS volume can only be connected to one EC2 instance or server, while EFS volumes can be connected to several EC2 instances and on-premises resources.

**Steps**
1. Create an EFS file system
2. Create two EC2 instance
3. Check the security group of the EFS to macth with the security group of the two(2) EC2 instance
4. SSH in to the two instance
5. Update the instances
6. Install the nfs client on both instance
7. Create a directory on both instance using `efs` as the prefix of the file name
8. copy and paste the `Using the NFS client` command on both instance and making sure that the file name is attached to the end of the command
9. cd into the directory and cteate a file on one(1) instance
10. The file that you created woulld reflect on the other instance.


**Praticals**
1. Create an EFS file system:

Click on `services` at the top, click on `storage` and you would see EFS
Click on `Create file system`
Give the file system a name and click on `Create`

2. Create two EC2 instance:

Goto your EC2 and create two EC2 instance using default settings.

3. Check the security group of the EFS to macth with the security group of the two(2) EC2 instance:

Got your EFS, click on the name of the EFS you just created
Scroll down and click on `Network` to check the security group
Goto your instance, click on the marker on one of the instance
Click on `Action` at the top
Click on the `security group` option
Click on `Change security group` option
Type the EFS security group name on the `search bar` and click on it
Click `Add security group` and `Save`
Do it to both instance

4. SSH in to the two instance

5. Update the instances:

using:

    sudo apt-get update


6. Install the nfs client on both instance


       sudo apt-get install nfs-common

7. Create a directory on both instance using `efs` as the prefix of the file name

Create a directory with efs as prefix such as 

    mkdir efstest1 

8. copy and paste the `Using the NFS client` command on both instance and making sure that the file name is attached to the end of the command:

Goto your EFS, click on the EFS that you just created
Click on `Attach`, at the top right corner
Copy the `Using the NFS client` command and paste on both instances, making sure that the file name is attached to the end of the command

    sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-09ab96cc6cdfc0e3c.efs.us-east-1.amazonaws.com:/ efstest1

9. cd into the directory and create a file on one(1) instance

cd into the directory using commands like

    cd efstest1

Create a file using

    touch me.txt

10. The file that you created woulld reflect on the other instance.
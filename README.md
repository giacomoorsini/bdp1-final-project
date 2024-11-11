# <p style="text-align:center;"> <b> Building Cloud IaaS Infrastructures and Computing Models </b> </p>

# Index
- Introduction
  - Big Data and Cloud computing
  - AWS
  - Instances
  - Cloud computing elements
  - Security in Cloud computing
  - File sharing in the data ceneter
  - Managing tasks in the data center
  - Sharing data among data centers
  - The scientific challenge
  - Aim of the project
- Instructions
  - Build a computing infrastructure on the Cloud
  - Simulation of geographical distribution of the sites
  - Extension of the Infrastructure
  - The biological challange
  - Work with containers: Docker
  - Results: time-cost estimation

# Introduction
This repository contains the final project of the Big Data infrastructures course of the Bioinformatics Master of Bologna, created by Laia Torres Masdeu and Giacomo Orsini. It contains all the instructions and files used to build a cloud IaaS infrastructure with AWS (Amazon Web Service) and Google Cloud Platform, as well as the final report made for the Big Data Infrastructure course.
The objectives of the project were the following:
- Build a computing infrastructure on the Cloud composed of at least two distinct and geographically distributed “sites”. Each site has to have:
  - CPU resources in a small batch farm.
  - Storage resources as one or more volumes attached.
  - Be based on an open source Linux distribution.
  - A batch system of choice.
- Install at least one data transfer tool of choice.
- Simulate geographical distribution.
- Create another cloud infrastructure with another Cloud system and transfer data between the two infrastructures.
- Simulate a computational challenge (biological) to be executed with this infrastructure.
- Create a container image that can be used to run the application and describe how you would use it in the computing model.
- Evaluate the time and costs needed to address the complete challenge chosen.

Written by Giacomo Orsini and Laia Torres Masdeu.

### Big Data and Cloud computing 
"Big Data" is high-volume, high-velocity and high-variety information assets that demand cost-effective, innovative forms of information processing that enable enhanced insight, decision making, and process automation. Moreover, this information is also high-veracity (meaning uncertain, uncategorized, difficult to trust) and high-value. In fact, processing and analyzing this data offers significant insights but requires powerful computing resources and storage.
Traditional systems struggle to handle this scale, which is why cloud infrastructures are essential. Cloud computing is a technology that delivers computing services over the Internet, providing resources like servers, storage, computing power, databases, networking, software, and analytics on demand. It typically uses a pay-as-you-go model. Large clouds often have functions distributed over multiple locations, each of which is a data center. Cloud infrastructures provide a flexible, scalable environment that can support big data needs by offering resources on demand. They often operate as Infrastructure as a Service (IaaS), which provides virtualized computing resources over the Internet. In an IaaS setup, users can rent processing power, storage, and network capabilities without needing to maintain physical servers.

### AWS
Amazon Web Services (AWS) is a comprehensive and widely used cloud platform that provides a vast array of on-demand computing services. EC2 (Elastic Compute Cloud) is a core service in AWS that provides resizable compute capacity in the cloud. Essentially, EC2 allows users to rent virtual servers, known as instances, to run applications, host websites, or process data. The service is highly scalable, meaning users can increase or decrease computing power as needed. EC2 instances can run various operating systems (Linux, Windows, etc.) and are priced based on usage, making it a flexible and cost-effective solution for different types of workloads. With EC2, AWS users only pay for the compute capacity they use, without the need to invest in physical hardware.

### Instances
An **instance** is a virtual server that runs on EC2. It is essentially a virtual machine (VM) that operates as an isolated environment within the AWS cloud. AWS provides various types of EC2 instances, such as `t2.large`, which specify different CPU, memory, and networking capacities suited to specific workloads. EC2 instances can be categorized into types like general-purpose, compute-optimized, memory-optimized, etc., depending on the needs of the application. AWS also provides **volumes**, which are block-level storage devices attached to instances. These can be used to store data persistently, even when instances are stopped or terminated.

### Cloud computing elements
In cloud computing and distributed systems, "**site**" refers to different geographical locations or data centres that host computing resources. These sites could be within the same cloud provider or across multiple providers and regions. A **node** in cloud computing is a basic unit (virtual machine) of a network or system (or site) that performs a specific function or task. A **master node** is the primary node in a distributed system that controls and coordinates tasks. It typically handles job scheduling, resource management, and monitoring. **Worker nodes**, on the other hand, are the nodes that execute tasks or processes assigned by the master node. The master node manages and assigns workloads to the worker nodes, which carry out the actual computation. In a cloud environment like AWS, master and worker nodes could be represented by EC2 instances located across different regions or availability zones. AWS organizes its infrastructure into **Regions** (large geographical areas) and **Availability Zones** (isolated data centers within each region). This separation allows for improved resilience, redundancy, and fault tolerance, as resources in one location can continue to function if another location experiences a failure. This distribution is particularly important for ensuring high availability and disaster recovery.

### Security in cloud computing
In AWS, a **key pair** is a pair of cryptographic keys used to access EC2 instances securely. AWS stores the public key while the user downloads the private key. When launching an EC2 instance, the private key is used for SSH access (for Linux instances). A **security group** is a virtual firewall that controls the inbound and outbound traffic for an EC2 instance. Security groups define which network traffic is allowed to reach the instance by specifying rules based on **IP address** ranges, ports, and protocols. They are essential for ensuring the security of instances and restricting unauthorized access.

### File sharing in the data center
Within a data center, a **network file-sharing protocol** is important because it allows multiple computers or instances to access and share files over a network, ensuring that data can be accessed centrally, even when it’s stored on different machines. This eliminates the need to transfer files between systems manually and supports collaborative work. **NFS** (Network File System) is one such protocol commonly used in Linux-based systems. It enables systems to share files over a network, allowing one computer (the server) to export a directory and another computer (the client) to access it as if it were a local directory. NFS is crucial in distributed systems, like those running on AWS, where data needs to be accessed across multiple instances or nodes in a seamless and efficient way.

### Managing tasks in the data center
A **job manager** is a system that manages and schedules computational tasks across a distributed computing environment. In high-performance computing (HPC) and distributed systems, job managers ensure that tasks are efficiently distributed to available resources, workloads are balanced, and jobs are completed on time. **HTCondor** is a job manager that provides a framework for managing, scheduling, and executing jobs on a cluster of machines. It is commonly used in research and computational environments where large-scale data processing is required. HTCondor handles job queuing, prioritization, and execution across multiple nodes, making it a crucial tool in managing complex workflows and ensuring that computational resources are utilized efficiently.

### Sharing data among data centers
In distributed computing environments, resources like data and processing power are often spread across multiple geographic locations or sites. Sharing these resources efficiently is essential for balancing workloads, reducing latency, and ensuring access to up-to-date information. This is particularly important for collaborative projects, data-intensive applications, or organizations with teams in different regions. **Web Distributed Authoring and Versioning (WebDAV)** is a protocol designed to enable web-based file sharing and collaborative management of files across sites. It allows users to access, edit, and manage files on remote servers as though they were local files. By supporting common file operations like reading, writing, and updating, WebDAV facilitates seamless data sharing across multiple locations. This enhances collaboration, reduces the need for manual file transfers, and ensures that users are always working with the latest information, making it a valuable tool for distributed and cloud-based systems.

### The scientific challenge
NGS (next Generation Sequencing) is a powerful technology that allows scientists to sequence entire genomes, analyze gene expression, and study genetic variations rapidly and accurately. The scale and speed of NGS have revolutionized genomics, enabling breakthroughs in personalized medicine, genetic research, and disease diagnostics. By generating massive amounts of DNA or RNA data in a single run, NGS produces vast quantities of complex, high-resolution genetic information. This level of data qualifies as "big data" because it requires substantial storage, computational power, and advanced analytics to process, interpret, and manage. In this context, cloud computing is essential to handle the complexity of data, allowing researchers to scale computing resources depending on their specific data analysis needs. Cloud computing also supports collaborative work, enabling researchers across the globe to access and analyze data simultaneously.

## Aim of the project
The aim of this work was the construction of a Cloud computing infrastructure using Amazon Web Services (AWS), simulating a geographical separation of sites, in order to solve a computational challenge for a biological model. During the creation of the infrastructure, the Network File System (NFS), HTCondor batch system, and WebDav data transfer tool were installed and used to manage data both within and between sites. A volume of existing data, initially created for the IBDPI course of the Master in Bioinformatics, was attached to the master nodes and shared among the respective worker nodes using NFS. During the building process, the infrastructure was expanded with two additional sites, each composed of a single master node, created through the Google Cloud Platform (GCP). To address the computational challenge, a custom Docker image was developed to run jobs with the HTCondor system. Finally, a time/cost table was generated to evaluate the infrastructure’s performance, and various possibilities for enhancement were discussed.


# Instructions
To replicate the work done, please download and follow the final report `BSPI_project_ltm_go.pdf` (https://github.com/giacomoorsini/bdp1-final-project/blob/main/BDPI_project_ltm_go.pdf).

## Build a computing infrastructure on the Cloud
A small **Iaas** (Infrastructure as a Service) infrastructure was built with **Amazon Web Services** (AWS) **Elastic Compute Cloud** (EC2) as a provider. This service provides fundamental hardware resources, servers, storage, and networking components. The aim was to simulate two geographically distributed sites composed of two nodes each:
 - **Site 1**, with 3 nodes: 1 master node (`S1_M`) and 2 workers nodes (`S1_W1 and S1_W2`)
 - **Site 2**, with 2 nodes: 1 master node (`S2_M`) and 1 worker nodes (`S2_W2`)

A **data volume** created from an existing snapshot was attached to both Master nodes. In both
sites, the **Network File System** (NFS) was installed to share data from the master nodes to the worker nodes of the same site. Then, a batch system for handling computations and CPUs (**HTCondor**) was installed, configuring the machines as Master/Workers. It was used to simulate the sharing of data from the volume attached to the Master with the workers at each site. Finally, the **WebDav** tool was installed on both sites to simulate data transfer between the two. The HTCondor system has been used to test the computational challenge in _section 4_.

### Create the instances on AWS
All the **instances** (Virtual Machines) were created with the Amazon Elastic Compute Cloud (Amazon EC2) service; each instance represents a node, and each of the 2 sites was created using 2 different AWS accounts (Giacomo Orsini and Laia Torres Masdeu).
To create each node, we used the following procedure:
 1. Rename the instances (`site1_master`, `site1_worker1`, `site1_worker2`, and `site2_master`,
 `site2_worker1`)
 2. Select an **open-source Linux distribution**: we decided to use the `RHEL-7.9_HVM-20220512-x86_64-1-Hourly2-GP2` version, published on the 2022-05-12.
 3. Select a type of instance for each node: we selected `t2-large` (2 CPU, 8 GB RAM) for all.
 4. Create a new **key pair**. This is done only once when creating the first instance of each site. Save the key (`.pem` format) document to the directory (from which you will need to initialise all the instances from this directory or change the key file directory from the initialisation command). In the other instances, select the previously created key pair.
 5. To simulate the geographical separation, select two different **Availability Zones** (sub-nets) in the network settings. We selected `us-east 1a` for `site 1` and `us-east 1c` for `site 2`.
 6. Create a **security group** for each site (create it for master, select existing for workers). We created `site1-security` for `site 1` and `site2-security` for `site 2`.
 7. Modify **inbound security groups rules** so that only you can access the sites: we removed the `default` (open to all, `0.0.0.0/0`) and restricted to the current IP address: `Security group rule 1` (`TCP`, `22`, `<your\_IP>/32`, SSH for my IP address)
 8. (Optional) Select different **size storage**, default being 10 gb. We selected 30 gb for `site2`.

Once each site was created, the connection is enabled to each node using `ssh` (`ssh-i "<key_name>.pem" ec2-user@ec2-<AWS_node_public_IP>.compute-1.amazonaws.com`). To help with the **prompt visualisation**, it is possible to change the prompt both in the ec2-user and root users to the name of each site and node we were working on. To do this, it is sufficient to modify the `.bashrc` file in both users. The specific lines of code used can be found in this Github repository:

```
ssh -i "<key_name>.pem" ec2-user@ec2-<AWS_node_public_IP>.compute-1.amazonaws.com         #connect to instance

################IN THE USER################
vi .bashrc                                                                                    
#paste the following line at the end of the file

PS1="\[\033[01;32m\]\u@<prompt_name>\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

################IN THE ROOT################
sudo su -
vi .bashrc                                                                                       #paste the following line at the end of the file

PS1="\[\033[01;32m\]\u@<prompt_name>\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

exit                                                                                             #exit root

exit                                                                                             #close connection to ssh

#connection has to be closed and re-initiated to save the changes done to .bashrc
```

### Attach an existing volume 
To extend the capacity of the nodes and to have data on which to operate, a **volume** was attached to each of the `master nodes`. These volumes were created in AWS with default settings from a **snapshot** made by the professor of the _BDPI course of the Master in Bioinformatics_ (University of Bologna), hence they were retrieved from the "**Snapshot ID**" option by using the code `snap-BDPI_2023`. We selected the correct `Availability Zone` for the volume of each site. Once the 2 volumes were created, they had to be attached to a node. To attach the volumes to the master nodes, they had to be connected to the Master instances through the **EC2 control panel**, in the **volume section**; then, on the virtual machines, the following commands (that can be found in this GitHub repository) were issued:

```
###########TO MOUNT THE VOLUME INTO THE NODE###########
sudo su -                                 #move to root
mkdir /project_data                       #create directory where to mount the volume
fdisk -l                                  #list the disk partitions and retrieve volume path
mount -t ext4 /dev/xvdf1 /project_data/   #mount volume path to directory path
##############TO MAKE THE MOUNT PERMANENT##############
vi /etc/fstab                             #add this line at the end of the fstab file: /dev/xvdf1	/project_data	ext4 defaults 0 0
mount -a                                  #mount all the filesystem listed in the fstab file
```

It is important to remark that the first mount command, `mount-a`, already mounted the volume into the `\project_data` directory of the worker node (Figure 4). However, this was not permanent. To make it permanent, the paths for the volume and the destination source in the VM were added to the `/etc/fstab` file.

After these steps, each volume was attached to the respective master node through a path leading to a folder, the `project_data` folder. The volume can be found locally in this directory. However, the directory was not yet accessible to any of the worker nodes. To enable the data transfer, NFS was installed in each master and worker.

### Install a NFS Client-Server
The **Network File System** (NFS) is a network file-sharing protocol that allows machines on the same network to share directories and files. The client can access files and directories exposed by the host as if they were locally stored. This tool enabled the sharing of the attached data volume from the master node (`host`) to the worker nodes (`clients`) in each site. Specifically, it allowed the worker nodes to access the directory of the mounted volume on the master nodes. In this case, only access to the volume was needed for the worker nodes, without modification permissions. Therefore, `read`, `write`, and `execute` permissions were granted to the owner (master node) of the directory and associated groups, but only `read` and `execute` permissions (4+1) were given to other users (worker nodes). This configuration was achieved using the command `chmod 775 \project_data`. The specific code lines used to install and connect NFS to the master and worker nodes can also be found in the project's GitHub repository:

```
#commands adapted from the BDP1 course notes

chmod 775 /project_data/                   #grant read, write, and execute permissions to the owner (master node) of the directory and to the group associated to it, but only read and execute permissions (4+1) to other users (worker nodes)

############IN THE SERVER (MASTER)############
sudo su - 

yum install nfs-utils rpcbind
systemctl enable nfs-server
systemctl enable rpcbind
systemctl enable nfs-lock
systemctl enable nfs-idmap
systemctl start rpcbind
systemctl start nfs-server
systemctl start nfs-lock
systemctl start nfs-idmap
systemctl status nfs              #verify that nfs status is active

vi /etc/exports                   #add the following lines in the the exports file (as much lines as clients you have). This will make the /project_data directory accessible to the worker nodes 
#          /project_data <WORKER1_PRIVATE_IP>(rw,sync,no_wdelay)
#          /project_data <WORKER2_PRIVATE_IP>(rw,sync,no_wdelay)

exportfs -r                       #export the changes, so that NFS-server is accessible from the client
exportfs                          #check that the desired directory has been exported to the desired IP address

###########IN THE CLIENTS (WORKERS)###########
sudo su -
yum install nfs-utils
mkdir /project_data               #create the directory from where you want the NFS client to access the NFS server
vi /etc/fstab                     #add the following line at the end of the fstab file. This will allow the NFS to be mounted automatically at boot time
#          <MASTER_PRIVATE_IP>:/project_data /project_data   nfs defaults        0 0

mount -a                          #mount the changes
```

Note: To grant `write` access to worker nodes, so that files and directories can be added to the volume and accessed by all nodes connected to NFS, the command `chmod 777` should be used. It is essential to add the private IP address(es) of the worker node(s) to the security group inbound rules for the NFS port, allowing the master node to accept requests from the worker node(s). To enable sharing of the volume (in the `\project_data directory`), the file `/etc/exportfs` on the server (master) node was modified, allowing directory access from the client (worker) node(s). After exporting, the directory and client (worker) IP address(es) were verified to be correct (Figure 6).

On the worker node(s), a directory, also named `\project_data`, was created to mount the NFS. It was set to mount automatically at boot by modifying the `/etc/fstab` file. In Figure 7, it is shown that the `mount -a command` executed successfully.
With this setup, storage resources were successfully shared among all nodes at each site.


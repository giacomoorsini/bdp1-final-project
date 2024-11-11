# <p style="text-align:center;"> <b> Building Cloud IaaS Infrastructures and Computing Models </b> </p>

This repository contains the final project of the Big Data infrastructures course of the Bioinformatics Master of Bologna, created by Laia Torres Masdeu and Giacomo Orsini. It contains all the instructions and files used to build a cloud IaaS infrastructure with AWS (Amazon Web Service) and Google Cloud Platform, as well as the final report made for the Big Data Infrastructure course.

Written by Giacomo Orsini and Laia Torres Masdeu.

# Index
- [Introduction](#introduction)
  - [Big Data and Cloud Computing](#big-data-and-cloud-computing)
  - [AWS](#aws)
  - [Instances](#instances)
  - [Cloud Computing Elements](#cloud-computing-elements)
  - [Security in Cloud Computing](#security-in-cloud-computing)
  - [File Sharing in the Data Center](#file-sharing-in-the-data-center)
  - [Managing Tasks in the Data Center](#managing-tasks-in-the-data-center)
  - [Sharing Data Among Data Centers](#sharing-data-among-data-centers)
  - [The Scientific Challenge](#the-scientific-challenge)
  - [Aim of the Project](#aim-of-the-project)
- [Instructions](#instructions)
  
# Introduction
In the world of **Big Data**, where incredibly large amounts of information are constantly generated, being able to extract valuable knowledge is of extreme importance. In this context, **Cloud computing** represents a valuable strategy to manage, store and analyze these quantities of data. Cloud computing infrastructures and data centers have become more and more essential, even in fields such as Biotechnology and Biology, where new, cutting-edge experimental techniques (such as NGS) grant us an unimaginable amount of information. Because of this, learning how a data center works and how to work within it has become a valuable skill set to have. This was the aim of the Big Data Infrastructures course. The objectives of the final project were the following:
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

The following chapters provide a brief overview of the concepts encountered during the project. The full explanation and workflow can be found in the project report, while all the commands used in each section are reported in the folder.

## Big Data and Cloud computing 
"**Big Data**" is high-volume, high-velocity and high-variety information assets that demand cost-effective, innovative forms of information processing that enable enhanced insight, decision making, and process automation. Moreover, this information is also high-veracity (meaning uncertain, uncategorized, difficult to trust) and high-value. In fact, processing and analyzing this data offers significant insights but requires powerful computing resources and storage.
Traditional systems struggle to handle this scale, which is why cloud infrastructures are essential. **Cloud computing** is a technology that delivers computing services over the Internet, providing resources like servers, storage, computing power, databases, networking, software, and analytics on demand. It typically uses a pay-as-you-go model. Large clouds often have functions distributed over multiple locations, each of which is a data center. Cloud infrastructures provide a flexible, scalable environment that can support big data needs by offering resources on demand. They often operate as **Infrastructure as a Service (IaaS)**, which provides virtualized computing resources over the Internet. In an IaaS setup, users can rent processing power, storage, and network capabilities without needing to maintain physical servers.

## AWS
**Amazon Web Services (AWS)** is a comprehensive and widely used cloud platform that provides a vast array of on-demand computing services. **EC2 (Elastic Compute Cloud)** is a core service in AWS that provides resizable compute capacity in the cloud. Essentially, EC2 allows users to rent virtual servers, known as instances, to run applications, host websites, or process data. The service is highly scalable, meaning users can increase or decrease computing power as needed. EC2 instances can run various operating systems (Linux, Windows, etc.) and are priced based on usage, making it a flexible and cost-effective solution for different types of workloads. With EC2, AWS users only pay for the compute capacity they use without the need to invest in physical hardware.

## Instances
An **instance** is a virtual server that runs on EC2. It is essentially a virtual machine (VM) that operates as an isolated environment within the AWS cloud. AWS provides various types of EC2 instances, such as `t2.large`, which specify different CPU, memory, and networking capacities suited to specific workloads. EC2 instances can be categorized into types like general-purpose, compute-optimized, memory-optimized, etc., depending on the needs of the application. AWS also provides **volumes**, which are block-level storage devices attached to instances. These can be used to store data persistently, even when instances are stopped or terminated.

## Cloud computing elements
In cloud computing and distributed systems, "**site**" refers to different geographical locations or data centres that host computing resources. These sites could be within the same cloud provider or across multiple providers and regions. A **node** in cloud computing is a basic unit (virtual machine) of a network or system (or site) that performs a specific function or task. A **master node** is the primary node in a distributed system that controls and coordinates tasks. It typically handles job scheduling, resource management, and monitoring. **Worker nodes**, on the other hand, are the nodes that execute tasks or processes assigned by the master node. The master node manages and assigns workloads to the worker nodes, which carry out the actual computation. In a cloud environment like AWS, master and worker nodes could be represented by EC2 instances located across different regions or availability zones. AWS organizes its infrastructure into **Regions** (large geographical areas) and **Availability Zones** (isolated data centers within each region). This separation allows for improved resilience, redundancy, and fault tolerance, as resources in one location can continue to function if another location experiences a failure. This distribution is particularly important for ensuring high availability and disaster recovery.

## Security in cloud computing
In AWS, a **key pair** is a pair of cryptographic keys used to access EC2 instances securely. AWS stores the public key while the user downloads the private key. When launching an EC2 instance, the private key is used for SSH access (for Linux instances). A **security group** is a virtual firewall that controls the inbound and outbound traffic for an EC2 instance. Security groups define which network traffic is allowed to reach the instance by specifying rules based on **IP address** ranges, ports, and protocols. They are essential for ensuring the security of instances and restricting unauthorized access.

## File sharing in the data center
Within a data center, a **network file-sharing protocol** is important because it allows multiple computers or instances to access and share files over a network, ensuring that data can be accessed centrally, even when it’s stored on different machines. This eliminates the need to transfer files between systems manually and supports collaborative work. **NFS** (Network File System) is one such protocol commonly used in Linux-based systems. It enables systems to share files over a network, allowing one computer (the server) to export a directory and another computer (the client) to access it as if it were a local directory. NFS is crucial in distributed systems, like those running on AWS, where data needs to be accessed across multiple instances or nodes in a seamless and efficient way.

## Managing tasks in the data center
A **job manager** is a system that manages and schedules computational tasks across a distributed computing environment. In high-performance computing (HPC) and distributed systems, job managers ensure that tasks are efficiently distributed to available resources, workloads are balanced, and jobs are completed on time. **HTCondor** is a job manager that provides a framework for managing, scheduling, and executing jobs on a cluster of machines. It is commonly used in research and computational environments where large-scale data processing is required. HTCondor handles job queuing, prioritization, and execution across multiple nodes, making it a crucial tool in managing complex workflows and ensuring that computational resources are utilized efficiently.

## Sharing data among data centers
In distributed computing environments, resources like data and processing power are often spread across multiple geographic locations or sites. Sharing these resources efficiently is essential for balancing workloads, reducing latency, and ensuring access to up-to-date information. This is particularly important for collaborative projects, data-intensive applications, or organizations with teams in different regions. **Web Distributed Authoring and Versioning (WebDAV)** is a protocol designed to enable web-based file sharing and collaborative management of files across sites. It allows users to access, edit, and manage files on remote servers as though they were local files. By supporting common file operations like reading, writing, and updating, WebDAV facilitates seamless data sharing across multiple locations. This enhances collaboration, reduces the need for manual file transfers, and ensures that users are always working with the latest information, making it a valuable tool for distributed and cloud-based systems.

## The scientific challenge
**NGS** (next Generation Sequencing) is a powerful technology that allows scientists to sequence entire genomes, analyze gene expression, and study genetic variations rapidly and accurately. The scale and speed of NGS have revolutionized genomics, enabling breakthroughs in personalized medicine, genetic research, and disease diagnostics. By generating massive amounts of DNA or RNA data in a single run, NGS produces vast quantities of complex, high-resolution genetic information. This level of data qualifies as "big data" because it requires substantial storage, computational power, and advanced analytics to process, interpret, and manage. In this context, cloud computing is essential to handle the complexity of data, allowing researchers to scale computing resources depending on their specific data analysis needs. Cloud computing also supports collaborative work, enabling researchers across the globe to access and analyze data simultaneously.

## Aim of the project
The aim of this work was the construction of a Cloud computing infrastructure using Amazon Web Services (AWS), simulating a geographical separation of sites, in order to solve a computational challenge for a biological model. During the creation of the infrastructure, the Network File System (NFS), HTCondor batch system, and WebDav data transfer tool were installed and used to manage data both within and between sites. A volume of existing data, initially created for the IBDPI course of the Master in Bioinformatics, was attached to the master nodes and shared among the respective worker nodes using NFS. During the building process, the infrastructure was expanded with two additional sites, each composed of a single master node, created through the Google Cloud Platform (GCP). To address the computational challenge, a custom Docker image was developed to run jobs with the HTCondor system. Finally, a time/cost table was generated to evaluate the infrastructure’s performance, and various possibilities for enhancement were discussed.

# Instructions
To replicate the work done, please download and follow the final report `BSPI_project_ltm_go.pdf` (https://github.com/giacomoorsini/bdp1-final-project/blob/main/BDPI_project_ltm_go.pdf). The commands used in the "coding" part can be found in the folder , while the steps executed on AWS can be easily followed in the report.


# <p style="text-align:center;"> <b> Building Cloud IaaS Infrastructures and Computing Models </b> </p>

# Index
- Introduction
  - Big Data, Cloud computing and AWS
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
This repository contains the final project of the Big Data infrastructures course of the Bioinformatics Master of Bologna, created by Laia Torres Masdeu and Giacomo Orsini. The objectives of the project were the following:
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

This repository contains all the instructions and files used to build a cloud IaaS infrastructure with AWS (Amazon Web Service) and Google Cloud Platform, as well as the final report made for the Big Data Infrastructure course.

Written by Giacomo Orsini and Laia Torres Masdeu.

## Big Data, Cloud computing and AWS
"Big Data" is high-volume, high-velocity and high-variety information assets that demand cost-effective, innovative forms of information processing that enable enhanced insight, decision making, and process automation. Moreover, this information is also high-veracity (meaning uncertain, uncategorized, difficult to trust) and high-value. In fact, processing and analyzing this data offers significant insights but requires powerful computing resources and storage.
Traditional systems struggle to handle this scale, which is why cloud infrastructures are essential. Cloud infrastructures provide a flexible, scalable environment that can support big data needs by offering resources on demand. They often operate as Infrastructure as a Service (IaaS), which provides virtualized computing resources over the internet. In an IaaS setup, users can rent processing power, storage, and network capabilities without needing to maintain physical servers.
Amazon Web Services (AWS) is a comprehensive and widely used cloud platform that provides a vast array of on-demand computing services.

## The scientific challenge
NGS (next Generation Sequencing) is a powerful technology that allows scientists to sequence entire genomes, analyze gene expression, and study genetic variations rapidly and accurately. The scale and speed of NGS have revolutionized genomics, enabling breakthroughs in personalized medicine, genetic research, and disease diagnostics. By generating massive amounts of DNA or RNA data in a single run, NGS produces vast quantities of complex, high-resolution genetic information. This level of data qualifies as "big data" because it requires substantial storage, computational power, and advanced analytics to process, interpret, and manage. In this context, cloud computing is essential to handle the complexity of data, allowing researchers to scale computing resources depending on their specific data analysis needs. Cloud computing also supports collaborative work, enabling researchers across the globe to access and analyze data simultaneously.

## Aim of the project
The aim of this work was the construction of a Cloud computing infrastructure using Amazon Web
Services (AWS), simulating a geographical separation of sites, in order to solve a computational challenge for a biological model. During the creation of the infrastructure, the Network File System (NFS), HTCondor batch system, and WebDav data transfer tool were installed and used to manage data both within and between sites. A volume of existing data, initially created for the IBDPI course of the Master in Bioinformatics, was attached to the master nodes and shared among the respective worker nodes using NFS. During the building process, the infrastructure was expanded with two additional sites, each composed of a single master node, created through the Google Cloud Platform (GCP). To address the computational challenge, a custom Docker image was developed to run jobs with the HTCondor system. Finally, a time/cost table was generated to evaluate the infrastructure’s performance, and various possibilities for enhancement were discussed.

# Instructions
To replicate the work done, please download and follow the final report `BSPI_project_ltm_go.pdf` (https://github.com/giacomoorsini/bdp1-final-project/blob/main/BDPI_project_ltm_go.pdf).

## Build a computing infrastructure on the Cloud
 A small Iaas (Infrastructure as a Service) infrastructure was built with Amazon Web Services (AWS) Elastic Compute Cloud (EC2) as a provider. This service provides fundamental hardware resources, servers, storage, and networking components. The aim was to simulate two geographically distribut

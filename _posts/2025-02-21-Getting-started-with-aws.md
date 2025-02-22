---
layout: post
title: AWS Fundamentals, Start of my cloud journey
subtitle: Notes from the AWS Cloud Practitioners Essentials course
thumbnail-img: /assets/img/AWS-Logo.png
tags: [AWS, AWS Free Tier, AWS Cloud Practitioner Essentials, AWS Management Console Basics, Amazon EC2, EC2 Instance Types, EC2 Auto Scaling, Lambda (Serverless Functions), AWS Lambda, Amazon S3, S3 Storage Classes, Amazon VPC, VPC Subnets, Networking, IAM (Identity and Access Management), Cloud Computing, Client-Server Model, Multitenancy, Vertical Scaling, General Purpose Instances, Compute Optimized Instances, Memory Optimized Instances, Accelerated Computing Instances, Storage Optimized Instances, On-Demand Instances, Reserved Instances, EC2 Instance Savings Plans, Spot Instances, Dedicated Hosts, Elastic Load Balancing (ELB), Amazon SQS, Amazon SNS, Amazon ECS, Amazon EKS, AWS Fargate, AWS Regions, Availability Zones (AZ), Edge Locations, Amazon CloudFront, AWS Outposts, AWS Management Console, AWS CLI, AWS SDKs, AWS Elastic Beanstalk, AWS CloudFormation, Internet Gateway (IGW), Virtual Private Gateway, AWS Direct Connect, Network ACL, Security Group, Public Subnets, Private Subnets, Amazon Route 53, DNS (Domain Name System), Instance Store Volumes, Amazon EBS, EBS Snapshots, Amazon EFS, Amazon RDS, Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, Microsoft SQL Server, Amazon DynamoDB, Amazon Redshift, AWS Database Migration Service (AWS DMS), Amazon DocumentDB, Amazon Neptune, Amazon QLDB, Amazon Managed Blockchain, Amazon ElastiCache, Amazon DynamoDB Accelerator (DAX), AWS Shared Responsibility Model, IAM Users, Groups, and Roles, IAM Policies, Multi-Factor Authentication (MFA), AWS Organizations, Organizational Units (OU), AWS Artifact, AWS Shield (Standard and Advanced), AWS KMS, AWS WAF, Amazon Inspector, Amazon GuardDuty, Amazon CloudWatch, CloudWatch Alarms, AWS CloudTrail, CloudTrail Insights, AWS Trusted Advisor, AWS Marketplace, AWS Cloud Adoption Framework (AWS CAF), Business Perspective, People Perspective, Governance Perspective, Platform Perspective, Security Perspective, Operations Perspective, Migration Strategies (Rehost, Replatform, Refactor, Repurchase, Retain, Retire), AWS Snow Family, AWS Snowcone, AWS Snowball, Snowball Edge Storage Optimized, Snowball Edge Compute Optimized, AWS Snowmobile, Serverless Applications, Artificial Intelligence, Machine Learning, Amazon SageMaker, AWS Well-Architected Framework, Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability]
comments: true
mathjax: true
author: Alejandro Fluitt Martinez
---



# Getting started with AWS
I created a free account on WS free tier.
I was told to do these course
* AWS Cloud Practitioner Essentials
* AWS Management Console Basics
* ComputeL EC2 (Virtual Servers), Lambda (Serverless Functions)
* Storage: S3 
* Networking: VPC (Virtual Private Cloud)
* Security: IAM (Identity and Access Management)

## Cloud Practitiioner Essentials
They say it will take 6hrs... I'll let you know

## I Finished (Thoughts)
![Quiz Results](/assets/img/Amazon Cloud Practioners Essentials final assessment results.png_)
Okay so it took me 7-8 hours. But I was writing notes (this). Alot of it yes was AWS/Amazon propganda but I did get e much better understanding of what AWS is. Perhaps Ill go for the Cloud Practitioner exam one of these days. Um... not a waste of time I Hope.

# Below are the notes

### Intro video
AWS service offerings
* Robot development
* Storage (Video Production server)
* Network security (Orbital sattelites you can rent)
* Blockchain
* Machine learning
* Artitificial intelligence

### What is a client-server model?
In computing, a __client__ can be a web browser or desktop application that a person interacts with to make requests to computer servers. A __server__ can be services, such as Amazon Elastic Compute Cloud (Amazon EC2) – a type of virtual server.

They used the reference of a coffee shop. I am a client, I make a request for coffee (and service) the server is the barista. 

AWS no prepay, only pay for what you need. The benefit of AWS

### What is cloud computing
The on demand delivery of IT resources over the internet with pay-as-you-go pricing
*on-premise deployment is also called Private cloud deployment*

__Benefits of cloud computing__
* Upfront expense
* No guessing capacity
* Benefit from massive economies of scale (lower price because of more customers)
* Increase speed and agility
* Go global in minutes

### Introduction to Amazon Elastic Compute Cloud (Amazon EC2)
EC2 is what you use to get access to servers (makes sense because its the cloud) Gets rid of the headache of having servers yourself. Makes sense for website or application hosting.
*Multitenancy: Sharing underlying hardware between virual machines*
We all have our own EC2 instance, where we can confige the OS (Windows/linx) the software running on the instance, databases, apps etc.. 
*vertical scaling- giving the instance more memory or cpu*

![How Amazon EC2 works](/assets/img/How-AmazonEc2-Works.png)

### Amazon EC2 Instance Types
* __General purpose instances__ When the need for compute, memory, and networking are roughly equivalent ie:
    application servers
    gaming servers
    backend servers for enterprise applications
    small and medium databases
 * __Compute optimized instances__ ideal for compute-bound applications (math heavy) that benefit from high-performance processors. Ideal for high-performace web app gaming servers.
    *for **batch processing** workloads that require processing many transactions in a single group.*
* __Memory optimized instances__  ideal for high-performance databases, for large datasets in memory.
* __Accelerated computing instances__ use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs. Examples of these functions include floating-point number calculations, graphics processing, and data pattern matching.
    *ideal for workloads such as graphics applications, game streaming, and application streaming.*
* __Storage optimized instances__ are designed for workloads that require high, sequential read and write access to large datasets on local storage.

In computing, the term __input/output operations per second (IOPS)__ is a metric that measures the performance of a storage device. It indicates how many different input or output operations a device can perform in one second.

### Amazon EC2 pricing
* On-Demand - ideal for short-term, irregular workloads that cannot be interrupted
* Reserved Instances *Standard Reserved Instances: This option is a good fit if you know the EC2 instance type and size you need for your steady-state applications and in which AWS Region you plan to run them.*  or  *Convertible Reserved Instances: If you need to run your EC2 instances in different Availability Zones or different instance types*
You are charged on-demand rates until you terminate the instance.
* EC2 Instance Savings Plans- term commitment results in savings of up to 72 percent compared to On-Demand rate
* Spot Instances- are ideal for workloads with flexible start and end times, or that can withstand interruptions
* Dedicated Hosts- physical servers with Amazon EC2 instance capacity that is fully dedicated to your use. 

### Scaling Amazon EC2

The AWS service that provides automatically scales to meet your computing capacity is called (guess) __Amazon EC2 Auto Scaling__

#### Amazon EC2 Auto Scaling 
Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand.
*Dynamic scaling* responds to changing demand. 
*Predictive scaling* automatically schedules the right number of Amazon EC2 instances based on predicted demand.

Scaling up- increasing the size of the barista
Scaling out- increasing the number of baristas and coffee makers
Decoupling the system (whatever that means)

In the cloud, computing power is a programmatic resource (programable what a bunch of nerds lol), so you can take a more flexible approach to the issue of scaling.
![Amazon EC2 autoscaling](/assets/img/Amazon EC2 autoscaling.png)
**minimum, desired, and maximum capacity**

### Directing Traffic with Elastic Load Balancing
You may have more baristas, but the customer might not know to go to other baristas. The host essentially tells the customers where to go. This induces efficienty.
*Load balancer - application that takes in requests and routes them to an instance to be processed*
#### Elastic Load balancing (ELB)
Regional construct - because it runs at the region level the service is automatically available 
ELB and Autoscaling work in tandem, the ELB being the host and the autoscaling basically the manager of the baristas
(OH sht) Theres an ELB for the workers (coffee makers/backend) too that optimizes the number of workers as well 

### Messaging and Queuing
The system between the barista and giving orders to the worker. As soon as the barista and worker are out of sync it degrades the system. So now, posting the order to the buffer is called messaging and queuing 
*Tightly coupled architecture* passing notes to each other **Monolithic application**
*Loosely coupled architecture:* Single failure wond cause cascading failures. Using a buffer sa Message Queue. **Microservices approach**
2 systems
**Amazon SQS** - allows to send store recieve messages between softwares at any volume
*Payload: Data contained within a message*
*Amazon SQS queues: Where messages are placed until they are processed*
**Amazon SNS** - Can also send out notifications to end users. Called a publish subcribe or pub sub model
*Amazon SNS topic: A channel for messages to be delivered* The idea that different customers want different notifications rather than just sending the same notification to all customers.

### Additional Compute Services
#### AWS Lambda
Designed for processes that take less than 15 minutes. Service like EC2 that lets you run code without need to provision or manage servers. You pay only for the compute time that you consume.
For example, a simple Lambda function might involve automatically resizing uploaded images to the AWS Cloud. In this case, the function triggers when uploading a new image.

![How Lambda Works](/assets/img/How Lambda Works.png)
*Container- package for your code*

#### Amazon ELastic Container (Amazon ECS)
Its a highly scalable, high-performance container management system that enables you to run and scale containerized applications on AWS. Amazon ECS supports Docker containers. With Amazon ECS, you can use API calls to launch and stop Docker-enabled applications.

#### Amazon Elastic Kubernetes Service (Amazon EKS)
Its a fully managed service that you can use to run Kubernetes on AWS. 

#### AWS Fargate 
It is a serverless compute engine for containers. It works with both Amazon ECS and Amazon EKS. When using AWS Fargate, you do not need to provision or manage servers. AWS Fargate manages your server infrastructure for you, pay only for the resources that are required to run your containers.

### Regions
* Compliance- Usually government that dictates regions
* Proximity- Speed of light applies, so *Latency time it takes for data to be sent or recieved* 
* Feature Availability- Some regions dont have all the features. But the R&lt;D might be region dependant.
* Pricing- Some regions are more expensive to run
__Availability Zone (AZ)__ the data centers grouped together. An AWS Region is a grouping of AZ's.
best practice is two run applications across at least 2 AZ's.
An __edge location__ is a site that Amazon CloudFront uses to store cached copies of your content closer to your customers for faster delivery.
__CDN__ Content Delivery Networks... Amazon CloudFront
*AWS Outposts, AWS server in your own building*

### How to Provision AWS Resoures
The __AWS Management Console__ is a web interface for managing AWS services. It lets you quickly access recent services and search for others by name, keyword, or acronym. Wizards and automated workflows help simplify tasks. The AWS Console mobile app lets you monitor resources, view alarms, and check billing. You can keep multiple identities logged in simultaneously.
The __AWS Command Line Interface__ (AWS CLI) lets you control multiple AWS services from the command line on Windows, macOS, and Linux. You can automate tasks using scripts, such as launching an EC2 instance or connecting it to an Auto Scaling group.
___AWS Software Development Kits__ (SDKs) let you access and manage AWS services using APIs designed for your programming language or platform. You can integrate AWS with existing applications or build new ones. AWS provides documentation and sample code for supported languages like C++, Java, .NET, and more.
__AWS Elastic Beastalk__ Allows you to provision EC2 instances, give the application code and desired configuration, it essentially builds it for you.Adjust capacity
Load balancing
Automatic scaling
Application health monitoring
__AWS CloudFormation__ Not restricted to EC2, it lets you build and manage infrastructure as code, instead of manually provisioning resources through the console. It safely provisions resources in a repeatable way, automates stack management, and rolls back changes if errors occur.

### Connectivity to AWS
__VPC__ - Private network in AWS, allows you to have your own private ip adress. They must be placed into differnt __Subnets__ 
__Internet Gatway__ (IGW) is a doorway that allows Public traffic into your VPC.
__Virtual Private Gateway__ allows you to create a VPN connection with a private network to your VPC. 
__AWS Direct Connect__ completely private dedicated fiber connection from your network to your VPC. Private Gatway VPN is still suseptible to attacks.

### Subents and Network Access Control Lists
_NETWORK HARDENING_
__Network access control list__ (Network ACL) Checks packets permissions based on who its sent from or what its trying to do. By default, your account’s default network ACL allows all inbound and outbound traffic, but you can modify it by adding your own rules. 
__Security Group__ Every EC2 comes with a Security Group already assigned, I think for the Network ACL. It is modifiable. It only checks if the sender is on the approved list. By default, security groups deny all inbound traffic, but you can add custom rules to fit your operational and security needs.
__The difference between Security Group and Network ACL__ The security group is _stateful_, it has a memory of who is allowed in and it lets every packet return, where as the Network ACL is _stateless_ means it tracks everysing packet going in or out.
__Public subnets__ contain resources that need to be accessible by the public, such as an online store’s website.
__Private subnets__ contain resources that should be accessible only through your private network, such as a database that contains customers’ personal information and order histories. 

### Global Networking
__Amazon Route 53__ Is AWS Domain name service
__DNS__ Translation service that translates Domain names into IP Adresses. DNS is the phone book of the internet.
* Latency-based routing
* Geolocation DNS
* Geoproximity routing
* Weighted round robin
You can use route 53 to register domain names.

__Amazon Cloud Front__ Content delivery network (CDN): A network that delivers edge content to users based on their geographic location
 
### Instance Stores and Amazon Elastic Block Store (Amazon EBS)
__block level storage__ a place where files are stored, they are stored in blocks because that is more efficient when they need to be changed. Its essentially a hardrive. There are multiple types for EC2.
__instance store volumes__ Physicaly attached to the AWS host. It provides temporary block-level storage for an Amazon EC2 instance and lasts as long as the instance is running. When the instance is terminated, all data in the instance store is lost. Useful for situation where its okay to lose the data of a file. Dont write important data into this, that needs persistance.
__Amazon Elastic Block Store__ (EBS) Virtual Hardrives called __EBS Volumes__ They act like and instance store volume but its digital and persists. EBS allows you to take __Snapshots__: Incremental Backups. Only data that has changed since the most recent snapshot is backed up.

### Amazon Simple Storage Service (Amazon S3)
In __object storage__, each object consists of data, metadata, and a key. Everytime there is a change the entire data must be reuploaded.
__Amazon Simple Storage Service__ (Amazon S3) is a service that provides object-level storage. Amazon S3 stores data as objects in buckets. You can upload any type of file to Amazon S3, The maximum file size for an object in Amazon S3 is 5 TB. When you upload a file to Amazon S3, you can set permissions to control visibility and access to it.
    __Amazon S3 storage classes__
* __S3 Standard__ - designed for frequently accessed data, stores data in a minimum of three AZs
* __S3 Standard-Infrequent Access__(S3 Standard-IA) -  Ideal for infrequently accessed data. Similar to standard but has lower storage price and higher retrieval price.
* __S3 One Zone-Infrequent Access__ (S3 One Zone-IA) - Stores data in a single AZ. Has low storage price. Use if you can easily reproduce your data in the event of an AZ failure
* __S3 Intelligent Tiering__ - Ideal for data with unknown or changing access patterns. Requires a small monthly monitoring fee.
* __S3 Glacier Instant Retrieval__ - Works well for archived data that requires immediate access. Can retrieve objects within a few milliseconds.
* __S3 Glacier Flexible Retrieval__ - low cost storage designed for data archiving, able to retrieve objects with a few minutes to hours.
* __Glacier deep archive__ - Lowest cost for archiving, retrieval -12 hours
* __S3 Outposts__ - Creates S3 buckets on Amazon S3 Outposts. Makes it easier to retrieve, store, and access data on AWS Outposts

### Amazon Elastic File System (EFS)
__File storage__ allows multiple clients to access data in shared file folders using file paths. It uses block storage with a local file system for organization and is ideal for scenarios where many services need simultaneous data access.

__Amazon Elastic File System (Amazon EFS)__ is a scalable Linux file storage system that automatically grows and shrinks as files are added or removed. It can scale to petabytes without disrupting applications. It stores data across __multiple__ AZs.

*EBS does not scale, EFS does.*

### Amazon Relational Database Service (Amazon RDS)
__Relation Database__ stores data in a structured way that relates different pieces of data to each other. They use __SQL__ to store and query data consistently and scalably.
__Amazon Relational Database Service__ (Amazon RDS) - is a service that enables you to run relational databases in the AWS Cloud.
Amazon RDS is available on six database engines
* Amazon Aurora *It is up to five times faster than standard MySQL databases and up to three times faster than standard PostgreSQL databases.*
* PostgreSQL
* MySQL
* MariaDB
* Oracle Database
* Microsoft SQL Server

### Amazon DynamoDP
Serverless Database or __nonrelational database__. You create __Tables__ where you can store items that have attributes. Uses rigid schema to store data. So dont use if that shi changes. Quick Response time. Highly scalable.

### Amazon Redshift
__Amazon Redshift__ is a data warehousing service that you can use for big data analytics. It offers the ability to collect data from many sources and helps you to understand relationships and trends across your data. Used for past data.

### AWS Database Migration ervice (AWS DMS)
__AWS Database Migration Service__(AWS DMS) allows you to migrate relational and nonrelational databases between a source and a target database, which can be of the same or different types.
During migration, the source database stays operational, minimizing downtime. For example, you can migrate a MySQL database from an on-premises server or Amazon EC2 instance to an Amazon Aurora database using AWS DMS.
Also used for:
* Development and test database migrations
* Database Consolidation
* Continuous replication

### Additional Database Services
* __Amazon Document DB__ a document database service that supports MongoDB workloads.
* __Amazon Neptune__ a graph database service
* __Amazon Quantum Ledger Database (Amazon QLDB)__ a ledger database service. 
* __Amazon Managed Blockchain__ a service that you can use to create and manage blockchain networks with open-source frameworks. 
* __Amazon ElastiCache__ a service that adds caching layers on top of your databases to help improve the read times of common requests. Comes in Redis and Memcached
* __Amazon DynamoDB Accelerator__ an in-memory cache for DynamoDB.

*Blockchain is a distributed ledger system that lets multiple parties run transactions and share data without a central authority.*

## AWS Security
![AWS Shared Security Model](/assets/img/AWS Shared Security Model.png)

### Shared Responsibility to model
Customers are responsible for the security of everything that they create and put in the AWS Cloud.
*"When using AWS services, you, the customer, maintain complete control over your content. You are responsible for managing security requirements for your content, including which content you choose to store on AWS, which AWS services you use, and who has access to that content. You also control how access rights are granted, managed, and revoked."*

AWS is responsible for security of the cloud.

### User Permissions and Access
__AWS Identity and Access Management__ (IAM) - enables you to manage access to AWS services and resources securely.   
* __IAM users, groups, and roles__- An __IAM user__ in AWS is an identity that represents a person or application interacting with AWS services. It has a name and credentials. By default, a new IAM user has no permissions. To enable actions like launching an EC2 instance or creating an S3 bucket, you must grant the necessary permissions. An __IAM group__ is a collection of IAM users. When you assign an IAM policy to a group, all users in the group are granted permissions specified by the policy. An __IAM role__ is an identity that you can assume to gain temporary access to permissions. Its the idea that you may need to do differnt stuff ie barista or worker at different times. 
* __IAM policies__ -  is a document that allows or denies permissions to AWS services and resources. Follow the security principle of least privilege when granting permissions.   
* __Multi-factor authentication__ - provides an extra layer of security for your AWS account.

Best practice:

Do not use the root user for everyday tasks. 

Instead, use the root user to create your first IAM user and assign it permissions to create other users.

Then, continue to create other IAM users, and access those identities for performing regular tasks throughout AWS. Only use the root user when you need to perform a limited number of tasks that are only available to the root user. Examples of these tasks include changing your root user email address and changing your AWS support plan. For more information, see “Tasks that require root user credentials” in the AWS Account Management Reference Guide.

### AWS Organizations 
You can use __AWS Organizations__ to consolidate and manage multiple AWS accounts within a central location.
When you create an organization, AWS Organizations automatically creates a __root__, which is the parent container for all the accounts in your organization. 

In AWS Organizations, you can group accounts into __organizational units (OUs)__ to manage accounts with similar business or security needs. Applying a policy to an OU automatically grants the specified permissions to all accounts within that OU.

This approach helps isolate workloads with specific security requirements. For example, accounts needing regulatory compliance can be placed in one OU with a policy that restricts access to non-compliant AWS services.

### Compliance
__AWS Artifact__ is a service that provides on-demand access to AWS security and compliance reports and select online agreements. 
* __AWS Artifact Agreements__ - manage compliance agreements across accounts, addressing regulatory needs like HIPAA.
* __AWS Artifact Reports__ - provide up-to-date compliance reports, verifying AWS's security standards and helping teams understand regulatory responsibilities.

### Denial-of-service Attacks (DDoS Attacks)
The objective of a DDOS attack is to overwelm the application so that it shuts down. 
__AWS Shield__ is a service that protects applications against DDoS attacks. AWS Shield provides two levels of protection: Standard and Advanced.
__AWS Shield Standard__ automatically protects all AWS customers at no cost.
__AWS Shield Advanced__ is a paid service that provides detailed attack diagnostics and the ability to detect and mitigate sophisticated DDoS attacks. 

### Additional Security Services
__AWS KMS__ enables encryption using cryptographic keys with customizable access control, ensuring keys remain within AWS KMS.
__AWS WAF__ is a web application firewall that lets you monitor network requests that come into your web applications. 
__Amazon Inspector__ Automated security asseessments. It checks applications for security vulnerabilities and deviations from security best practices.
__Amazon GuardDuty__ detects threats by monitoring network activity and account behavior.

### Monitoring
__Monitoring:__ Observing systems, collecting metrics, and then using data to make decisions
__Amazon CloudWatch__ is a web service that enables you to monitor and manage various __metrics__ (variables tied to your resources) and configure alarm actions based on data from those metrics.
With CloudWatch, you can create __alarms__ that automatically perform actions if the value of your metric has gone above or below a predefined threshold. 

Reduce __mean time to resolution MTTR__ and __improve Total Cost of Ownership TCO__
![Cloudwatch Dashboard](/assets/img/Cloudwatch Dashboard.png)

### AWS CloudTrail 
__AWS CloudTrail__ logs API calls, tracking caller identity, time, and source IP for auditing and security.
* Track user activities and API requests throughout your AWS infrastructure
* Filter logs to assist with operational analysis and troubleshooting
Within CloudTrail, you can also enable __CloudTrail Insights__. This optional feature allows CloudTrail to automatically detect unusual API activities in your AWS account. 

### AWS Trusted Advisor
__AWS Trusted Advisor__ is a web service that inspects your AWS environment and provides real-time recommendations in accordance with AWS best practices. The inspection includes security checks, such as Amazon S3 buckets with open access permissions.
Comparing your infrastructure to AWS best practices in five categories

### Pricing
#### It is Amazon propaganda so im skipping
__AWS Marketplace__ Has thousands of softwares you can implent for a price. Reduces the cost of ownership 

![AWS Marketplace options](/assets/img/AWS Marketplace options.png)

### AWS Cloud Adoption Framwork (AWS CAF)
__The AWS Cloud Adoption Framework (AWS CAF)__ organizes guidance into six Perspectives: Business, People, Governance (focusing on business capabilities) and Platform, Security, Operations (focusing on technical capabilities).
* __Business Perspective__ - ensures IT aligns with business needs and investments contribute to key business results. It builds a cloud adoption business case, aligning strategies and goals, with roles including business managers, finance managers, budget owners, and strategy stakeholders.
* __People Perspective__ - develops a change management strategy for cloud adoption by evaluating organizational roles, skills, and processes. It identifies gaps to prioritize training and staffing, involving roles like human resources, staffing, and people managers.
* __Governance Perspective__ - aligns IT strategy with business goals to maximize value and minimize risks. It updates staff skills and processes for cloud governance, managing cloud investments to measure outcomes, involving roles like CIOs, program managers, enterprise architects, business analysts, and portfolio managers.
* __Platform Perspective__ - provides principles for cloud solutions and migrating on-premises workloads. It uses architectural models to define and communicate IT systems and their relationships Key roles include CTOs, IT managers, and solutions architects.
* __Security Perspective__ - ensures security objectives for visibility, auditability, control, and agility. It structures security control selection and implementation, involving roles like CISO, IT security managers, and IT security analysts.
* __Operations Perspective__ - ensures IT workloads run and recover as agreed with business stakeholders. It defines operational procedures and aligns them with business needs, involving roles like IT operations managers and IT support managers.

### Migration Strategies
1. __Rehosting__ - or “lift-and-shift,” involves moving applications to the cloud without changes. It is commonly used in large legacy migrations to scale quickly and meet business needs.
2. __Replatforming__ - or “lift, tinker, and shift,” makes minor cloud optimizations for tangible benefits without changing the application’s core architecture.
3. __Refactoring/re-architecting__ - or re-architecting, involves redesigning an application using cloud-native features to improve features, scale, or performance, driven by strong business needs.
4. __Repurchasing__ - involves switching from a traditional license to a software-as-a-service (SaaS) model, such as migrating from an on-premises CRM system to Salesforce.com.
5. __Retaining__ - involves keeping critical applications in their current environment, either because they require significant refactoring or because migration can be postponed.
6. __Retiring__ - Found that as much as 10-20% of application portfolios arent even being used or already updated

### AWS Snow Family
The AWS Snow Family(opens in a new tab) is a collection of physical devices that help to physically transport up to exabytes of data into and out of AWS. 

AWS Snow Family is composed of 
* __AWS Snowcone__ - is a small, rugged, and secure edge computing and data transfer device. 
* __AWS Snowball__ - __Snowball Edge Storage Optimized__ is ideal for large-scale data migrations and local computing with 80 TB HDD storage, 1 TB SSD, 40 vCPUs, and 80 GiB memory. __Snowball Edge Compute Optimized__ is designed for machine learning and video analysis, featuring 80 TB HDD, 28 TB NVMe SSD, 104 vCPUs, 416 GiB memory, and an optional NVIDIA Tesla V100 GPU.
* __AWS Snowmobile__ - an exabyte-scale data transfer service that moves up to 100 petabytes of data per Snowmobile, which is a 45-foot ruggedized shipping container pulled by a semi-trailer truck.

### Innovations with AWS
* __Serverless applications__ - Serverless in AWS means running applications without managing servers, with AWS handling fault tolerance and availability. __AWS Lambda__ enables serverless applications by triggering functions to run code, allowing developers to focus on their product instead of server management.
* __Artificial Intelligence__ - AWS offers a variety fo stuff
* __Machine Learning__ - __Amazon SageMaker__ simplifies traditional ML development by enabling quick building, training, and deployment of ML models. It allows data analysis, problem-solving, and predictive analytics without the complexity and cost of traditional methods.

__Amazon Q Developer__ - codes along with you, pretty much it... for now

### Well-Architected Framework
The Well-Architected Framework is based on six pillars: 
* Operational excellence
* Security
* Reliability
* Performance efficiency
* Cost optimization
* Sustainability
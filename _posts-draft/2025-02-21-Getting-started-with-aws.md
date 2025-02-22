



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

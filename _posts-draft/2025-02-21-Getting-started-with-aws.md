



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






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

![How Amazon EC2 works](assets/img/How-AmazonEc2-Works.png)

### Amazon EC2 Instance Types
* __General purpose instances__ When the need for compute, memory, and networking are roughly equivalent ie:
    application servers
    gaming servers
    backend servers for enterprise applications
    small and medium databases
 * __Compute optimized instances__ ideal for compute-bound applications (math heavy) that benefit from high-performance processors. Ideal for high-performace web app gaming servers.
    *for batch processing workloads that require processing many transactions in a single group.*
* __Memory optimized instances__  ideal for high-performance databases, for large datasets in memory.
* __Accelerated computing instances__ use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs. Examples of these functions include floating-point number calculations, graphics processing, and data pattern matching.
    *ideal for workloads such as graphics applications, game streaming, and application streaming.*
* __Storage optimized instances__ are designed for workloads that require high, sequential read and write access to large datasets on local storage.

In computing, the term __input/output operations per second (IOPS)__ is a metric that measures the performance of a storage device. It indicates how many different input or output operations a device can perform in one second.

### Amazon EC2 pricing
* On-Demand - ideal for short-term, irregular workloads that cannot be interrupted
* Reserved Instances **Standard Reserved Instances:** *This option is a good fit if you know the EC2 instance type and size you need for your steady-state applications and in which AWS Region you plan to run them.*  or  __Convertible Reserved Instances:__ *If you need to run your EC2 instances in different Availability Zones or different instance types*
You are charged on-demand rates until you terminate the instance.
* EC2 Instance Savings Plans- term commitment results in savings of up to 72 percent compared to On-Demand rate
* Spot Instances- are ideal for workloads with flexible start and end times, or that can withstand interruptions
* Dedicated Hosts
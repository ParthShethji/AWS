### Aws

AWS provides us with data center to store data but lets say due to some disaster the data center brks down then they have another data center this cluster of data center is called AZ availaibility zone. 
Regions are clusters of Availability Zones. Availability Zones are clusters of data centers

![alt text](images/image.png)


IAM is a web service that enables you to manage access to your AWS account and resources. It also provides a centralized view of who and what are allowed inside your AWS account

At a fundamental level, there are three types of compute options: virtual machines, container services, and serverless.

To run these virtual machines, you install a hypervisor on a host machine. This hypervisor provisions the resources to create and run your virtual machines.In AWS, these virtual machines are called Amazon Elastic Compute Cloud or Amazon EC2.


### What Is Amazon EC2?
It allows you to provision virtual servers called EC2 instances. 

### What Is an AMI?
operating system installation is no longer your responsibility, and is instead built into the AMI that you choose.Not only does an AMI let you configure which operating system you want, you can also select storage mappings, the architecture type (such as 32-bit, 64-bit, or 64-bit ARM), and additional software installed.

EC2 instances are live instantiations of what is defined in an AMI, 


When you launch a new instance, AWS allocates a virtual machine that runs on a hypervisor. Then the AMI you selected is copied to the root device volume, which contains the image used to boot the volume. In the end, you get a server you can connect to and install packages and any additional software.

![alt text](images/image1.png)


Each AMI in the AWS Management Console has an AMI ID, which is prefixed by “ami-”, followed by a random hash of numbers and letters. These IDs are unique to each AWS region.

What Makes Up an EC2 Instance?
EC2 instances are a combination of virtual processors (vCPUs), memory, network, and in some cases, instance storage and graphics processing units (GPUs). When you create an EC2 instance, you need to choose how much you need of each of these components.

c5.large can be broken down into the following elements. 

    c5 determines the instance family and generation number. Here, the instance belongs to the fifth generation of instances in an instance family that’s optimized for generic computation.
    
    large, which determines the amount of instance capacity.


#### Instance Families

| Family               | Description                                                                                                          |
|----------------------|----------------------------------------------------------------------------------------------------------------------|
| General purpose      | Provides a balance of compute, memory, and networking resources, and can be used for a variety of workloads.          |
| Compute optimized    | Ideal for compute-bound applications that benefit from high-performance processors.                                   |
| Memory optimized     | Designed to deliver fast performance for workloads that process large data sets in memory.                            |
| Accelerated computing| Use hardware accelerators or co-processors to perform functions such as floating-point number calculations, graphics processing, or data pattern matching more efficiently than is possible with conventional CPUs. |
| Storage optimized    | Designed for workloads that require high, sequential read and write access to large data sets on local storage. They are optimized to deliver tens of thousands of low-latency random I/O operations per second (IOPS) to applications that replicate their data across different instance. |



By default, your EC2 instances are placed in a network called the default Amazon Virtual Private Cloud (VPC).  Any resource you put inside the default VPC will be public and accessible by the internet, so you shouldn’t place any customer data or private information inside of it.


![alt text](images/image2.png)


### Containerisation
.A container is a standardized unit that packages up your code and all of its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment. This makes it easy to carry workloads from one place to another, such as from development to production or from on-premises to the cloud.  
Helsp when using micro service or serivce oriented architecture, Also helps in scaling up and down


### DOCKER
Docker is a popular container runtime that simplifies the management of the entire operating system stack needed for container isolation, including networking and storage. Docker makes it easy to create, package, deploy, and run containers.
![alt text](image3.png)
Containers share the same operating system and kernel as the host they exist on, whereas virtual machines contain their operating system.


Amazon ECS is an end-to-end container orchestration service that allows you to quickly spin up new containers and manage them across a cluster of EC2 instances.
To run and manage your containers, you need to install the Amazon ECS Container Agent on your EC2 instances. This agent is responsible for communicating back to the Amazon ECS service about cluster management details.  An instance with the container agent installed is often called a container instance.


To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers. A task definition is similar to a blueprint that describes the resources you need to run that container, such as CPU, memory, ports, images, storage, and networking information.

### Kubernates
Kubernetes is a portable platform for managing containerized workloads and services

## EC2, ECS, and EKS Terminology

| Concept                  | Amazon ECS                                | Amazon EKS                     |
|--------------------------|-------------------------------------------|--------------------------------|
| Instance                 | Container instance                        | Worker node                    |
| Container                | Task                                      | Pod                            |
| Technology               | Runs on AWS native technology             | Runs on top of Kubernetes      |


### Serverless computing
### Fargate
Amazon ECS Fargate is a serverless compute engine for Amazon ECS & EKS that allows you to run containers
It  Fargate scales and manages the infrastructure
![alt text](images/image4.png)

### Lambda
serverless compute engine for Runs only on triggers that we need to set. Used for code that have runtime of less than 50 mmins


### Networking 
Networking is how you connect computers around the world and allow them to communicate with one another. 

 IPV4 NOTATION - 4 byte data - 
 ![alt text](images/image5.png)

 Classless Inter-Domain Routing (CIDR) notation. CIDR notation is a compressed way of specifying a range of IP addresses.
 ![alt text](images/image6.png)


 ### Amazon VPC 
 VPC or Virtual Private Cloud is like gate keeper, nothing can come in and out until you allow it

Once you create your VPC then you create many subnets and inside each subnet we can then create an ec2 instance inorder to get control of more granular level like can keep some subnets private and some public


Internet Gateway - Like a modem connects internet to computer, this connects internet to our vpc once created it must also be connected

Virtual Private gateway - inorder to allow traffic to flow between aws and our private institution  

Route Table - 
![alt text](images/image7.png)

#### Network ACL
Think of a network ACL as a firewall at the subnet level. A network ACL enables you to control what kind of traffic is allowed to enter or leave your subnet. VPC is for your all subnet
Network ACL’s are considered stateless, so you need to include both the inbound and outbound ports used for the protocol. If you don’t include the outbound range, your server would respond but the traffic would never leave the subnet.   


#### Security Groups
firewall called a security group. The default configuration of a security group blocks all inbound traffic and allows all outbound traffic . security groups are stateful, meaning they will remember if a connection is originally initiated by the EC2 instance or from the outside and temporarily allow traffic to respond without having to modify the inbound rules.   


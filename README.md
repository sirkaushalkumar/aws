# Amazon Web Services

## Introduction to Amazon Web Services

> One can access AWS Management Console using the [Management Console Link](https://console.aws.amazon.com/console/home)

A availability region consiste of one or more discreate data centres, each with redudantant power, metworking and connectivity housed in separate facilities.

To prevent latency, AWS provides CloudFront Delivery Network to cache the traffic and improve the experience.

AWS Features 
- Multi-tenancy & Pick up your address range
- Own Virtual Private Cloud on AWS (VPC, NACLs, Security Groups)
- Compute (EC2, Lambda, ECS, ... etc)
- Database Services (RDS, DynamoDB, RedShift, ElasticCache)
- Storage Services (EBS, S3, EFS)
- Monitoring and Logging (CloudWatch and CloudTrail)
- DNS(Domanin Name Service) (Route 53)
- Content Distribution Networks - CDN (Cloud Front)
- Security & Encryption
- Other services (Big Data, Analytics, IoT, Desktop, Virtualixzation, etc)


AWS Access Methods

- Console
- REST API
- SDKs
- CLI

### Getting Started with AWS

> Account Creation is a very simple and straightforward process, so not mentiioning the steps here.

> We can manage account ID for IAM users sign in link at IAM Dashboard.

Authentication and Authorization are different things in an AWS account. To get in, we need authentication. To execute a process or access a service, authorization is needed.

IAM Users Count have a limit. So in case of exceeding limit, we have roles. This is called securetoken service credentials, when we want to access something, we are given these and they expire after some time.

IAM Users are long lived credentials and Roles are short lived credentials.

Groups are logical grouping of users which make the administration, assigning, and revoking, and changing permissions simple.

We can also add an existing user to a group. They can have also additional permissions apart from what group has. 

> Programmatic Access is anything except AWS Management Console Access.

We can delete the group from Console with users still in being there. But apart from it, if using it through CLI or SDK, we need to remove users first. 

## VPC, Security Group, NACL, Elastic IP, NAT, VPN, VPC Perring, & D Connect

### VPC Introduction

AWS has regions. Regions has availability zones. 

Every region can have one or more VPCs and Every Availability Zone has one or more VPC Subnets

VPCs cannot span across multiple regions and VPC Subnets cannot cannot span across multiple availability zones.

VPC is a virtual network or data center inside AWS for one client, or a department in a enterprise.

The AWS Client has full control over resources and virtual compute isntances (virtual servers) hosted inside that VPC

Is similar to having your own data center inside AWS

Logically isolated from other VPCs on AWS

You can have one or more IP Address subnets inside a VPC.

A VPC is confines to an AWS regiosn and does not extend between regions.

VPC Components are:

- CIDR and IP Address subnets
- Implied Router
- Route Tables
- Internet Gateways
- Security Groups
- Network Access Control Lists (N ACLs)
- Virtual Private Gateway

IPv6 Addressing
- All IPV6 addresses are Public
- Hence, AWS allocates the IPV6 address range if you require that

### VPC Components - Implied Router and Route Tables

**Implied Router**

Inplied Router is what connects different subnets together. It is the central VPC routing function.

It connects the different AZ's together and connects the VPC to the Internet Gateway

Each subnet will have a route table the route table uses to forwrd traffic within the VPC.

The route tables will also have enteries to external destinations.

**Route Tables**

We can have upto 200 route tables per VPC

We can have up to 50 routes enteries per route table

Each subnet must be associated with only one route table at any given time.

If we do not specify a subnet to a route table association, the subnet (when created) will be associated with thr main (default) VPC table

We can change the subnet association to another route table

We can also edit ther main (default) route table if we need, but we cannot delete the main(default) route table.
- However, if we  make custom route table manually become the main route table, then we can delete the former main, as it is no longer a manin route table.

Every route table in a VPC comes with a default rule that allows all VPC Subnets to communicate with each other.
- We cannot modify or delete this rule

### IP Addressing Internet Gateway - Subnet Types

We have full control over the IP range that we create and use but it has to rfc 1918 or a public routable IP Address block that we have registered or assigned to us.

Once the VPC is created, we cannot change its CIDR block range

We can create CIDR block between /28 and /16. /28 IPs have address of length 32 bits. 28 are for subnests and 4 are for hosts, EC2 and subnets that we use. 4 means we can have 16 IP address assigned. Simlarly /16 is 16 and 16 like we had 28 and 4 for /28.

If you need a different CIDR size, create a new VPC.

The different subnets within a VPC can not overlap (basic TCP/IP rule) 

We can however expand our VPC CIDR by adding new/extra IP address ranges.

### AWS Reserved IPs in each subnet

First 4 IP addresses in each subnet and the last one are reserved by AWS.
- For eaxample if the subnet is 10.0.0.0/24
    - 10.0.0.0 is the base network
    - 10.0.0.1 is VPC Router
    - 10.0.0.2 is DNS realted
    - 10.0.0.3 is reserved for future use
    - 10.0.0.255 is the last IP which we cannot use.

### Internet Gateway

Internet Gateway is the gateway through which our VPC communicates with the Internet, and with other AWS Services.

Is a horizontally scaled, redundant, and highly available VPC component

It performs NAT (Network Address Translation)(static one-to-one) between our Private ans Public (or Elastic) IPv4 addresses.

It supports IPv4 and IPV6

### Public Subnet vs Private Subnet

### VPC Types and Introduction to Security Groups

**VPC Types**
- A Default VPC
    - created in each AWS region when an AWS account is created
    - Has default CIDR, Security Group, N ACL, and route table settings
    - Has an Internet gateway by default
- A Custom (non-default) VPC
    - Is a VPC an AWS account owner created
    - AWS user creating the custom VPC can decide the CIDR
    - Has its own default desurity group, NACL, and Route Tables
    - Does not have an Internet Gateway by defaut, one needs to be created if needed.

Security Groups

> NIC Cards in AWS are called as **Elastic Network Interface**

They are nothing but firewall which can allow or disallow traffic in and out.

Anything coming in to EC2 through ENI is inbound and anything going out is outbound

- A security group is a virtual firewall
- It contolls traffic at the virtual server (EC@ Instnace) level
    - Specifically at the virtual Network Interface Level
- Upto 5 security groups per EC2 instance interface can be applied
- **Stateful**, return traffic, of allowed inbound traffic, is allowed , even if there are no rules to allow it.
- **Can only** permit rules, **can not** deny rules.
- Implicit deny rules at the end
- Security groups are associated with EC2 instances netork interfaces
- All rules are evaluated to find a permit rule. 

- Any Virtual Server Instance (EC2) created must have a security group for it specified during its launch. One can either choose an existing one, or create a new security group during launch.
- Each VPC created will have a default security group created for it, you cannot delete a default Security Group.
- Security groups are VPC resources, hence different EC2 instances, in different availaibility zones, belonging to the same VPC, can have the same security group applied to them. 
- **Changes to security groups take effect immediately**

#### Default and non-Default Security Groups

Default Settings
- Defailt Security Group in a default VPC, will have 
    - Inbound rules allowing Instances assigned the sae security group to talk to one anotehr
    - All outbound traffic is allowed
- Custom Security groups in a VPC will always have 
    - No inbound rules - basically all inbound tradffic is denied by default.
    - All outnound traffic is allowed by default.

... to be continued


## Elastic Compute Cloud

- EC2 service provides resizable compute capacity in the cloud
- We have root access to each of our EC2 isntances
- We can stop, restart, reboot or terminate our instance
- EC2 availability SLA is 99.5% for each region during any monthly billing period
    - ~22 minutes per month
- We can provison our EC2 instances on shared or dedicated hosts (physical servers)
- To access an instance we need a key and a key pair name
    - When we launch a new EC2 instance, we can create a public/private key pair
    - We can download the private key only once
        - We should save it at safe place so we won't loose it
    - The public key is saved by AWS to match it yo a key pair name, and a private key when we try tomlogin to the EC2 instance.
    - If we launch a instance without a key pair, we will not be able to access it (via RDP or SSH)
There is a 20EC2 instances soft limit per account, we can submit a request to AWS to increase it.
- Two types of Block Storage devices are supportted
    - Elastic Block Store (EBS)
        - Persistent
        - network attached virtual drives (e.g. root volume and data volume)
    - Instance-store
        - Basically teh virtual hard drive on the host allocated to this EC2 instance
        - Limited to 10 GB per instance
    - EC2 instance root/boot volumes can be EBS or Instance Store Volumes
    - EBS-backed EC2 instance
        - It has a EBS root volume
    - Instance-store backed EC2 instnace
        - It has an Instnace-store root volume
- EC2 Instance families
    - General Purpose
        - Balanced memory and CPU
        - Suitable for most applicaytions
        - Ex. M3, M4, T2
    - Compute Optimized
        -   More CPU than memory
        - Compute & HPC intensive use
        - Ex. C2, C4
    - Memory Optimized
        - More RAM/memory
        - Memory intensive apps, DB, and caching
        - Ex. R3, R4
    - GPU compute instances
        - Graphics Optimized
        - High Performance and parallel computing
        - Ex. G2
    - Storage Optimized
        - Very Ligh, low latency, I/O
        - I/O intensive apps, data warehousing, Hadoop
        - Ex I2, D2

- EBS Types
    - General Purpose
        - SSD-Backed (Solid State Devices)
        - Are better for transactional workloads such as **small databases & boot volumes, Dev/Test environments, Low latency Interactive apps** where performance is highly dependent on IOPS
        - Volume sizes 1 TiB - 16 TiB (Tibibyte = TiB = 2 to the power 40)
        - Max IOPS, 10,000
    - Provisioned IOPS
        - SSD-backed
        - Use for mission critical applications and I/O intensive SQL/NoSQL adtabases
        - Provides sustainable IOPS performance & Low Latency
        - Max IOPS/Volume, 32,000 IOPS
        - Volume sizes 4 TiB - 16 TiB
    - Throughput Optimized HDD
        - Ideal for streaming, big data, log processing, and data warehousing
        -  Can not be used as a boot volume
        - Used for frequently accessed, throughput intensive workloads
        - Size 500GiB - 16GiB
    - Cold HDD
        - Ideal for less frequently accessed workloads
        - Can not be the boot volume
        - Size 500GiB - 16 GiB
    - Magnetic EBS
        - For transactional workloads, where performance is not dependent on IOPS, rather on MB/Sec transfer rates
        - HDD backed
        - Use for infrequently accessed data
        - Volume sizes 1GiB - 16GiB
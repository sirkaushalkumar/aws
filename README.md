# aws

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

## Getting Started with AWS

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

## VPC Components - Implied Router and Route Tables

Inplied Router is what connects different subnets together. It is the central routing function.

It connects the different AZ's together and connects the VPC tp the Internet Gateway

Each subnet will have a route table the route table uses to forwrd traffic within the VPC.

The route tables will also have enteries to external destinations.

We can have upto 200 route tables per VPC

We can have up to 50 routes enteries per route table


## Amazon EC2

Amazon EC2 is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing us to quickly scale capacity, both up and down, as our computing requirements change.

EC2 Pricing Models

| _S. No._| _Type_ | _Description_ |
|---|---|---|
|1.| **OnDemand**| Allows us to pay a fixed rate by the hour <br/> (or by the second) with no commitment |
|2.| **Reserved**|  Provides us with a capacity reservation, and offer <br/> a significant discount on the hourly charge  for an <br/>instance. Contract Terms ate 1 Year and 3 Year Terms|
|3.| **Spot**| Enables us to bid whatever price we wantfor instance <br/>capacity, providing for even greated savings if our  <br/>applications have flexible start and end times |
|4.| **Dedicated Hosts**| Physical EC2 server dedicated for our use.Dedicated  <br/> Hosts can help us reduce costs by allowing us to use<br/> our existing server-bound software licenses |

On Demand pricing is useful for 
- Users that want the low cost and flexibility of Amazon EC2 without any up-front paymentor long term commitment
- Applications with short tem, spiky, or unpredicatb;e workloads that cannot be interrupted
- Applications being developed or tested on Amazon EC2 for the first time.

Reserved pricings is useful for:
- Applications with steady state or predicatble usage
- Applications that require reserved capacity
- Users able to make upfront payments to reduce their total computing costs even further.

Reserved Pricing types:
- **Standard Reserved Instances** - These offer upto 75% off on demand isntances. The more we pay up front and longer the contract, the greater the discount
- **Convertible Reserved Instances** - These offer up to 54% off on demand capability to change the attributes of the RI as long as  the exchange results in the creation of Reserved Instances or equal or greater value
- **Scheduled Reserved Instances** - These are available to launch within the time windows we reserve. This option allows us to match our capacity reservation to a predicatable recurring schedule that only requires a fraction of a day, a week, or a month

Spot pricing is useful for:
- Applications that have flexible start and end times
- Applications that are only feasible at very low compute prices
- Users with urgent computing needs for large amounts of additional capacity.

Dedicated Hosts priving is useful for
- Useful for regulatory requiremnets thar may not support multi-tenant virtualization
- Great for licensing which does not support multi-tenacy or cloud deployments
- can be purchased On-Demand (hourly)
- Can be purchased as Reservation for up to 70% off on the On-Demad price.
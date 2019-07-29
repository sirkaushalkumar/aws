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

> Account Creation is a very simple and straightforward process, so not mentiioning the steps here.

> We can manage account ID for IAM users sign in link at IAM Dashboard.

Authentication and Authorization are different things in an AWS account. To get in, we need authentication. To execute a process or access a service, authorization is needed.

IAM Users Count have a limit. So in case of exceeding limit, we have roles. This is called securetoken service credentials, when we want to access something, we are given these and they expire after some time.

IAM Users are long lived credentials and Roles are short lived credentials.

Groups are logical grouping of users which make the administration, assigning, and revoking, and changing permissions simple.

We can also add an existing user to a group. They can have also additional permissions apart from what group has. 

> Programmatic Access is anything except AWS Management Console Access.

We can delete the group from Console with users still in being there. But apart from it, if using it through CLI or SDK, we need to remove users first. 
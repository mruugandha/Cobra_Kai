# COBRA KAI
     After proposing hosting of the Cobra Kai application on the Amazon Web Services (AWS), I would like to give a walkthrough for the services that can be used to successfully migrate the application in the cloud. This migration will make the application more secure and sturdy and can help in reducing IT costs, and enabling benefits like application scalability and many more.
<img width="821" alt="Screen Shot 2021-03-06 at 11 39 39 AM" src="https://user-images.githubusercontent.com/54558744/110218668-f53d0100-7e88-11eb-92ad-2e62eb60f903.png">

     This was a high-level representation of how the Cobra Kai application will look after migrating it to AWS. Considering the current issues, the document will describe use of several services provided by AWS to overcome those issues and make the application more resilient and highly secure.
 
#### For Migrating the Cobra Kai Application to AWS we need to follow the below mentioned steps:

     1. Assess cloud migration strategies and readiness.
     2. Discover portfolio and plan for migration.
     3. Plan and design application migration strategy.
     4. Perform and validate application migration to the cloud.
     5. Optimize applications and operations after migration

### Tools Used to implement the services in order to overcome the current issues in Cobra Kai Application are as follows:
## Problem 1: Patching Strategy
## Patch Management:
         Patch management is the process of distributing and applying updates to software.These patches are regularly important to address mistakes (likewise alluded to as "weaknesses" or "bugs") in the product. At the point when a weakness is found after the arrival of a bit of programming, a patch can be utilized to fix it.

## Patch Management Life Cycle:

    1. Update vulnerability details from software vendors.
    2. Scan the enterprise network for vulnerability.
    3. Examine the Vulnerability and identify the missing patches.
    4. Deploy patches and validate patch installation.
    5. Produce Status Report on the most recent patch updates.

## Recommendation:
         For the Kobra Kai application, we can make use of AWS System Manager that will help in providing a unified user interface, so that we can view the operational data from the multiple AWS services. System Manager can help in grouping resources like the EC2 instance and the S3 buckets, therefore here in the case of occurrence of malfunctioning in the availability zone A and B, Amazon S3 buckets will have the backup data.
         
### Process of patching by AWS System Manager:
#### How it works:
Screen Shot 2021-03-06 at 2.48.33 PM![image](https://user-images.githubusercontent.com/54558744/110219079-156dbf80-7e8b-11eb-9491-0e381ddac5a7.png)

 
#### Using patch baselines:
    A patch baseline defines which patches ought to and shouldn't be introduced on your instances.​ We can specify approved or rejected patches one after another. We can also create an auto-approval rule to specify that certain types of updates (for example, critical updates) should be automatically approved.
    
    Patch Manager has a pre-characterized (default) patch standard:
    Screen Shot 2021-03-06 at 2.49.45 PM![image](https://user-images.githubusercontent.com/54558744/110219116-4ea62f80-7e8b-11eb-9925-d73cd0c36d5c.png)

#### Creating a patch baseline:
    We can make our own custom patch baselines, here we can pick which patches to auto-support by using the Operating system, Product name, Classification and Severity.
 
#### Patch groups:
    Patch group is a discretionary method for characterizing which patch pattern should be utilized for what occurrences. For instance, one can establish patch groups for various conditions, for example, development, test, and production. One can likewise make essential and optional failover bunch groupings
#### Maintenance Windows:
    AWS Systems Manager Maintenance Windows lets you characterize a schedule for when to perform possibly troublesome activities on your instances, for example, patching an operating system (OS), refreshing drivers, or installing software.
    
#### Created AWS EC2 instance:
Screen Shot 2021-03-06 at 3.01.56 PM![image](https://user-images.githubusercontent.com/54558744/110219410-0556df80-7e8d-11eb-85fe-b76722ba41d7.png)

#### Baseline ID:
 Screen Shot 2021-03-06 at 3.03.10 PM![image](https://user-images.githubusercontent.com/54558744/110219423-21f31780-7e8d-11eb-89ee-147c4f66ed5e.png)

#### Patch Manager:
Screen Shot 2021-03-06 at 3.04.12 PM![image](https://user-images.githubusercontent.com/54558744/110219444-4c44d500-7e8d-11eb-8ad7-4acef4839e34.png)

#### Creating a baseline
 Screen Shot 2021-03-06 at 3.04.12 PM![image](https://user-images.githubusercontent.com/54558744/110219462-6979a380-7e8d-11eb-83a4-44a39c50cfb1.png)

#### Creating Maintenance Window:
  Screen Shot 2021-03-06 at 3.06.00 PM![image](https://user-images.githubusercontent.com/54558744/110219483-801ffa80-7e8d-11eb-9a88-9a2e10bcc5e1.png)

## Problem 2: DDoS Attack Prevention Distributed denial-of-service Attack:
    A distributed denial-of-service (DDoS) attack is a malicious attempt to disrupt the normal traffic of a targeted server, service or network by overwhelming the     target or its surrounding infrastructure with a flood of Internet traffic.
     
#### Recommendation:
     In the case of any DDoS attacks by the rivals, AWS shield advanced will help our application to withstand that attack. AWS shield advanced provides customized      detection based on the traffic patterns in our protected elastic IP address. AWS Shield Advanced accompanies DDoS cost insurance, to protect against scaling        charges coming about because of DDoS-related utilization spikes.. It is integrated with AWS WAF, that is a web-application firewall.
     
#### AWS shield advanced:
#### Tailored detection based on application traffic patterns:
    AWS Shield Advanced provides customized detection based on traffic patterns to your protected Elastic IP address, Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator or Amazon Route 53 resources. Using additional region- and resource-specific monitoring techniques, AWS Shield Advanced detects and alerts you of smaller DDoS attacks.
    
#### Advanced attack mitigation:
    AWS Shield Advanced provides more sophisticated automatic mitigations for attacks targeting your applications running on protected Amazon Elastic Compute Cloud     (EC2), Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator, and Amazon Route 53 resources.
#### Elastic Load Balancing:
    Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as Amazon Elastic Compute Cloud (Amazon EC2)           instances, containers, and IP addresses, and multiple Availability Zones, which minimizes the risk of overloading a single resource.
#### DNS Route 53:
    One of the most common targets of DDoS attacks is the Domain Name System (DNS). Amazon Route 53 is a highly available and scalable DNS service designed to         route end users to infrastructure running inside or outside of AWS. Route 53 makes it possible to manage traffic globally through a variety of routing types       and provides out-of-the box shuffle sharding and Anycast routing capabilities to protect domain names from DNS-based DDoS attacks.
Screen Shot 2021-03-06 at 3.07.28 PM![image](https://user-images.githubusercontent.com/54558744/110219517-b3fb2000-7e8d-11eb-8cc3-48600b8fbd89.png)

 
 ##  Problem 3: Slow streaming, Downloads and order processing:
#### Recommendation:
    In the event of slow streaming and downloading of data and videos, Amazon CloudFront, a fast Content Delivery Network (CDN) service, helps in securely             delivering data, videos and applications and APIs to customers globally with low latency and high transfer speed.Customers will have easy access to the data       without any interruptions. AWS CloudFront works smoothly with other services like Amazon S3 and Elastic Load Balancing.
## Amazon CloudFront:
    Amazon CloudFront distributes traffic across multiple edge locations and filters requests to ensure that only valid HTTP(S) requests will be forwarded to           backend hosts. CloudFront also supports geo-blocking, which you can use to prevent requests from particular geographic locations from being served.
#### Amazon CloudFront Key Features:
    1. Faster Performance. Network optimizations for optimal performance.
    2. Security protection against Network and Application Layer Attacks.
    3. Programmable and DevOps Friendly full-featured APIs and DevOps Tools.
    4. Cost effective pay-as-you-go publicly available pricing and discounted pricing.
 Screen Shot 2021-03-06 at 3.08.56 PM![image](https://user-images.githubusercontent.com/54558744/110219561-fde40600-7e8d-11eb-9f6e-3f41d5468515.png)

#### CloudFront delivers content to your users:
Screen Shot 2021-03-06 at 3.10.05 PM![image](https://user-images.githubusercontent.com/54558744/110219570-1ce29800-7e8e-11eb-9f41-7eaef5c01fdd.png)

## Problem 4: Account Permission
#### Account Permission Strategy:
    It is an approach intended to offer approval to various clients that empowers them to get to explicit assets on the organization, for example, information         records, applications, printers and scanners.
#### Recommendation:
    Currently every user group has the ability to run the privileged commands on the web server if they want to, but that is highly insecure and thus we should         have a good account permission strategy. Use of AWS Identity & Access Management (IAM) will allow us to manage access to AWS services and resources securely.
#### AWS Identity & Access Management (IAM):
    AWS Identity and Access Management, helps you set up users and groups, and shows you how to protect your resources with access control policies. Also shows how     to connect to other identity services to grant external users access to your AWS resources.
#### Working of IAM for securing resources on AWS:
    Using IAM, we can create and manage several user groups and according to their different user roles, they will be given access to various services in AWS.
    IAM allows us to:
    1. Manage IAM users and their access – We can create users in IAM, assign them individual security credentials (in other words, access keys, passwords, and            multi-factor authentication devices), or request temporary security credentials to provide users access to AWS services and resources.
    2. Manage IAM roles and their permissions​ – We can create roles in IAM and manage permissions to control which operations can be performed by the entity, or          AWS service, that assumes the role. We can also define which entity is allowed to assume the role.
    3. Manage federated users and their permissions –​ You can enable identity federation to allow existing identities (users, groups, and roles) in your                  enterprise to access the AWS Management Console, call AWS APIs, and access resources, without the need to create an IAM user for each identity.
#### Creating a User:
Screen Shot 2021-03-06 at 3.11.25 PM![image](https://user-images.githubusercontent.com/54558744/110219591-43083800-7e8e-11eb-9c1b-cf36290092f3.png)

 #### Adding Permissions:
 Screen Shot 2021-03-06 at 3.12.04 PM![image](https://user-images.githubusercontent.com/54558744/110219604-57e4cb80-7e8e-11eb-91f2-a3f02e10cb69.png)

  #### Roles can be created:
  Screen Shot 2021-03-06 at 3.12.49 PM![image](https://user-images.githubusercontent.com/54558744/110219636-75199a00-7e8e-11eb-86b0-465de771dd20.png)

#### Setting up MFA for IAM user:
 Screen Shot 2021-03-06 at 3.13.44 PM![image](https://user-images.githubusercontent.com/54558744/110219667-b0b46400-7e8e-11eb-9d57-d227e31c21ee.png)

 #### Admin Policies:
 Screen Shot 2021-03-06 at 3.15.06 PM![image](https://user-images.githubusercontent.com/54558744/110219685-c590f780-7e8e-11eb-86c8-8999e4331403.png)

#### Network Engineer Policies:
Screen Shot 2021-03-06 at 3.15.40 PM![image](https://user-images.githubusercontent.com/54558744/110219704-d80b3100-7e8e-11eb-8a0d-6be6feaf3bbf.png)

  
## Problem 5: Backup Strategy
#### Why do we need a backup Strategy-
    Backup Strategy is storing copies of data so that, in the case of loss or damage of the original data we can utilize the extra copies of data that is stored in backup.
#### Recommendation:
    In case of break-down in the VPC(Virtual Private Cloud), AWS Backup service will be used.
#### AWS Backup:
    AWS Backup, is a fully managed backup service that makes it easy to centralize and automate the backup of data across AWS services.It helps in automating the backup process and saves time and money.
    Benefits of AWS Backup:
    1. Centrally manage backups
    2. Automate backup processes
    3. Improve backup compliance
Screen Shot 2021-03-06 at 3.16.18 PM![image](https://user-images.githubusercontent.com/54558744/110219764-17d21880-7e8f-11eb-9adf-7f2c619fd316.png)

#### Creating a Backup Plan:
     AWS Console -> AWS Backup -> Create Backup plan. In which we can define rules, retention period, region, and other options as per need
   Screen Shot 2021-03-06 at 3.16.37 PM![image](https://user-images.githubusercontent.com/54558744/110219775-31736000-7e8f-11eb-8ca5-58285445b87b.png)
   Screen Shot 2021-03-06 at 3.16.51 PM![image](https://user-images.githubusercontent.com/54558744/110219784-3c2df500-7e8f-11eb-8547-27beedc24cba.png)

 ## Problem 6: Personal Information
 #### Recommendation:
    In order to keep the sensitive information of the users safe, ​Amazon Macie service​ is used. It uses machine Learning and pattern learning to discover and protect the user data.Amazon Macie is linked to the S3 buckets, where it applies techniques to these buckets in order to identify and alert about any sensitive data, such as personally identifiable information (PII).
#### Amazon Macie features:
    Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
 
#### Features of Amazon Macie:
    1. Detailed and actionable security and sensitive data discovery findings
    2. Custom-defined sensitive data types
    3. One-click deployment with no upfront data source integration
    4. Multi-account support and integration with AWS Organizations
    5. Fully managed sensitive data types
#### After enabling Amazon Macie:
Screen Shot 2021-03-06 at 3.19.10 PM![image](https://user-images.githubusercontent.com/54558744/110219810-6089d180-7e8f-11eb-9bca-af8ac10dcb40.png)

#### S3 Bucket:
Screen Shot 2021-03-06 at 3.19.21 PM![image](https://user-images.githubusercontent.com/54558744/110219814-667fb280-7e8f-11eb-9da4-0f2a469c4c21.png)

 

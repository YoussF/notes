# **AWS Services**
## **Compute Services**

### **AWS Lambda**
With AWS Lambda, you can run code without provisioning or managing servers. You pay only for the compute time that you consume—there's no charge when your code isn't running. You can run code for virtually any type of application or backend service—all with zero administration. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app.
**The cost of running Lambda for your workload is determined by three factors: the number of executions, the duration and memory usage (combined as Gb/s), and data transfer.**
<br>

### **AWS Auto Scaling**
AWS provides multiple services that you can use to scale your application. Auto scaling is enabled by Amazon CloudWatch and is available at no additional charge beyond the service fees for CloudWatch and the other AWS resources that you use.
<br>

### **AWS Elastic Beanstalk**
AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.
<br>

### **Amazon Elastic Compute Cloud (EC2)**
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable computing capacity—literally, servers in Amazon's data centers—that you use to build and host your software systems. See also: [Amazon Machine Images (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
<br>

## **Containers**

### **Amazon Elastic Container Service (ECS)**
Amazon Elastic Container Service (Amazon ECS) allows you to easily deploy containerized workloads on AWS. The powerful simplicity of Amazon ECS enables you to grow from a single Dock  er container to managing your entire enterprise application portfolio. Run and scale your container workloads across availability zones, in the cloud, and on-premises, without the complexity of managing a control plane or nodes.
<br>

### ***Amazon Elastic Container Registry (ECR)**
Easily store, manage, and deploy container images
<br>

### **Amazon Elastic Kubernetes Service**
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed Kubernetes service that makes it easy for you to run Kubernetes on AWS and on-premises.
<br>

## **Security, Indentity, and Compliance Services**

### **AWS CloudHSM**
AWS CloudHSM offers secure cryptographic key storage for customers by providing managed hardware security modules in the AWS Cloud.
<br>

### **AWS WAF**
AWS WAF is a web application firewall that lets you monitor web requests that are forwarded to Amazon CloudFront distributions or an Application Load Balancer. You can also use AWS WAF to block or allow requests based on conditions that you specify, such as the IP addresses that requests originate from or values in the requests.
<br>

### **AWS Shield**
AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS. AWS Shield provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection. There are two tiers of AWS Shield - Standard and Advanced.
<br>

### **AWS Directory Service**
AWS Directory Service provides multiple ways to set up and run Microsoft Active Directory with other AWS services such as Amazon EC2, Amazon RDS for SQL Server, FSx for Windows File Server, and AWS Single Sign-On. AWS Directory Service for Microsoft Active Directory, also known as AWS Managed Microsoft AD, enables your directory-aware workloads and AWS resources to use a managed Active Directory in the AWS Cloud.
<br>

### **AWS Identity & Access Management (IAM)**
AWS Identity and Access Management (IAM) is a web service for securely controlling access to AWS services. With IAM, you can centrally manage users, security credentials such as access keys, and permissions that control which AWS resources users and applications can access.

Note: Access key per IAM user is required for AWS CLI
<br>

### **AWS Key Management Service**
AWS Key Management Service (AWS KMS) is an encryption and key management service scaled for the cloud. AWS KMS keys and functionality are used by other AWS services, and you can use them to protect data in your own applications that use AWS.
<br>

### **Amazon GuardDuty**
Amazon GuardDuty is a continuous security monitoring service. Amazon GuardDuty can help to identify unexpected and potentially unauthorized or malicious activity in your AWS environment.
<br>

### **AWS Artifact**
AWS Artifact is a web service that enables you to download AWS security and compliance documents such as ISO certifications and SOC reports.
<br>


## **Storage Services**

### **AWS Snowball (Part of Snow Family)**
Petabyte-scale data transport with on-board storage and compute capabilities
[Read more](https://aws.amazon.com/snowball/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc)
<br>

### **Amazon S3**
Amazon Simple Storage Service (Amazon S3) is storage for the internet. You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere on the web.
**important:**
- S3 is capable of hosting static websites
- Amazon S3 Reduced Redundancy Storage : Reduced Redundancy Storage (RRS) is an Amazon S3 storage option that enables customers to store noncritical, reproducible data at lower levels of redundancy than Amazon S3’s standard storage.
<br>

### **Amazon S3 Glacier**
The Amazon S3 Glacier storage classes are purpose-built for data archiving, providing you with the highest performance, most retrieval flexibility, and the lowest cost archive storage in the cloud. All S3 Glacier storage classes provide virtually unlimited scalability and are designed for 99.999999999% (11 nines) of data durability. The S3 Glacier storage classes deliver options for the fastest access to your archive data and the lowest-cost archive storage in the cloud.
<br>

### **Amazon Elastic File System**
Amazon EFS provides file storage for your Amazon EC2 instances. With Amazon EFS, you can create a file system, mount the file system on your EC2 instances, and then read and write data from your EC2 instances to and from your file system.
<br>

### **Amazon Elastic Block Store**
Amazon Elastic Block Store (Amazon EBS) is a web service that provides block level storage volumes for use with Amazon Elastic Compute Cloud instances. Amazon EBS volumes are highly available and reliable storage volumes that can be attached to any running instance and used like a hard drive.
<br>

### **AWS Storage Gateway**
AWS Storage Gateway is a service that connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between your on-premises IT environment and the AWS storage infrastructure in the cloud.
<br>


## **Migration Services**

### **AWS Database Migration Service (DMS)**
AWS Database Migration Service (AWS DMS) helps you migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database. The AWS Database Migration Service can migrate your data to and from the most widely used commercial and open-source databases.
<br>

### **Migration Evaluator**
Creating a business case on your own can be a time-consuming process and does not always identify the most cost-effective options. A business case is the first step in your migration journey. With Migration Evaluator (Formerly TSO Logic), you can gain access to insights and accelerate decision-making for migration to AWS at no cost. Following data collection, you will quickly receive an assessment including a projected cost estimate and savings of running your on-premises workloads in the AWS Cloud.
<br>

## **Database Services**

### **Amazon ElastiCache**
Amazon ElastiCache makes it easy to set up, manage, and scale distributed in-memory cache environments in the AWS Cloud. It provides a high performance, resizable, and cost-effective in-memory cache, while removing complexity associated with deploying and managing a distributed cache environment. ElastiCache works with both the Redis and Memcached engines; to see which works best for you, see the Comparing Memcached and Redis topic in either user guide.
<br>

### **Amazon Relational Database Service**
Amazon Relational Database Service (Amazon RDS) is a web service that makes it easier to set up, operate, and scale a relational database in the cloud. It provides cost-efficient, resizable capacity for an industry-standard relational database and manages common database administration tasks.
<br>

### **AWS DynamoDB**
Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. You can use Amazon DynamoDB to create a database table that can store and retrieve any amount of data, and serve any level of request traffic. Amazon DynamoDB automatically spreads the data and traffic for the table over a sufficient number of servers to handle the request capacity specified by the customer and the amount of data stored, while maintaining consistent and fast performance.
<br>

### **Amazon Aura**
Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases.

Amazon Aurora is up to five times faster than standard MySQL databases and three times faster than standard PostgreSQL databases. It provides the security, availability, and reliability of commercial databases at 1/10th the cost. Amazon Aurora is fully managed by Amazon Relational Database Service (RDS), which automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.
<br>


## **Networking and Content Delivery Services**

### **Amazon CloudFront**
Amazon CloudFront speeds up distribution of your static and dynamic web content, such as .html, .css, .php, image, and media files. When users request your content, CloudFront delivers it through a worldwide network of edge locations that provide low latency and high performance.
<br>

### **Amazon Route 53**
Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service.
<br>

### **AWS Virtual Private Network**
AWS Virtual Private Network (AWS VPN) establishes a secure and private tunnel from your network or device to the AWS Cloud. You can extend your existing on-premises network into a VPC, or connect to other AWS resources from a client. AWS VPN offers two types of private connectivity that feature the high availability and robust security necessary for your data.
<br>

### **AWS Direct Connect**
AWS Direct Connect establishes a dedicated network connection between your on-premises network and AWS. With this connection in place, you can create virtual interfaces directly to the AWS Cloud, bypassing your internet service provider. This can provide a more consistent network experience.
<br>

### **Elastic Load Balancing**
Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. It monitors the health of its registered targets and routes traffic only to the healthy targets. You can select the type of load balancer that best suits your needs.
<br>

### **Amazon VPC**
Amazon Virtual Private Cloud (Amazon VPC) enables you to provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you've defined.
<br>

## **Management & Governance Services**

### **AWS Organizations**
With AWS Organizations, you can consolidate multiple AWS accounts into an organization that you create and centrally manage. You can create member accounts and invite existing accounts to join your organization. You can organize those accounts and manage them as a group. With AWS Account Management you can update the alternate contact information for each of your AWS accounts.
<br>

### **AWS Control Tower**
AWS Control Tower is a service that enables you to enforce and manage governance rules for security, operations, and compliance at scale across all your organizations and accounts in the AWS Cloud.
<br>

### **CloudFormation**
AWS CloudFormation enables you to create and provision AWS infrastructure deployments predictably and repeatedly. It helps you leverage AWS products such as Amazon EC2, Amazon Elastic Block Store, Amazon SNS, Elastic Load Balancing, and Auto Scaling to build highly reliable, highly scalable, cost-effective applications in the cloud without worrying about creating and configuring the underlying AWS infrastructure. AWS CloudFormation enables you to use a template file to create and delete a collection of resources together as a single unit (a stack).
<br>

### **AWS Config**
AWS Config provides a detailed view of the resources associated with your AWS account, including how they are configured, how they are related to one another, and how the configurations and their relationships have changed over time.
<br>
 
### **Amazon CloudWatch**
Amazon CloudWatch is a monitoring and observability service built for DevOps engineers, developers, site reliability engineers (SREs), IT managers, and product owners. CloudWatch provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, and optimize resource utilization. CloudWatch collects monitoring and operational data in the form of logs, metrics, and events. You get a unified view of operational health and gain complete visibility of your AWS resources, applications, and services running on AWS and on-premises.
<br>

### **AWS OpsWorks**
AWS OpsWorks is a configuration management service that provides managed instances of Chef and Puppet. Chef and Puppet are automation platforms that allow you to use code to automate the configurations of your servers. OpsWorks lets you use Chef and Puppet to automate how servers are configured, deployed, and managed across your Amazon EC2 instances or on-premises compute environments. OpsWorks has three offerings, AWS Opsworks for Chef Automate, AWS OpsWorks for Puppet Enterprise, and AWS OpsWorks Stacks.

### **AWS CloudTrail**
With AWS CloudTrail, you can monitor your AWS deployments in the cloud by getting a history of AWS API calls for your account, including API calls made by using the AWS Management Console, the AWS SDKs, the command line tools, and higher-level AWS services. You can also identify which users and accounts called AWS APIs for services that support CloudTrail, the source IP address from which the calls were made, and when the calls occurred. You can integrate CloudTrail into applications using the API, automate trail creation for your organization, check the status of your trails, and control how administrators turn CloudTrail logging on and off.
<br>

### **AWS Personal Health Dashboard**
AWS Personal Health Dashboard provides a personalized view of the health of AWS services, and alerts when your resources are impacted. Also includes the AWS Health API for integration with your existing management systems.
<br>

### **AWS Trusted Advisor**
AWS Trusted Advisor provides you real time guidance to help you provision your resources following AWS best practices. Trusted Advisor checks help optimize your AWS infrastructure, increase security and performance, reduce your overall costs, and monitor service limits. Seven core checks are included with Developer Support.
<br>

## **Analytics**

### **Amazon EMR**
Amazon EMR is a web service that makes it easy to process vast amounts of data efficiently using Apache Hadoop and services offered by Amazon Web Services.
<br>

## **Developer Tools**

### **AWS CodeCommit**
AWS CodeCommit is a version control service that enables you to privately store and manage Git repositories in the AWS Cloud
<br>

### **AWS CodeDeploy**
AWS CodeDeploy is a deployment service that enables developers to automate the deployment of applications to instances and to update the applications as required.
<br>

### **AWS CodeArtifact**
AWS CodeArtifact is a secure, scalable, and cost-effective artifact management service for software development.
<br>

## **AWS Cost Management Services**

### **AWS Cost Explorer**
AWS Cost Explorer has an easy-to-use interface that lets you visualize, understand, and manage your AWS costs and usage over time.
<br>

## **Machine Learning Services**

### **Amazon Macie**
Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover, classify, and help you protect your sensitive data in Amazon S3.
<br>

### **AWS CodeGuru**
CodeGuru provides intelligent recommendations for improving application performance, efficiency, and code quality in your Java applications.
<br>

### **AWS DeepLens**
AWS DeepLens helps put machine learning in the hands of developers, literally, with a fully programmable video camera, tutorials, code, and pre-trained models designed to expand deep learning skills.
<br>

### **AWS Alexa Skills**
Skills are like apps for Alexa, and provide a new channel for your content and services. Skills let customers use their voices to perform everyday tasks like checking the news, listening to music, playing a game, and more. Organizations and individuals can publish skills in the Alexa Skills Store to reach and delight customers on hundreds of millions of Alexa devices.
<br>

## **Unclassified Services**

### **AWS Marketplace**
AWS Marketplace is a curated digital catalog that makes it easy for organizations to discover, procure, entitle, provision, and govern third-party software. You can find thousands of software listings from popular categories like security, business applications, and data & analytics, and across specific industries, such as healthcare, financial services, and public sector. You can also explore and buy professional services to configure, deploy, and manage your third-party software.
<br>

### **AWS Professional Services**
Adopting the AWS Cloud can provide you with sustainable business advantages. Supplementing your team with specialized skills and experience can help you achieve those results. The AWS Professional Services organization is a global team of experts that can help you realize your desired business outcomes when using the AWS Cloud. We work together with your team and your chosen member of the AWS Partner Network (APN) to execute your enterprise cloud computing initiatives.
<br>

### **AWS Service Health Dashboard**
Amazon Web Services publishes our most up-to-the-minute information on service availability
<br>

## **Other Tools**

### **AWS Pricing Calculator**
AWS Pricing Calculator is a web service that you can use to create cost estimates that match your AWS use case. AWS Pricing Calculator is useful both for people who have never used AWS and for those who want to reorganize or expand their usage.
<br>

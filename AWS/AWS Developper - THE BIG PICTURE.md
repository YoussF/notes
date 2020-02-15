# AWS Developper - The big picture



## What is AWS ?
1. Amazon Web Services (AWS) is a subsidiary of Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered pay-as-you-go basis
2. AWS is the world leader in cloud computing service, Netflix, Amazon, Airbnb, Yelp, Expedia uses AWS to run there business.
3. AWS comprises of a multitude of individual service is that interact and work in an incredibly complex number of ways.
### L'énigme de l'application Web
- Application installé sur l'ordinateur.
- Application Web Hébergé sur un serveur connecté a internet.
- Lisa à développer une Application Web hébergé dans le plaquart, problème maitenance, charges, etc.. bilant, perte d'argent.
- Gary est développeur chez BIG compagny et il est contraint à la lenteure de la machine burocratique à chaque fois qu'il a un besoin d'une VM, en plus il est forcer de partager le cluster interne avec tant d'autres equipes de developpement que la qualité de service des applications qu'il développe s'en retrouve impacté.

### Hello Amazon Web Services
### Tracing the global infrastructure of AWS
### How does AWS work ?
### AWS vs the rest.
### Conclusion



## Understanding the core services of AWS
- **Amazon EC2**:

    Forget the expensive physical servers with this Amazon service that allows us to create virtual machines and manage other features of servers; such as storage, security, ports, etc. With Amazon EC2 you can create servers in minutes with your preferred operating system.

    This way you will have more time to take care of your projects and spend less time maintaining your servers.

- **Amazon S3**:

    What happens to my data in the cloud? Well, Amazon S3 gives us relief when we talk about data, because they have an incredibly secure infrastructure. In addition to intelligently distributing data in different physical regions, they also have integrations such as PCI-DSS, HIPAA / HITECH, FedRAMP, our data will never be compromised.

    That is all?

    Of course not, AWS S3 also has high availability, so accessing your information is just a click away, with almost zero latency of 99.9999999999%. Surely now you wonder how expensive this service is? Well, we are pleased to inform you that it is impressively cheap. First, it has a free layer that includes 5 GB of storage and then starts at the cost of $ 0.023 / month for the first 50TB.

- **Amazon RDS**:

    Amazon helps us to make our infrastructure less complicated, which is why it provides us with the RDS service. But what is it? With this service we will have dedicated instances for databases in a matter of minutes, fully managed by the AWS support team and capable of supporting multiple database engines such as SQL, PostgreSQL, SQL Server, etc ...

    Finally, we will forget all those hours of maintenance and support to our database servers!

- **Amazon Route 53**:

    Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service. You can use Route 53 to perform three main functions in any combination: domain registration, DNS routing, and health checking. If you choose to use Route 53 for all three functions, perform the steps in this order:
    
    - Register domain names
    - Route internet traffic to the resources for your domain
    - Check the health of your resources

## Enhancing your app with AWS Databases and Application Services
- **Amazon Elastic Beanstalk**:

    This is the most attractive service for developers. I know that as a developer you do not want to manage the infrastructure of your site, right? It is normal since its maintenance becomes tedious and difficult to solve any problem. AWS Elastic Beanstalk relieves all this; developers no longer need to manage the infrastructure and focus on developing their software or applications.

- **Amazon Lambda**:

    Is your server saturated with many requests? You do not know what to do? Stop worrying too much about infrastructure and less about development.

    If you, like many other developers, have the problem that your current infrastructure does not support the demands of your developments, then AWS Lambda is for you. This instance allows you to work in an environment highly capable of supporting any development you do. You just take care of the coding and AWS will be responsible for providing the necessary resources, climbing at the same time so that everything works correctly.

- **Amazon DynamoDB**:
    Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. DynamoDB lets you offload the administrative burdens of operating and scaling a distributed database so that you don't have to worry about hardware provisioning, setup and configuration, replication, software patching, or cluster scaling. DynamoDB also offers encryption at rest, which eliminates the operational burden and complexity involved in protecting sensitive data. For more information, see DynamoDB Encryption at Rest.

- **Amazon VPC**:

    Is my information at risk in the AWS cloud? The answer is NO, with the private network in the cloud your information will only be available to the people or systems that you authorize. With AWS VPC you can create a private virtual network in which your entire IT environment (infrastructure or services) will live totally isolated from the outside world. This way your information is free of exposure.

- **Amazon CloudFront**:

    Have you asked yourself how fast your website is? When your users connect, do they have to wait for seconds to open the page? With the Global Content Delivery Service, commonly known as CDN, Amazon is responsible for managing all your content, delivering it and presenting it efficiently. With a minimum latency and with its high integration with other AWS services. Reaching your target users has never been so easy.

- **Amazon CloudWatch**:

    Amazon CloudWatch is a monitoring and management service that provides data and actionable insights for AWS, hybrid, and on-premises applications and infrastructure resources. With CloudWatch, you can collect and access all your performance and operational data in form of logs and metrics from a single platform. This allows you to overcome the challenge of monitoring individual systems and applications in silos (server, network, database, etc.). CloudWatch enables you to monitor your complete stack (applications, infrastructure, and services) and leverage alarms, logs, and events data to take automated actions and reduce Mean Time to Resolution (MTTR). This frees up important resources and allows you to focus on building applications and business value.

    CloudWatch gives you actionable insights that help you optimize application performance, manage resource utilization, and understand system-wide operational health. CloudWatch provides up to 1-second visibility of metrics and logs data, 15 months of data retention (metrics), and the ability to perform calculations on metrics. This allows you to perform historical analysis for cost optimization and derive real-time insights into optimizing applications and infrastructure resources.

    You can use CloudWatch Container Insights to monitor, troubleshoot, and alarm on your containerized applications and microservices. CloudWatch collects, aggregates, and summarizes compute utilization information like CPU, memory, disk, and network data, as well as diagnostic information like container restart failures, to help DevOps engineers isolate issues and resolve them quickly. Container Insights gives you insights from container management services such as Amazon ECS for Kubernetes (EKS), Amazon’s Elastic Container Service (ECS), AWS Fargate, and standalone Kubernetes (k8s).
- **Amazon SNS**:

    Going back to the developers’ issue, AWS offers us a very particular notification system that provides integration with any type of application, be it PHP, Python, Node, etc. With Amazon SNS we can send notifications to all our users on any platform, whether it is web or mobile on Android or iOS.

- **Amazon Auto Scaling**:

    The magic of AWS - How to expand our application and take it to thousands and millions of users?

    Well, Amazon again gives us the solution. With AutoScaling we can manage a fleet of servers which are capable of supporting all the traffic that our application demands. The service is totally free, the only thing charged is the number of instances for the time they run.

- **Amazon Elasticache**:

    Memory caching system of AWS. Elasticache supports Memcache and Redis.

    "Now that you have what it takes do not think more and venture to create extraordinary things with AWS and ClickIT.”


## Harnesting the power of AWS from the command line to the code
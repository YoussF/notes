# AWS Cloud Practitioner Exam Preparation
## **AWS Global Infrastructure**
<img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fjayendrapatil.com%2Fwp-content%2Fuploads%2F2016%2F03%2Fscreen-shot-2016-03-20-at-3-06-22-pm.png&f=1&nofb=1" width="100%">
The AWS Global Cloud Infrastructure is the most secure, extensive, and reliable cloud platform, offering over 200 fully featured services from data centers globally

[Services list to know for CCP EXAM](./AWS-Services.md)

Core components:

- **Regions**

  AWS has the concept of a Region, which is a physical location around the world where we cluster data centers. We call each group of logical data centers an Availability Zone. Each AWS Region consists of multiple, isolated, and physically separate AZs within a geographic areaAWS helps answer the critical question of what will happen during unforeseen circumstances like disasters by building its data centers in large groups, called Regions.
- **Availibility Zones**
  
  An Availability Zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity in an AWS Region
- **Edge Locations**
  
  Edge locations are AWS data centers designed to deliver services with the lowest latency possible.

  Example of usage: CloudFront(CDN), Route 53, Web Application Firewall(WAF), AWS Global Accelerator.
<br><br>


## **Six Advantages of Cloud Computing**
- **Trade fixed expense for variable expense**
  
  Instead of having to invest heavily in data centers and servers before you know how you’re going to use them, you can pay only when you consume computing resources, and pay only for how much you consume.

- **Benefit from massive economies of scale**
  
  By using cloud computing, you can achieve a lower variable cost than you can get on your own. Because usage from hundreds of thousands of customers is aggregated in the cloud, providers such as AWS can achieve higher economies of scale, which translates into lower pay as-you-go prices.

- **Stop guessing capacity**
  
  Eliminate guessing on your infrastructure capacity needs. When you make a capacity decision prior to deploying an application, you often end up either sitting on expensive idle resources or dealing with limited capacity. With cloud computing, these problems go away. You can access as much or as little capacity as you need, and scale up and down as required with only a few minutes’ notice.

- **Increase speed and agility**
  
  In a cloud computing environment, new IT resources are only a click away, which means that you reduce the time to make those resources available to your developers from weeks to just minutes. This results in a dramatic increase in agility for the organization, since the cost and time it takes to experiment and develop is significantly lower.

- **Stop spending money running and maintaining data centers**
  
  Focus on projects that differentiate your business, not the infrastructure. Cloud computing lets you focus on your own customers, rather than on the heavy lifting of racking, stacking, and powering servers.

- **Go global in minutes**
  
  Easily deploy your application in multiple regions around the world with just a few clicks. This means you can provide lower latency and a better experience for your customers at minimal cost.
<br><br>

## **Shared Responsability Model**
<center>
<img src="https://d1.awsstatic.com/security-center/Shared_Responsibility_Model_V2.59d1eccec334b366627e9295b304202faf7b899b.jpg" width="100%">
</center>
<br><br>

## **AWS Support plans**

Basic Support is included for all AWS customers and includes:

- Customer Service and Communities - 24x7 access to customer service, documentation, whitepapers, and AWS re:Post.

- AWS Trusted Advisor - Access to core Trusted Advisor checks and guidance to provision your resources following best practices to increase performance and improve security.

- AWS Personal Health Dashboard - A personalized view of the health of AWS services, and alerts when your resources are impacted.

### **Plans details**:

- **Basic**:
  
  Present on all aws produts and contains 24x7 access to customer service, documentation, whitepapers, and AWS re:Post.

- **Developer**
  
  ***Recommended if you are experimenting or testing in AWS.***

  We recommend AWS Developer Support if you are testing or doing early development on AWS and want the ability to get technical support during business hours as well as general architectural guidance as you build and test. **In addition to enhanced technical support and architectural guidance, Developer Support provides access to documentation and forums, AWS Trusted Advisor, and AWS Personal Health Dashboard**

- **Business**
  
  ***Minimum recommended tier if you have production workloads in AWS***

  We recommend AWS Business Support if you have production workloads on AWS and want **24x7 access to technical support and architectural guidance** in the context of your specific use-cases.
  
  In addition to enhanced technical support and architectural guidance, **Business Support provides access to third-party software support, documentation and forums, AWS Trusted Advisor, AWS Personal Health Dashboard, AWS Support API, and launch and event planning.**

- **Entreprise On-Ramp**
  
  ***Recommended if you have production and/or business critical workloads in AWS.***

  We recommend AWS Enterprise On-Ramp if you have production/business critical workloads in AWS and want 24x7 access to technical support and need expert guidance to grow and optimize in the Cloud.
  
  With Enterprise On-Ramp, you get 24x7 technical support from high-quality engineers, tools and technology to automatically manage health of your environment, consultative architectural guidance delivered in the context of your applications and use-cases, and a pool of Technical Account Managers (TAMs) to coordinate access to proactive / preventative programs and AWS subject matter experts. 

- **Entreprise**
  
  ***Recommended if you have business and/or mission critical workloads in AWS.***

  AWS Enterprise Support provides you with concierge-like service where the main focus is helping you achieve your outcomes and find success in the cloud.
  
  With Enterprise Support, you get 24x7 technical support from high-quality engineers, tools and technology to automatically manage health of your environment, consultative architectural guidance delivered in the context of your applications and use-cases, and a designated Technical Account Manager (TAM) to coordinate access to proactive / preventative programs and AWS subject matter experts. AWS Enterprise Support is recommended if you have business and/or mission critical workloads in AWS.
  
[More infos about support plans](https://aws.amazon.com/premiumsupport/plans)
<br><br>
## AWS Leadership Principles

- **Customer Obsession**
  
  Leaders start with the customer and work backwards. They work vigorously to earn and keep customer trust. Although leaders pay attention to competitors, they obsess over customers.

- **Ownership**
  
  Leaders are owners. They think long term and don’t sacrifice long-term value for short-term results. They act on behalf of the entire company, beyond just their own team. They never say “that’s not my job."

- **Invent and Simplify**
  
  Leaders expect and require innovation and invention from their teams and always find ways to simplify. They are externally aware, look for new ideas from everywhere, and are not limited by “not invented here." As we do new things, we accept that we may be misunderstood for long periods of time.

- **Are Right, A Lot**

  Leaders are right a lot. They have strong judgment and good instincts. They seek diverse perspectives and work to disconfirm their beliefs.

- **Learn and Be Curious**
  
  Leaders are never done learning and always seek to improve themselves. They are curious about new possibilities and act to explore them.

- **Hire and Develop the Best**
  
  Leaders raise the performance bar with every hire and promotion. They recognize exceptional talent, and willingly move them throughout the organization. Leaders develop leaders and take seriously their role in coaching others. We work on behalf of our people to invent mechanisms for development like Career Choice.

 - **Insist on the Highest Standards**
  
  Leaders have relentlessly high standards — many people may think these standards are unreasonably high. Leaders are continually raising the bar and drive their teams to deliver high quality products, services, and processes. Leaders ensure that defects do not get sent down the line and that problems are fixed so they stay fixed.

  - **Think Big**

  Thinking small is a self-fulfilling prophecy. Leaders create and communicate a bold direction that inspires results. They think differently and look around corners for ways to serve customers.

- **Bias for Action**
  
  Speed matters in business. Many decisions and actions are reversible and do not need extensive study. We value calculated risk taking. 

- **Frugality**
  
  Accomplish more with less. Constraints breed resourcefulness, self-sufficiency, and invention. There are no extra points for growing headcount, budget size, or fixed expense.

- **Earn Trust**
  
  Leaders listen attentively, speak candidly, and treat others respectfully. They are vocally self-critical, even when doing so is awkward or embarrassing. Leaders do not believe their or their team’s body odor smells of perfume. They benchmark themselves and their teams against the best.

- **Dive Deep**
  
  Leaders operate at all levels, stay connected to the details, audit frequently, and are skeptical when metrics and anecdote differ. No task is beneath them.

- **Have Backbone; Disagree and Commit**

  Leaders are obligated to respectfully challenge decisions when they disagree, even when doing so is uncomfortable or exhausting. Leaders have conviction and are tenacious. They do not compromise for the sake of social cohesion. Once a decision is determined, they commit wholly.

- **Deliver Results**
  
  Leaders focus on the key inputs for their business and deliver them with the right quality and in a timely fashion. Despite setbacks, they rise to the occasion and never settle.

  - **Strive to be Earth's Best Employer**

  Leaders work every day to create a safer, more productive, higher performing, more diverse, and more just work environment. They lead with empathy, have fun at work, and make it easy for others to have fun. Leaders ask themselves: Are my fellow employees growing? Are they empowered? Are they ready for what's next? Leaders have a vision for and commitment to their employees' personal success, whether that be at Amazon or elsewhere.

- **Success and Scale Bring Broad Responsibility**
  
  We started in a garage, but we're not there anymore. We are big, we impact the world, and we are far from perfect. We must be humble and thoughtful about even the secondary effects of our actions. Our local communities, planet, and future generations need us to be better every day. We must begin each day with a determination to make better, do better, and be better for our customers, our employees, our partners, and the world at large. And we must end every day knowing we can do even more tomorrow. Leaders create more than they consume and always leave things better than how they found them.


## **AWS Well-Architected Framework (Six pillars):**

- **Operational Excellence**
  
  The operational excellence pillar focuses on running and monitoring systems, and continually improving processes and procedures. Key topics include
    
    - **Automating changes, responding to events, and defining standards to manage daily operations**
    <br><br>

- **Security**
  
  The security pillar focuses on protecting information and systems. Key topics include
  
    - **Confidentiality and integrity of data, managing user permissions, and establishing controls to detect security events.**
    <br><br>
  
- **Reliability**
  
  The reliability pillar focuses on workloads performing their intended functions and how to recover quickly from failure to meet demands. Key topics include
    
    - **Distributed system design, recovery planning, and adapting to changing requirements.**
    <br><br>

- **Performance Efficiency**
  
  The performance efficiency pillar focuses on structured and streamlined allocation of IT and computing resources. Key topics include

    - **Selecting resource types and sizes optimized for workload requirements, monitoring performance, and maintaining efficiency as business needs evolve.**
    <br><br>

- **Cost optimization**
  
  The cost optimization pillar focuses on avoiding unnecessary costs. Key topics include
    
    - **Understanding spending over time and controlling fund allocation, selecting resources of the right type and quantity, and scaling to meet business needs without overspending.**
    <br><br>

- **Sustainability**
  
  The sustainability pillar focuses on minimizing the environmental impacts of running cloud workloads. Key topics include
  
    - **A shared responsibility model for sustainability, understanding impact, and maximizing utilization to minimize required resources and reduce downstream impacts.**
<br><br>

## **Disaster recovery options in the cloud**
Notions:
- Recovery Time Objective (RTO):
  
  RTO refers to how much time an interruption can last for any business function

- Recovery Point Objective (RPO):

  The Recovery Point Objective is the point in time you’d like to go back to retrieve clean versions of your files. How often backups run, and how much space is available to store the backups are crucial factors in RPO analysis. Senior management must place limits on RTO and RPO based on the application and resulting cost considerations involved to minimize damage. 

<img src="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/images/disaster-recovery-strategies.png" width="100%">
<br><br>

## **Amazon EC2 pricing models (Five)**
 - **On-Demand** (Pay per hour of usage)
  
   You pay for compute capacity by the hour or the second depending on which instances you run.

   On-Demand instances are recommended for:
   - Users that prefer the low cost and flexibility of Amazon EC2 without any up-front payment or long-term commitment
   - Applications with short-term, spiky, or unpredictable workloads that cannot be interrupted
   - Applications being developed or tested on Amazon EC2 for the first time
    <br><br>

 - **Savings Plans**

    Savings Plans are a flexible pricing model that offer low prices on EC2 and Fargate usage, in exchange for a commitment to a consistent amount of usage (measured in $/hour) for a 1 or 3 year term.
    <br><br>

 - **Dedicated Hosts**
    
    A Dedicated Host is a physical EC2 server dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses, including Windows Server, SQL Server, and SUSE Linux Enterprise Server (subject to your license terms), and can also help you meet compliance requirements. Learn more.

    - Can be purchased On-Demand (hourly).
    - Can be purchased as a Reservation for up to 70% off the On-Demand price.
    <br><br>

 - **Dedicated Instances**
  
    Pay, by the hour, for instances that run on single-tenant hardware.

 - **Reserved Instances**

    Reserved Instances provide you with a significant discount (up to 72%) compared to On-Demand Instance pricing. In addition, when Reserved Instances are assigned to a specific Availability Zone, they provide a capacity reservation, giving you additional confidence in your ability to launch instances when you need them.
    <br><br>

 - **Spot Instances**
    
    Ideal if you don't mind your ressources can be potentialy terminated. And can be run

    Ideal for quick non critical one-off job.

    Up to 90% of on demand price for same ressource, but only to run non critical processing. 

    Job run when ressources are availible.

    Do not use for production loads.

    Amazon EC2 Spot instances allow you to request spare Amazon EC2 computing capacity for up to 90% off the On-Demand price.
    
    Spot instances are recommended for:

    - Applications that have flexible start and end times
    - Applications that are only feasible at very low compute prices
    - Users with urgent computing needs for large amounts of additional capacity
    <br><br>

 - **Capacity Reservations**
  
    Reserve capacity for your EC2 instances in a specific Availability Zone for any duration.
    <br><br>



## **CAPEX vs OPEX**

- **Capital Expenditure (CAPEX)** (on-premise)
  
  Spending money upfront on physical infrastructure deducting that expense from your tax bill over time.

  - Server Costs (computers)
  - Storage Costs (hard drives)
  - Network Costs (Routers, Cables, Switches)
  - Backup and Archive Costs
  - Disaster Recovery Costs
  - Datacenter Costs (Rent, Cooling, Physical Security)
  - Technical Personal
  
  With **Capital Expenses**, you have to guess upfront what you plan to spend

- **Operational Expenditure (OPEX)** (Cloud)
  
  The costs associated with an on-premises data center that has shifted the cost to the service provider. The customer only has to be concerned with non-physical costs.

  - Leasing Software and Customizing features
  - Training Employees in Cloud Services
  - Paying for Cloud Support
  - Billing based on cloud metrics eg.
    - compute usage
    - storage usage
  
With **Operational Expenses** you can try a product or service without investing in equipment

<div style="border: 1px solid #808080; padding: 5%">

## **Not to forget**
### Some words:
- VPC:
- Security Group:
- NACL:
- AMI:
- 

### **Security**
- [Blog post - Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
### **Amazon VPC-to-Amazon VPC**
- [Blog post - Amazon VPC-to-Amazon VPC connectivity options](https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/amazon-vpc-to-amazon-vpc-connectivity-options.html)
- [VPC peering](https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/vpc-peering.html)

### **AWS Pricing/TCO Tools**
**How do you pay for AWS?** (three options)
- **Pay-as-you-go**
  
  Pay-as-you-go allows you to easily adapt to changing business needs without overcommitting budgets and improving your responsiveness to changes. With a pay-as-you-go model, you can adapt your business depending on need and not on forecasts, reducing the risk of overprovisioning or missing capacity.
- **Save when you commit**
  
  For AWS Compute and AWS Machine Learning, Savings Plans offer savings over On-Demand in exchange for a commitment to use a specific amount (measured in $/hour) of an AWS service or a category of services, for a one- or three-year period.
- **Pay less by using more**

  With AWS, you can get volume based discounts and realize important savings as your usage increases. For services such as S3, pricing is tiered, meaning the more you use, the less you pay per GB. AWS also gives you options to acquire services that help you address your business needs.

**Usefull links**
- [Wiki: Total cost of ownership](https://en.wikipedia.org/wiki/Total_cost_of_ownership)
- [AWS Services Pricing](https://aws.amazon.com/pricing/)

</div>
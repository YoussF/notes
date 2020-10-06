<p align="center">
   <img src="assets/mirstation.png" alt="MirStation" width="197"/>
</p>

# AWS Certified Cloud Practitioner

This document is intended to help preparing for the AWS Cloud Practitioner Certification

## Table of contents
<details>
  <summary>Introduction</summary>

  - [Who is the Certified Cloud Pratictitioner for](#who-is-the-certified-cloud-pratictitioner-for)
  - [What does this exam validates](#what-does-this-exam-validates)
    * [What value does CCP hold](#what-value-does-ccp-hold)
  - [Why get the CCP](#why-get-the-ccp)
  - [How long to study to pass CCP](#how-long-to-study-to-pass-ccp)
  - [Where to take the test](#where-to-take-the-test)
  - [How much how long and other questions..](#how-much-how-long-and-other-questions)
  - [Exam Guide - Content Outline](#exam-guide---content-outline)
      + [Domain 1: Cloud Concepts](#domain-1--cloud-concepts)
      + [Domain 2: Security and Compliance](#domain-2--security-and-compliance)
      + [Domain 3: Technology](#domain-3--technology)
      + [Domain 4: Billing and Pricing](#domain-4--billing-and-pricing)
  - [Exam response type](#exam-response-type)
</details>

<details>
  <summary>Cloud Concepts</summary>

  - [What is Cloud Computing](#what-is-cloud-computing)
  - [Six Advantages and Benefits of Cloud Computing](#six-advantages-and-benefits-of-cloud-computing)
  - [Types of Cloud Computing](#types-of-cloud-computing)
  - [Cloud Computing Deployment Models](#cloud-computing-deployment-models)
</details>


<details>
  <summary>AWS Global Infrastructure</summary>

  - [Introduction and Map Overview](#introduction-and-map-overview)
  - [Regions](#regions)
  - [Availability Zones](#availability-zones)
  - [Edge Locations](#edge-locations)
  - [GovCloud Regions](#govcloud-regions)
</details>


<details>
  <summary>Getting Started</summary>

   - [Creating an AWS Account](#creating-an-aws-account)
   - [Billing Preferences, Budgets and Alarms](#billing-preferences,-budgets-and-alarms)
   - [Change IAM Users Sign-in Link](#change-iam-users-sign-in-link)
   - [Activate MFA on Root Account](#activate-mfa-on-root-account)
   - [Create individual IAM user](#create-individual-iam-user)
   - [Set a password policy](#set-a-password-policy)
</details>



# Introduction


## Who is the Certified Cloud Pratictitioner for
- Learning AWS foundational knowledge
- Shows you've poked around and can use the AWS console.
- Focus on billing and business-centric concepts
- Commonly obtained by sales and management to help inform VPs or CEO reasons to utilize AWS.


## What does this exam validates
It validates an examinee’s ability to:
- Explain the value of the AWS Cloud.
- Understand and explain the AWS shared responsibility model.
- Understand AWS Cloud security best practices.
- Understand AWS Cloud costs, economics, and billing practices.
- Describe and position the core AWS services, including compute, network, databases, and storage.
- Identify AWS services for common use cases.


## What value does CCP hold
- Not a gilded title.
- Can help superficially increase your AWS Certification count.
- Not recognized as an important certification for developers on resumes.


## Why get the CCP
- It's a easy win, and a confidence booster.
- To become familiar with your test center.
- Mitigate unknown conditions that case stress or distraction for a future exam.
- Directly prepare for the Solution Architect Associate certification.


## How long to study to pass CCP
If you're a :
- developer => 8hrs
- bootcamp grad => 15hrs
- sales or manager => 20hrs


## Where to take the test
On a test center such as PSI or Pearson VUE or Online via a "proctor" supervisor. (a person who monitors students during an examination to avoid cheating).


## How much how long and other questions..
- 100$ USD
- 90 Minutes
- 65 Questions
- 70% Passing Score
- Valid 3years


## Exam Guide - Content Outline
You can find the exam guide [here](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

| Domain               | Percentage    |
| -------------------- |:-------------:|
| Cloud Concepts       | 28%           |
| Security             | 24%           |
| Technology           | 36%           |
| Billing & Pricing    | 12%           |

#### Domain 1: Cloud Concepts
- Define the AWS Cloud and its value proposition
- Identify aspects of AWS Cloud economics
- List the different cloud architecture design principles

#### Domain 2: Security and Compliance
- Define the AWS shared responsibility model
- Define AWS Cloud security and compliance concepts
- Identify AWS access management capabilities
- Identify resources for security support

#### Domain 3: Technology
- Define methods of deploying and operating in the AWS Cloud
- Define the AWS global infrastructure
- Identify the core AWS services
- Identify resources for technology support

#### Domain 4: Billing and Pricing
- Compare and contrast the various pricing models for AWS
- Recognize the various account structures in relation to AWS billing and pricing
- Identify resources available for billing support

## Exam response type
- Multiple choice. (1 out of 4)
- Multiple response. (2 out of 5 or more options)



# Cloud Concepts


## What is Cloud Computing
Cloud computing is the pratice of using a network of remote servers hosted on the internet to store manage, and process data, rather than a local server or a personal computer.


## Six Advantages and Benefits of Cloud Computing
1. **Trade capital expense for variable expense** :

   **No upfront-cost** Instead of paying for data centers and servers
   **Pay On-Demand** Pay only when you consume computing resources

2. **Benefit from massive economies of scale** :

   Usage from hundreds of thousands of customers aggregated in the cloud. Your are **sharing the cost with other customers** to get unbeatable savings.

3. **Stop guessing capacity** :

   Eliminate guesswork about infrastructure capacity needs, **Instead of paying for idle or underutilized servers**, you can scale up or scale down to meet the current need.

4. **Increase speed and agility** :

   Launch resources **within a few click in minutes** instead of waiting days or weeks of your IT to implement the solution on-promise.

5. **Stop spending money on running and maintaining data centers** :

   **Focus on your own customers**, rahter than on the heavy lifting of racking, staking, and powering servers.

6. **Go global in minutes** :

   Deploy you app in minutes in **multiple regions around the world with a few clicks**.
   Provide lower latency and a better experience for your customers at minimal cost.


## Types of Cloud Computing
   1. **SaaS** : (For Customers, ex: gmail, office365,...) \
   Software as a service, a completed product that is run and managed by the service provider
   2. **PaaS** : (For Developers, ex: AWS Elastic Beanstalk, Heroku, Google App engine,...) \
   Plateform as a service, removes the need for you organization to manage the underlying infrastructure. Focus on the deployment and management of yoAWS Elastic BeanstalkYou have an app, you push-it and it runs.
   1. **IaaS** : (For Admins, ex: AWS, Google Cloud Platform, Microsoft Azure,...)
   Infrastructure as a service, the basic building blocks for you cloud IT, Provides access to networking features, computers and data storage space.


## Cloud Computing Deployment Models
   1. **Cloud** : Fully utilizing cloud computing \
   For Startups, SaaS offerings, New Projects and companies
   1. **Hybrid** : Using both Cloud and On-Promise \
   For Banks, FinTech, Investment Management, Large Professional Service providers, Legacy on-promise
   1. **On-Promise** : Dploying resources on-promises, using virtualization and resource management tools \
   For Public sectors eg. Government, Super Sensitive eg. Hospitals, large Entreprise with heavy regulation eg. Insurance Compagnies



# AWS Global Infrastructure


## Introduction and Map Overview
<p align="center">
   <img src="assets/aws_regions-1.png" width="600">
</p>

AWS now spans **77 Availability Zones** within **24 geographic regions** around the world, and has announced plans for nine more Availability Zones and three more AWS Regions in Indonesia, Japan, and Spain.

**Regions** : Physical location inthe world with multiple Availibity Zones \
**Availibity Zones** : One or more discrete data centers \
**Edge Location** : Datacenter owned by a trusted partner of AWS\


## Regions

A **geographysically distinct** location which has multiple datacenters (AZs)

Every region is **physically isolated** from and independent of other region in terms of location, power, water supply

Each region has **at least two AZs**

AWS largest ragion is **US-EAST**

New services almost always become availible first in **US-EAST**

Not all services are availible in all regions

**US-EAST** is the region where you see all your **billing information**

[More Information](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2)


## Availability Zones

An AZ is a datacenter owned and operated by AWS in which AWS services run

Reach region has at least two AZs

AZs are represented by a Region Code, followed by a letter identifier eg. **us-east-1a**

**Multi-AZ** Distributing your instances across multiple AZs allows failover configuration for handling requests when one goes down.

< 10ms latency between AZs


## Edge Locations

An Edge Locaton is a datacenter owned by a trusted partner of AWS which has a **direct connection** to the AWS network.

These locations serve reqeuests for **CloudFront** and **Route 53**. Requests going to either of these services will be routed to the nearest edge location automaticaly.

**S3 Transfer Acceleration** traffic and **API Gateway** endpoind traffic also use the AWS Edge Network.

This allows for low latency no matter where the end user is geographically located.


## GovCloud Regions

AWS GovCloud Regions allow customers to host sensitive **Controlled Unclassified Information** and other types of regulated workloads.

GovCloud Regions are only operated by employees who are U.S citizens, on U.S. soil.

They are **only** accessible to U.S. entities and root account holders who pass a screening process.

Customers can architect secure cloud solutions that comply with:
   - FedRAMP High baseline
   - DOJ's Criminal Justice Information Systems (CJIS) Security Policy.
   - U.S. International Traffic in Arms Regulations (ITAR)
   - Export Administration Regulations (EAR)
   - Department of Defense (DoD) Cloud Computing Security Requirements Guide.



# Getting Started


## Creating an AWS Account
## Billing Preferences, Budgets and Alarms
## Change IAM Users Sign-in Link
## Activate MFA on Root Account
## Create individual IAM user
## Set a password policy
---
title: 'EXTRA: CloudFormation'
layout: posts
categories:
- theproject
date: 2018-02-20 00:00:00 +0000
---
![](/uploads/2018/02/20/create-stack-diagram.png)

I had a discount on another course of Stephane and as I have one week ahead, since I already know how to do the stress test I paid for it. It is the CloudFormation course. And sounds very handy for the project. 

### What is CloudFormation

It helps you define an entire cloud in a YAML template. That implies:

* The security policy
* The ELB
* The EC2 machines. 
* The network. 

Basically it is ideal for my project. It could find as a going through a rabit hole, but no. It is exactly what I need for the project. 

Cloudformation is free, the resources might not be. Apply the knowledge from the previous course. 

Budget it for 10 dollars. So you get an alert. 

An alternative to CloudFormation is Ansible/Terraform you could use this info for your project. Video 6 explains it. 

When you run CloudFormation it will automatically terminate the previous instance it created. 

**Deleting a STack deletes every artifact (EC2) that the CloudFormation stack created.** 

Stacks must have unique names. 

Section 2 (video 10) teaches YAML

YAML works with Key value pairs delimited by a colon, nested objects (like JSON) but with an structure similar to Python code. Arrays are delimited with - (minus) comments come with a hashtag. 

An S3 bucket created with CloudFormation can be updated without interruption (adding AccessControl). Be careful to do this otherwise you might delete it. 

On updates of S3 always preview changes. 

I'm going to finish this entire section 2 (Cloudformation First Hand-On) and give up for today. 

Video 16 is crucial becuase it shows the designer. 

YOu can't run custom scripts on cloud formation (but you can run custom AMIs...so)

### F\*\*k it let's go to Section 3: Parametres
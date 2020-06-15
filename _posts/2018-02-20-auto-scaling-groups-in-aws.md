---
title: Auto Scaling Groups in AWS
layout: post
categories:
- theproject
date: 2018-02-20 00:00:00 +0000
---
![](/uploads/2018/02/20/UC-7FICP0SI.jpg)So finally we reach the point in which I learn about the entire subject of this week of the project: **How to do autoscaling.** 

This should finish this week of project work but I'm a couple of days delayed so I'll go straight after to the next subject of my research. 

Before creating an autoscaling group you need a launch configuration. 

ASG works with ELB (see previous post). It can work by itself but the configuration is hideous without it. 

Desired, min and max are important choices. 

### Alarms

You can use it with Cloudwatch alarms such as average CPU. This metrics are computed for the overall ASG instances. 

Hmmm, he speaks about a load testing tool. This can be handy for this week too. 

The tab is scaling policies in Auto Scaling groups. Video 46 for this policies. 

### Restful Stress from Chrome

[This is the one ](https://chrome.google.com/webstore/detail/restful-stress/lljgneahfmgjmpglpbhmkangancgdgeb?hl=en)he uses for it. You would need to justify your stress test though. 

You could just create the two policies same as he did but you'll need to justify why. 

The new rules for policies are even simpler. 

AutoScaling is free and CloudWatch is not but it has free tiers. 

### Elastic Block Store

Used to store data durably. 

Video 49 justifies this. EBS are network drives. They will have some latency. 

It's locked to one availability zone. us-east-1a cannot be attached to us-east-1b **this is very important.** 

**EBS can be:**

* GP2: price and performance balanced SSD
* IOI highes performance for mission critical low latency, expensive. 
* STI (HDD)
* SC1 (HDD) for ultra low cost. 

You shoudl choose IO1 for Mongo but you can't because it is too expensive. 

There's a table of max throughoput in MBi/s. 

SC1 is for cold storage. 

Not sure if you would use any EBS volume for anything. I don't think so. 

EBS Snapshots live in S3. This is the useful bit to back up your EC2 machine. 

EBS are quite cheap, for example the st1 is 0.045 dollars per month per GB of storage. Ideal to save backups of your DB. 

The thing is that when you terminante an EC2 instance you lose all the data, you need to set up some form of permanent storage for the Mongo content or put the mongo content elsewhere. 

### EC2 Reserved Instances

I didn't know this was possible, but again i didn't need them because I'm on the free-tier. When it's over I might need them. The EC2 RI offer 75% discount. 

They basically save costs. 

This could be handy to use one for www.maikel.uk and keep the elasticity of the cloud architecture for everything else. 

I could purchase a nano for 77 dollars 3 years and move maikel.uk there. That's incredibly cheap. Cheaper than buying Raspberry Pis and changing the SDCard as they break along. 

This is only useful after I've run out of the free-tier but is' handy to know about it now. 

### EC2 Spot instances

They use the spare capcity of AWS cloud. The discount is 90%. Hmmm, then why to use the previous one?

Amazon can terminate them at any time. Ok, that's the problem. You can't run critical jobs on they then. 

Dedicated hosts are pointless for me. 

And that's it I finsihed the course. What are my conclussion for the project this week?

I will need:

* An Autoscaling group
* A security policy
* An Elastic Load Balancer
* A custom made AMI 
* Find out where to keep the data which probably would be an external service (mongo)

Right I've finished I've completed the entire course now and finished two weeks accidentally. 
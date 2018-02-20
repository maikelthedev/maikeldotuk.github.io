---
title: Auto Scaling Groups in AWS
layout: posts
categories:
- theproject
date: 2018-02-20 00:00:00 +0000
---
![](/uploads/2018/02/20/aws-autoscaling.png)So finally we reach the point in which I learn about the entire subject of this week of the project: **How to do autoscaling.** 

This should finish this week of project work but I'm a couple of days delayed so I'll go straight after to the next subject of my research. 

Before creating an autoscaling group you need a launch configuration. 

ASG work with ELB (see previous post). 

Desired, min and max are important choices. 

### Alarms

You can use it with Cloudwatch alarms such as average CPU. This metrics are computed for the overall ASG instances. 

Hmmm, he speaks about a load testing tool. This can be handy for this week too. 

The tab is scaling policies in Auto Scaling groups. Video 46 for this policies. 

### Restful strees from Chrome

This is the one he uses for it. You would need to justify your stress test though. 

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
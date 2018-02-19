---
title: Amazon Machine Images
layout: posts
categories:
- theproject
date: 2018-02-19 00:00:00 +0000
---
![](/uploads/2018/02/19/debian-cloud-building-the-debian-amis-24-638.jpg)

Today I'm learning about AMIs.

AMIs allow you to create your own images. Note that AMIs are built for specific regions. They can be copied but by default they are on one region.

You'll need to create your own AMI so you need to decide what goes into it.

**How to set it to run when you reboot it**

This is on video 15 at around the 10 minutes mark.

Later today you should use what's on EC2 to do a machine out of maikel.uk as practice.

Explain why aren' you using Docker for your AMI (explain first why you were using it for maikel.uk)

Some AMIs in the AWS Marketplace are free but there are many that are paid on top of what AWS EC2 cost.

In Community AMIs there are many who are malware.

AMIs are stored in S3 but they don't appear in the S3 console (the file manager).

You can use the pricing results for the EMA and as part of the blueprints of the cloud architecture (a deliverable).

Done with the AMI sectio, now the EC2 section.

### Choosing the right EC2 instance.

Factors:

* RAM
* CPU
* I/O (disk)
* Network
* GPU (if the instance has one)

Video 22 tells you how to monitor the CPU usage from the console.

To be continued this evening...

### Continuing

Back from working in the council now I can continue. 

IO is key for database applications. Consider it when choosing where to store the MongoDB instance. 

Bunrstable instances are the T2. If you choose T2 you might have to change to T2 Unlimited (video 29) because otherwise it'll be weird for an autoscalable system. 

### Network and Security

I'm trying to get rid of the entire course today so moving onto this section.

Keep a separated security group for SSH instances. (video 30). You need to choose how are you designing the IP addresses of your cloud architecture .

CIDR are usueful to set HTTP rules for entire networks, see picture. You'll need this for autoscaling. 

![](/uploads/2018/02/19/entirenetworks.JPG)
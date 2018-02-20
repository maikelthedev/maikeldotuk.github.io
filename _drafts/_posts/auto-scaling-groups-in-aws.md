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
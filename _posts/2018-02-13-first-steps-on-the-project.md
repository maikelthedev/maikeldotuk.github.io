---
title: 'First steps on the project: Auto scaling'
layout: posts
categories:
- theproject
date: 2018-02-13 19:32:05 +0000
---
![](/uploads/2018/02/13/as-basic-diagram.png)

## To add on TMA01

Forgot to mention any connectivity through a Rest API. The project needs to connect to one otherwise it wouldn't do enough of TM352 stuff.

Right, today I'm checking this

[https://aws.amazon.com/autoscaling/](https://aws.amazon.com/autoscaling/ "https://aws.amazon.com/autoscaling/")

And it mentions two parts, autoscaling with EC2 and CloudWatch fees. And DynamoDB which I guess is where the DB will be.

Apparently I've got to learn about CloudFormation. At least I know for now that autoescaling is free.

Right the requisite is to have a CloudFormation so reading this:

[https://aws.amazon.com/cloudformation/](https://aws.amazon.com/cloudformation/ "https://aws.amazon.com/cloudformation/")

Good, CloudFormation is also free

[https://aws.amazon.com/cloudformation/pricing/](https://aws.amazon.com/cloudformation/pricing/ "https://aws.amazon.com/cloudformation/pricing/")

Here some examples of code for CloudFormation

[https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html "https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html")

At the end is easier to buy this course and start from there. It's only 3 hours.

[https://www.udemy.com/aws-ec2-masterclass/learn/v4/overview](https://www.udemy.com/aws-ec2-masterclass/learn/v4/overview "https://www.udemy.com/aws-ec2-masterclass/learn/v4/overview")

## Conclussions

To make an elastic cloud with Amazon I need an Elastic Load Balancer, which means I've got to learn how to configure it. For this I've bought the udemy course that explains it. The course has been 8.94 pounds because I pay in dollars (US account through VPN).

If in need of more (a.k.a: CloudFormation) I can buy another course for it.

Remember that this is only part of the research, not the cloud creation. All I'm researching is the feasibility and gathering instructions, once I need to create it I'll go back to this information. I'll have a look around the material to have a clearer picture, especially considering creating the cloud image map, which is where an implementation should be planned. But I won't really create the cloud until later.

I will have to justify my choices too. In here my choice for the Udemy course is because an introductory course always gives you more information than you require but groups them nicely so you can expand using the documentation.

With the documenation alone you don't know where to begin, while Udemy course is sequential.

By the way I'm following carefully my own Gantt chart for the project. Either way the most research that I do now, the better later.

## Extra

I've been watching the videos and finished the entire Introduction and EC2 Basics sections.   
It was mostly a refresher everything is too basic so far, but I learn how to add user data on the start of a machine. Something that I haven't done in [www.maikel.uk ](www.maikel.uk  "www.maikel.uk ")since I manually SSH into it and start the web servers (and MySQL, and node, etc) with bash commands. 

With this, that bit can be automatised. 

The commands are run with admin privileges on Amazon AMI (so no sudo su needed). 

For further reference this is video 12 in here

[https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197210?start=0](https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197210?start=0 "https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197210?start=0")

Something that worried me was prices. Since I'm already running 24/7 my own website I was wondering how to do this and the project without additional costs. I've learn a non-running instance costs nothing so all I've got to do is to shutdown my website when I'm testing for the project for it to cost zero. 

I've also learnt how to check the logs which is useful to see how these commands run. 

Lecture 13 contains the prices which will be part of the Project consideration too. 

[https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197212?start=0](https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197212?start=0 "https://www.udemy.com/aws-ec2-masterclass/learn/v4/t/lecture/9197212?start=0")

Remember to check how much is an instance per month as that would be the case when doing the math with 500 users for example. 

## Beware that bootstrap script

It's only run the first time the instance is run. Not every time that is restarted. 

Beware you don't pay for an instance that is stopped but you do for the EBS attached. 

I need to find a way to run this commands automatically whenever it is started, not just the first time. 

It could be handy if I could convert my instance of maikel.uk into a nano one so I could run two at once without having to disconnect this one first. 

## Project related

So far I know I'll need an EC2 instance to run node, a webserver, and the page. But it could be done with just S3 if I'm using only Angular. The problem is whether I need to upload files. If I do then I might need a full server. If I don't then S3 suffices but I'll need multiple DBs to connect to. 

If the site is in Angular, which is my intention, all the job is on the client side, the server would do very little. Or maybe not, because I'll need a REST API since the website cannot comunicate directly to the DB for security reasons. 

Tomorrow I'll continue with AMI images. So far we can determine that I'll run AMI images for simplicity. 
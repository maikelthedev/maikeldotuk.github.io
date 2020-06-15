---
title: The cloud image map
layout: post
categories:
- theproject
date: 2018-03-11 00:00:00 +0000
---
![](/uploads/2018/03/11/awseditor3.png)

It's 11:28am on Sunday, today I've got to finish the cloud image map I started. The main issue to decide on (and justify) is the location of the database.

I've got to check on TMA01 to see what I've decided so far.

So, I've chosen Mongo as the DB for this endevour because it integrates better with a Full Stack Javascript development than any other alternative. But there are alternatives I have indeed considered and I would have to explain why I discarded.

The main one is DynamoDB. That is Amazon's own offering of NoSQL databases.

A NoSQL database is one that is non-relational and non-SQL ([reference](https://goo.gl/X16ZC1) maybe explain it better) and is better for un-structured data. A few examples are DynamoDB, ElasticSearch, Mongo and Reddis.

There are many reasons to choose one over the other ones but at the end is just a matter of familiarity. Learning how to use Reddis, ElasticSearch or DynamoDB would be out of the scope of this project as it is. You can see a comparison here ([reference](https://db-engines.com/en/system/ElasticSearch%3BMongoDB%3BRedis)) but also a few reasons to choose mongo:

* It is not propietary. I can migrate it out of MongoDB atlas at any time to my own machine.
* it is much strongly integrated to javascript than all others.
* It is cost-effective compared to all other options.
* No lock-in unlike the others, especially amazon's offerings.

DynamoDB seemed the best choosing to make it all fully AWS integrated but that is not wise thinking in the future because that would lock me in Amazon offering, something that I'm already trying to avoid by using Terraform as the orchestration tool.

So, decided for Mongo, I noticed the complexity of my cloud could escalate quickly just based on this server. The Mongo one has to be separated from the web server images because Mongo needs 1 main machine and the rest are just replicas that take over in case that one fails. So you can't just clone the main one. On this [reference](https://aws.amazon.com/blogs/aws/mongodb-on-the-aws-cloud-new-quick-start-reference-deployment/) I found out how to add a mongodb cluster to my cloud.

This text on [that](https://s3.amazonaws.com/quickstart-reference/mongodb/latest/doc/MongoDB_on_the_AWS_Cloud.pdf) link is the most important bit

> The purpose of replication is to ensure high availability, in case one of the servers goes down. This reference deployment supports one or three replica sets. In the case of three replica sets, the reference deployment launches three servers in three different Availability Zones (if the region supports it). In production clusters, we recommend using three replica sets (Primary, Secondary0, Secondary1). All clients typically interact with the primary node for read and write operations. It is possible to choose a secondary node as a preference during read operations, but write operations always go to the primary node and get replicated asynchronously in the secondary nodes

Because that means the MongoDB will use just one machine. But then after reading that there's no set advantage of adding a machine and replicas to my cloud set up if MongoDB atlas can do that without me having to set it up. instead of me managing the DB inside my Infrastructure as a Service, MongoDB Atlas deals with all the complexity and I use them as a Dabase as a Service for free.

So I'm externalising my DB to them and taking them out of my cloud. They are free after all.

### So let's complete the rest.

Because I live in London and this is a small cloud I have chosen eu-west-2 as the region for the cloud to reside. This is to reduce latency. That region is based in London.

To ensure high availability and resilience it will have an Elastic Load Balancer that would distribute the workload across three availability zones, that will work with an AutoScaling group that means that if more machines are required from the initial three ones across 3 zones, they will automatically be created. To save on cost the machiens are all nano images. Maybe explain the sizing for AWS for the TMA02 and the EMA.

The app I'm using to model my cloud is [Cloudcraft](https://cloudcraft.co/app)

The MongoDB atlas services is then external through the internet and independent of my cloud. So my cloud architecture looks like this:

![](/uploads/2018/03/11/My Project (2).png)

I've missed adding the VPC (in blue) IPs and the subnets. Why? Because it'll add unrequried complexity to the image. I won't need more than 10 machines on each availability zones for the scope of this project so the subneting woudl use the standard 192.168.1.0/28 networks. I might have to explain my choosing later.

I like the text explanation from this page ([reference]()) from Rackspace about AWS Availability Zones.

> This ability to leverage multiple zones is foundational for building a highly available, fault-tolerant application using AWS.

I will add details of the subnets once the infrastructure as code is written for Terraform. So they might be included in that image on the final cloud model for the EMA. 

I could make up the subnet details now here, no need to postpone them:

* For availability zone 1:

  192\.168.1.0/25 is the CIDR that will give me a maximum of 126 IP addresses. 
* For availability zone 2:

  192\.168.2.0/25 is the CIDR, same number of addresses as before. 
* For availability zone 3:

  192\.168.3.0/25 is the CIDR, gives me the same number of addresses as before too. 

Let's add this on the cloud image. Now the only thing to add to it is the Elastic IP address for the page. I am not using Amazon Route 53 DNS service because it is costly and once an Elastic IP address it is attached to an AWS cloud it stays there for as long as it is required so it is easier to associate the EIP with a domain name. So far I'm going to use project.maikel.uk for it in my registrar (gandi.net) so I can access the project from there. All that I need to do is, following the advice on this page ([reference](https://stackoverflow.com/questions/35313134/assigning-static-ip-address-to-aws-load-balancer)) assign a CNAME to the load balancer. So let's simply add the website temporal address in the cloud map. 

This is the result and that one ready **deliverable** for my final project. But it could change as I go along. 

![](/uploads/2018/03/11/My Project (3).png)

It needs the Terraform code though to be finished. But it is good to have a visual clue. This page ([reference](https://www.terraform.io/docs/providers/aws/r/elb.html)) have good ideas about how to create the ELB using Terraform. 

That cloud map will serve as a conceptual idea of the cloud for the later stages on my project when I actually have to create it. That's all the work for this stage. On the next one I'll have to start writing the code for the server side of my web application. 
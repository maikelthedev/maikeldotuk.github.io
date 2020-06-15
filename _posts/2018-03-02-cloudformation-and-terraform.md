---
title: CloudFormation and Terraform
layout: post
categories:
- theproject
date: 2018-03-02 00:00:00 +0000
---
![](/uploads/2018/03/02/cf-tf-scope.png)

I need to run my entire cloud architecture from a template. Now, there are a few options, some incredibly complicated and some simpler.

I am not changing infrastructure because Amazon Web Services is what I know, but that doesn't mean I'm forced to use CloudFormation to write the infraestructure as code.

Yesterday I tried in many ways to automate my cloud (what's behind www.maikel.uk) and I succeeded in many fields, for example now the entire setup is disposable and I can re-generate it in barely 2 minutes.

But I failed in finding an orchestrating tool. I tried to get it built with CloudFormation but it is incredibly cumbersome to use. So I asked the internet and Terraform is the way to go.

As shown [here](https://www.terraform.io/intro/getting-started/build.html), this is all you need to get an instance declared

    provider "aws" {
      access_key = "ACCESS_KEY_HERE"
      secret_key = "SECRET_KEY_HERE"
      region     = "us-east-1"
    }
    
    resource "aws_instance" "example" {
      ami           = "ami-2757f631"
      instance_type = "t2.micro"
    }

Save the file as anything.tf and the run "terraform apply". That's all it takes. Well, appart from getting your keys from AWS which is also explained in the link.

While with CloudFormation is more of:

    EC2Instance:
        Type: AWS::EC2::Instance
        Properties:
          InstanceType:
            Ref: InstanceType
          KeyName:
            Ref: KeyName
          ImageId:
            Fn::FindInMap:
            - AWSRegionArch2AMI
            - Ref: AWS::Region
            - Fn::FindInMap:
              - AWSInstanceType2Arch
              - Ref: InstanceType
              - Arch

Now, how is that understandable to any human or not error prone is a mystery to me.

Apart from being clearer, Terraform can work with many cloud providers. That means I can re-create my infrastructure elsewhere instead of being locked in AWS in the future. 

Doing all this took me until 5am last night so today I'm knackered. 
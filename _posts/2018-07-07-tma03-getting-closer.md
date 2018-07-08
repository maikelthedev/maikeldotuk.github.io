---
title: TMA03 getting closer
layout: posts
categories:
- theproject
date: 2018-07-07 00:00:00 +0000
---
So the frontend is finished and is available in [https://www.maikel.uk/project](https://www.maikel.uk/project "https://www.maikel.uk/project")

Now I'm checking whether I've forgotten anything the project must or should do.

Doing changes and deploying those changes to the server is quite a hindrance so I'm investingating about Gulp, a task runner on Javascript.

Sources:

So far this is what I'm doing:

    const gulp = require('gulp');
    
    gulp.task('name', function() {
      console.log('hello');
    });
    
    // Clean the dist directory in frontend
    // Clean the views directory in backend
    
    // build the frontend
    // Copy the frontend to th ebackend views folder.
    
    // Git update both.
     
    
    
    gulp.task('default', ['name']);

Now I just have to fill the blanks.

So now I have an environment in which I can change stuff in the frontend, run gulp and it amends it on the server.

Now I'm doing the Terraform bit to get the infraestructure as code, one of the main deliverables.

## A few days later...

This has taken me ages to accomplish but finally I manage to create the entire site as code. Terraform is a pain in the arse but once it works you fall in love with it. The problem is not what you tell it to do but what you don't. It keeps asking for more details until everything falls into the same VPC, same subnets, right availability zones, etc.

![](/uploads/2018/07/04/shitesite.PNG)

I don't think many people can understand my happiness when this all finally worked. It's done, I've got **one of the deliverables**. Yay!

## But how about the workload?

I have no way right now to test the website underload so I have to emulate it in an API call.

This is what I'm going to use.

[https://github.com/lloyd/node-toobusy](https://github.com/lloyd/node-toobusy "https://github.com/lloyd/node-toobusy")

With that I can make the site unresponsive when is too busy and I can also set workload.

I'm giving it an API call of /makemebusy

That didn't work so I'm going for

[https://www.npmjs.com/package/toobusy-js](https://www.npmjs.com/package/toobusy-js "https://www.npmjs.com/package/toobusy-js")

## Real problems

So I had problems with the deliverables I have to had ready for this TMA, a big major problem is Test-Driven Angular, another one is to make the app bilingual, something I thought it was a "nice to have feature" that shouldn't be in the final ones. The literature bit of this TMA is very weird compared to the previous TMA and the fact that the formatting has radically changed compared to the previous one, dropping sections I found necessary isn't helping either.

Putting the site behind a load-balancer and finding out the right configuration for AWS took a lot of effort, let alone how to write the right Terraform code. For a time I thought I might had to give up onn that, which is central to this project so I'm glad I managed to fix it at the end.

Then instances were all above 89% and I fixed it.

# What I should put on the Appendix

1. Infrastructure as code
2. Parts of the front-end

Right, TMA sent. 
---
title: The server code - Part 2 The development
layout: posts
categories:
- theproject
date: 2018-03-24 16:39:19 +0000
---
Let's start by finishing the videos on security.

I'll have to install a module called validator for the email field and others.

You'll need to define (justify this in the TMA/EMA) the minimum length of the password.

### Jason Web Token

Using material from TM352 you could justify this. The module is called jsonwebtoken

Two important methods, sign and verify. You'll need video 89 to implement this. And:

* Video 90 to undertsand how to implement it in the rest call. Plus the site for JWTs.
* You'll need to create your own scheme (video 90) for this.

You will need to justify the private routes (video 91). Remember UserSchema.statics for model methods. Minute 3:42 for this.

* Video 92 is about hiding the passwords. The library is bcryptjs

You need to explain what salting passwords is...once you learn it yourself. Bcryo genSalt method advantages to prevent brute force attack, use it.

Mongoose middleware will help hide the passwords.

Understanding the storage of passwords is one of the most complex things of the back-end of the web application because I haven't done it before.

* Video 94 is the key because that's the test case.
* Video 95 with findByCredentials to log in users by username and email (and get back the token)
* **Video 99 is the key of how to connect** the data with the user who created it. Minute 4:12

Right, so that's all the videos I needed, now is time to start coding.

### The coding part

Following a method:

1. Create a folder for the project and a subfolder for the backend, run npm init to create a node project.
2. Created an expressjs app that prints Hello.
3. Created a test case with MOcha to test that hello. Put all the tests in a test folder
4. Added the extra dev-dependencies i'll require (mocha, expect, supertest).
5. Set nodemon index.js as the start routine.
6. Wrote some test code

And it works

![](/uploads/2018/03/23/itowkrs.JPG)

Now that I've got the basics of testing my app covered I need to develop all the other test cases but for that I need to model the data first.

On one side we've got users. Users should be made of:

* email
* password
* token

For that I need mongoose. On the other side I need job applications, they should be made of, according to the mockup pictures of:

* role_name
* company_name
* date_applied
* location
* reference __ later _ name_
* cv _ used _ name
* notes

So before I create tests cases the model for this needs to be created in mongoose.

Right, I can create users, log them, unlog them.

### Coding the users

I needed to decide why to choose patch instead of put and I didn't get it but this link got it explained for me

[https://stackoverflow.com/questions/28459418/rest-api-put-vs-patch-with-real-life-examples](https://stackoverflow.com/questions/28459418/rest-api-put-vs-patch-with-real-life-examples "https://stackoverflow.com/questions/28459418/rest-api-put-vs-patch-with-real-life-examples")

I only need to replace so patch is better than put in this case. 

Well the code is there, is just a matter of doing some refactoring now. 

![](/uploads/2018/03/25/Capture.JPG)
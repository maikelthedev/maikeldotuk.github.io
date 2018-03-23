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
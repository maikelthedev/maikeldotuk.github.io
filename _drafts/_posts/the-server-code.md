---
title: The server code
layout: posts
categories:
- theproject
date: 2018-03-11 00:00:00 +0000
---
![](/uploads/2018/03/11/0_kJRU-y-GlI_z0i7o.jpg)

This is going to be a long running post, so it is going to stay in draft mode for a very long time. I've got until the 26th of April to write the server side code but if I finish earlier that is errors and bugs that I can fix. Until then this post will be open.

The reason to use SPA framework is because they feel like a mobile application, they don't stop or stall while you move through the page making you feel it is a very reactive interface, almost as a desktop application.

I will write the code by following the ten requirements of the web application and using Max's course in Udemy as a refresher through it whenever I feel I'm stuck ([reference](https://www.udemy.com/angular-2-and-nodejs-the-practical-guide/learn/v4/t/lecture/5866976?start=0))

I didn't feel the course from Max was enough for the backend so I'm going to the course of Andrew Mead for this. I reset the progress, is a course I already did long time ago, so I'm going to start from scratch on it.

### Import lectures

* Video 9: reminds you how to use string interpolation inside JS.
* Video 10: how to import from relative paths (other files) and how to use **exports.**

## Fast-forward

### Express.js refresher

* V 11: Installing lodash
* V 45: Using middleware (next and next() );

Ok, following the course step by step is going to waste much more than the 10 hours I've got allowed for this project so I'm skipping stuff and directly accessing some sections. Right now I'm on Section 5 Lecture 40, all about Express. This is a just a quick refresher.

![](/uploads/2018/03/12/DYFMewSXkAAA3_V.jpg)

I bought my computer from Cex, formerly known as Cash Converters, hence why the local username appears as Cex. I couldn't be bothered to change it.

Now getting into the part of sending JSON back. This is important because is all almost everything we're going to send from the web server. The front-end in Angular will communicate with a Restful service that will access the Mongo database. So the back-end, the Express.js server I'm building now is that Restful service.

I'm using a chrome extension called JsonView ([reference](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en)) to see this, it facilitates shaping the JSON that comes back from the server in a coherent, easy to read and navigate format.

Now I remembered how to set up the static directory with express.static()

Now moving onto templating engines, I'm going to use handlebars. The module name is hbs. I'll use this for pages that are generated dynamically. Which ones? The SEO ones. **More on this later.**

Remember that 'views' is the place expressjs by default will search for templates.

Now, with HBS we could just omit the front-end and use it for everything. But that wouldn't be a responsive website and hence why are we dividing it in two.

Now about passing data to the template. This is video 43.

For styling I'll use Bootstrap but on the server side code I won't need it.

Now about using partials for templating, for example to include the copyright code on every code.

I've learnt also how to get the current year using helper functions for handlebars. This other page can help understand that ([reference](https://www.sitepoint.com/a-beginners-guide-to-handlebars/)).

Request or req is one of the most important objects to access thorugh middleware, this page tells you all the parametres that it holds ([reference](http://www.murvinlai.com/req-and-res-in-nodejs.html)).

Note that by default node doesn't come with all locales and you need to install them and set an environment variable ([reference](https://github.com/unicode-org/full-icu-npm)).

Using fs.appendFile a server log can easily be saved of each connection.

Middleware will be used to check authentication for example.

### Test-driven JS back-end development with Mocha.

This is the start of no more experiments and actually writing my own code. As soon as I've got test cases then I can actually write the Rest API. This test cases are an actual **deliverable** so I could append it to the TMA02 as an annex and the EMA.

Remember that Mocha must be saved as --save-dev such as

    npm i mocha --save-dev

And now, beware this is Behaviour-Driven Development (BDD) so you will have to explain that and also what the mocha framework is.

Note the way it has to be written in packages.json

    "test": "mocha **test.js", 

And that says which files mocha has to check.

So it is a matter of using it('The message', callback) and in the callback use

    throw new Error('The message');

to get the test. Error can use string templating so you could use that to see what was receive instead.

Now the point is how to test express applications.

* Video 52. To rerun test when the files change. So use:

  nodemon --exec "npm test"

So now every time the test are changed it reruns. Other way is to use test-watch in packages.json

    "test-watch": "nodemon --exec \"npm test\"",

Now with

    npm run test-watch

You get it running

So now you combine Mocha with Expect which is an assertion library. Up to second 36 on video 53, Andrew explains what is an assertion library for, use it for your TMA when you need to justify why you use it. Here there is **cheatsheet** for **expect** ([reference](https://devhints.io/expectjs)).

Basically _expect_ saves writing code. Remember that to compare equality of objects toBe doesn't work but toEqual.

Async calls are a bit harder. This is an example of it, what matters is to add done in the call and in after the return.

    it('should return something', (done) => {
      aSync('Something', (result) => {
        expect(result).toBe('Something');
        done();
      });
    });

And that would do the job. Without calling done the test won't ever finish.

* Videos 55 and 56 are the ones that matter. Testing express applications.

Andrew recommends a library called SuperTest that makes it simple ([reference](https://github.com/visionmedia/supertest)).

The last thing to remember is using **describe** which is part of the Mocha framework to group the tests. This is its usage:

    describe('Whatever you want to say', () => {
    the test;
    the other test;
    });

So, the things to remember are:

* to use SuperTest for Express applications.
* To export whichever variable or object you'll require for the supertests.
* To use describe to group the test cases. 

So, without getting the refresher in Mongo I can finally already start writing test code. 

Spies can built in with Expect but they aren't needed for my project. 

This link in StackOverflow puts an example of testing a RestAPI and therefore MongoDB by extension ([reference](https://stackoverflow.com/questions/47570972/testing-mongodb-database-with-mocha-and-request)).
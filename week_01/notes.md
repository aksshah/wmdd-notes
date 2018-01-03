# week 01 January 03

## agenda
this week:
- intro to course

next week:
- first look at AWS lambda

## main topics this term

### serverless

first things first, there are servers in serverless. serverless more accurately
means that the development team doesn't have to provision, or really think about
the servers at all. Serverless is often used as a blanket term that covers BaaS
(backend as a service) and FaaS(function as a service). In this class generally
serverless will refer to the later. Perhaps the easiest way to think about this
is: instead of writing backend code the traditional way or setting up a server
and writing an application, then running that application. You write a function,
that function performs one task, just like it would in the larger application.
When you want that function to perform the task it was written to perform it is
triggered by an event, when it has finished running and the task is complete
that function is no longer in use until it is triggered again. So your
application is now broken up into individual functions, triggered by events and
only running as they are needed.

[what is serverless, auth0 blog](https://auth0.com/blog/what-is-serverless/)

### microservices

Microservices are an architectural style for writing apps in which functionality
of the whole is made up of a collection of services.

Now if you are thinking, wait; that is what you said serverless is you are
absolutely correct. Throughout this course generally Serverless will refer to
the technology and microservices the architectural style. So serverless is AWS
Lambda and microservices is how a larger application/service is planned and
built using serverless technologies like AWS Lambda. Essentially a
Microservices, as opposed to a 'monolith' is an architectural style that means
breaking an app/service into smaller pieces, each piece performing one function.
This isn't a new concept in computing or app design, but is one that has become
popular for web apps/services in the past 2 years.

[opensource resource on microservices](https://opensource.com/resources/what-are-microservices)

### AWS

primarily we will be working with AWS Lambda

> AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app.
> > [aws lambda](https://aws.amazon.com/lambda/?nc2=h_m1)

during the course we will take a look at frameworks that make working with
a microservices architecture created with AWS Lambda a little easier, such as
the [serverless framework](https://serverless.com/) and
[Apex](http://apex.run/). We will also look at several alternatives to the major
service providers such as [stdlib](https://stdlib.com/) which are a great
alternative particularly for small personal projects.

## what you need for next week

for next week you need a [free](https://aws.amazon.com/free/) AWS account.

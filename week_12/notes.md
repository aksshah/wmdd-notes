# Week 12 March 28 2018

## agenda:
- a recap of microservices
- exam info

## microservices recap

### messages

so far we have been working with small projects that have a relatively small
number of services, so it isn't too tedious to keep track of all of them.
Because of this we are using what is commonly referred to as *point-to-point*
messaging. Each service must contain all of the necessary information needed to
communicate with the services it needs to communicate with. In the class
examples we have been essentially making miniature REST applications so this is
a URL.

A common alternative to this is to create messages queues. client services
publish messages onto your queue and listening services retrieve them.
A message queue obviously introduces greater complexity and needs to be treated
with the same level of care as database management. There are a number of
different methods for actually creating a messages queue as well as existing
services designed for this task. One common technique is the *scatter/gather*
strategy, described in *The Tao of Microservices* as a way to allow partial
information to be collected in the event that one service is down. The idea
being that a business would prefer to stay open and deliver some content if
something isn't working, than shut down for every little problem. The example
provided in this book is an online newspaper, each page has multiple components:
the article, advertising, author bio, related content... using the scatter
gather method one services requests all of this information and another collects
it with a time limit. So if one service is down the page still loads and
provides the reader with some, or most of the information.


### DRY (don't repeat yourself)

You can and should ignore this when creating microservices. It is often
necessary to repeat yourself.

### loose coupling, high cohesion

I have mentioned these before, but they are really important to understanding
the structure of good microservices, so worth repeating.

a system composed of loosely coupled services can remove or significantly change one service without
breaking others.

high cohesion helps to achieve this by having related behaviour together.

### code is disposable

your code isn't precious. a service should be throw-away, in that it is only a
small amount of work for a single developer to replace it should it need to be
replaced. 

### how small is small

There is obviously no exact number of lines of code, although I have heard 100
lines of code used. I think that the two above topics are a better answer to
this. If you meet both of those requirements your code per service should be
relatively low lines count.

## take home exam

exam questions will be posted Monday April 2nd on github

the exam will consist of several questions and a small project

Submission instructions as well as the deadline will be provided with the exam
material

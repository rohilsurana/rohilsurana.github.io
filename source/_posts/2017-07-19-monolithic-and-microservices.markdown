---
layout: post
title: "Monolithic and Microservices"
date: 2017-07-19 07:16:08 +0530
comments: true
categories:
---

<center>{% img center /images/mono_micro.jpg %}Picture made using <a href="http://shakydraw.com">ShakyDraw</a></center><br>

Recently we had an downtime at the place where I just started working. It took around an hour to get the servers up and running again. When they traced back they found out that fault occurred in one microservice and propagated to others. While discussing the cause of the problem, we were questioned if it would had been easier to trace and correct the fault if the architecture had been Monolithic.

Monolithic architecture means that the system has been designed to be self-contained, all parts required to build and run the whole system are included in a single package. For example a single Java Web Application, or a single directory that has all the NodeJS code.

Monolithic systems are considered to be -

  * easy to develop as they use single language and IDE for the development purpose
  * easy to deploy as there is only a single package that has to be deployed on a server
  * simpler to get started with as all the code lies in the same place
  * simpler to scale as you can scale by running multiple instances of the application behind a load balancer

But as the size of the application increases -

  * the time taken for each test run increases as well and so does the time to deploy it
  * it also becomes difficult for anyone new to completely understand the whole code.
  * will be difficult to reimplement as the whole system will have to implemented
  * impossible to scale individual functionalities that are receiving most hits, need to scale whole application

Microservice architecture has a set of loosely coupled, collaborative services. These services all need to work together for the system to work as expected. Their is no specific example for this as these services can independently be written in any language that is deemed useful by the developing team.

Microservice systems are considered to be -

  * easier for developer to understand as each small service only has contracts that it has to maintain
  * faster to test as unit tests are only run for service that is being deployed
  * better at fault isolation as all services are running in different nodes
  * easier to reimplement in case the language currently being used in one of the services has some serious issues, it can be reimplemented by just maintaining the contract with other services
  * easier to deploy as each service can be deployed independently
  * easier to scale as you only need to scale the service that is receiving more traffic
  * difficult to deploy as added complexity of a distributed system
  * having lesser throughput than monolithic counterpart as most of the inter-service communication also happens over network
  * more memory consuming since all services are in different containers that have a memory overhead

Hence the developer or team has to make a choice on the basis of the conditions under which they have to develop the application. Here at Go-Jek we initially has a monolithic architecture that was slowly moved to a microservice based architecture, as did most of the well known services on the internet.

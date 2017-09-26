---
layout: post
title: "Working with Ruby on Rails and PgSQL on Vagrant"
date: 2017-08-10 03:26:15 +0530
comments: true
categories:
---

<center>{% img center /images/vagrant-postgre-ruby.jpeg %}</center><br>

At our bootcamp we were working on a Rails application that uses PgSQL for database. At DevOps part of bootcamp we were told to setup and use Vagrant to run this application. Most of us had never used Vagrant before. It was steep learning curve understanding how it works and how to use it.

Vagrant is a tool built upon already existing virtual machine providers like VirtualBox, VMWare, etc. to simplify workflow and remove any worry about the environment in which our code will run.
The name suggests that it is meant for code that can reside any where, so as a vagrant your code can live anywhere, irrespective of the environment present there.

There are many guides out there that will help you to setup a Vagrant virtual machine for Rails, but I found that most of them missed a very important information in the guide. When you setup your Vagrant virtual machine using a Vagrantfile, there are two users that are created by default, a `root` user and a `vagrant` user. Now why this is important is that by default the provisions run by the Vagrantfile are executed by the root user, but when you `ssh` into you Vagrant machine using `vagrant ssh` you are logged in as the `vagrant` user.

Now when you try to use PgSQL for your Rails app, when logged in using ssh you see the vagrant user and hence create a PG role with vagrant name so you won't have to use a password in you Rails app for connecting to PG, and when you try to start the Rails app tests in the provisions, you fail because the provisions are being executed by the root user.

So I found out three ways to resolve this error -
  - Create the PG role with name as root
  - Change the user to vagrant user before starting the Rails app tests in provisions
  - Run provisions with the vagrant user

The first option seems the easiest as all you have to do is change the name of the role in the provisions. But you will need to use different user for serving the app as any vulnerability in your app can give a person access to the root user on your machine.

For the second option you just need to change the user to vagrant in your provisions script and run tests with that.
You won't need to use a different user when serving the app.

The third way is very similar to the second way except that the functionality is provided by Vagrant itself. You can set the provisions to run with the vagrant user by setting `priviledged: false` in the Vagrantfile for the provisions, but then you will need to use `sudo` many times in your shell scripts.

I am trying to find out which is the most appropriate way to resolve the error and will post about it when I find out. Till then - Happy coding.

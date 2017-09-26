---
layout: post
title: "It's not optimization"
date: 2017-07-17 02:34:24 +0530
comments: true
categories:
---

<center>{% img center /images/got_premature_optimization.jpg %}</center><br>

>"We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil." - Donald Knuth

"Premature Optimization" can be defined as optimizing before we know that we need to. It can be considered as breaking YAGNI (You Aren't Gonna Need It). This can result in a design that is not as clean as it could have been or code that is incorrect, because the code is complicated by the optimization and the programmer is distracted by optimizing.

It can be
In short the programmer thought it's good to complicate the code to extract a little bit of optimization out of it. What they do not realize is that this optimization will be useless, unless done after following the the only rule of optimization -

  *First profile, and then attack the bottleneck*

The error that most people make is that they do not look at bigger picture, they optimize the code that they think will affect performance but they do not realize that that was not the bottleneck. Many times these optimizations break the design that the programmer initially had in mind. This results in unwanted complexity of the code. When they do this they end up creating a trap for future contributors to fall into and generate bugs.

The right way of approaching performance optimization should be to create a project according to the initial design and then perform metrics on it to find the bottleneck. Once you find out the performance you will know which parts are worth the effort. Think about the cost and how much complexity you will add to the code as well. Do not mistake premature optimization with refactoring, if possible try to refactor your code to optimize it without breaking the design you are following.

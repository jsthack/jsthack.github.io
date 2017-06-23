---
layout: post
author: Cosmin Haims
title:  "02 / Git Team Workflow"
date:   2017-06-20 10:18:00
categories: Git Workflow
---

<p>I'm assuming if your reading this blog post you use Git, or are atleast familiar with it. There is no self respecting developer or engineering team out there who isn't using git in their workflow. As you know I'm not a traditional front-end developer, I didn't get a computer science degree, and most of my dev skill sets has been self taught. If your a designer who doesn't use Git, all I can say is <span style="color: #9638ff"><b>Version Control is Non Negotiable.</b></span></p>

<h5>Quick Overview of Git</h5>
<p>'Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.' It was designed by Linus Torvalds, the creator of the Linux Operating System Kernal. You would be blown away by the number of software projects, that rely on Git. Git is a DVCS System (Distributed Version Control System). Instead of having your full version control history in a single place, like many older VCS (CVS/Subversion). With Git everyones working copy of the code base, is also a repository that can keep the full history of all global changes. Git was also designed with performance, security and flexibility in mind.</p>

<h5>Using Git with Teams</h5>
<p>There are many different ways to use git, and different workflows work for different teams. I'm only going to be explaining the way my Team uses Git, this workflow might not work for you. I'm head of UI/UX on my team, and also do front end development implementing UI changes. Our app is a very data intensive IOT web application, and code base is quite big, and growing every day. Working efficiently while collaborating is important, and when you have multiple developers all working on different aspects of the app at the same time it can get hectic. This is where Git comes in. Not only does it help with Version Control, but it also helps with collaboration, making sure people aren't working on stale code, and pushing and testing code for production.</p>

<h5>Working with Branches</h5>
<p>Below is workflow chart showing the process of pushing code from a working branch up to the server. Branches are the key. It's a best practice, especially with teams to never be working on the Master branch. The master branch should always just contain the most recent healthy build of your project. When a team member wants to start working they will do the following.</p>

{% highlight bash %}
#clone master from remote repo to your machine
$git clone <remote repo path>
{% endhighlight %}

{% highlight bash %}
#change to newly cloned local directory
$cd <local repo path>
{% endhighlight %}

{% highlight bash %}
#create new working branch from master
$ git checkout -b <new branch name>
{% endhighlight %}

After you have created a local working branch from master, you are ready to work. The new branch you created is where all your changes will be, this means whatever work you do, won't effect the stable master branch.

<h5>Consolidate Changes</h5>
<p>On my team we consolidate changes or bug fixes into their own branches. It's better to have different branches for each thing your working on. This helps consolidate code changes, also if something breaks it's very easy to discard or roll back the bad code. For example If I was working on the main Nav of a web app, the working branch could be named app_mainNav, and the only new code that will be in this branch is for that part of the app.</p>

<h5>Merging Local Changes</h5>
<p>Once you are finished with a set of local changes, you will then need to push your changes to the remote repo, so they can be merged with the master branch. I'll explain this some more but first take a look below at this flow chart showing the workflow my team uses.</p>

![flow](/assets/images/git-team-workflow.png)

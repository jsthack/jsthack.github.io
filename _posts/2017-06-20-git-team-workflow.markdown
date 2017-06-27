---
layout: post
author: Cosmin Haims
title:  "02 / Git Team Workflow"
date:   2017-06-20 10:18:00
categories: Git Workflow
---
I'm assuming if your reading this blog post you use Git, or are atleast familiar with it. There is no self respecting developer or engineering team out there who isn't using git in their workflow. As you know I'm not a traditional front-end developer, I didn't get a computer science degree, and most of my dev skill sets has been self taught. If your a designer who doesn't use Git, all I can say is <span style="color: #9638ff"><b>Version Control is Non Negotiable.</b></span>

![flow](/assets/images/gitflow/gitflow1.png){:height="100%" width="100%"}

##### Quick Overview of Git
'Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.' It was designed by Linus Torvalds, the creator of the Linux Operating System Kernal. You would be blown away by the number of software projects, that rely on Git. Git is a DVCS System (Distributed Version Control System). Instead of having your full version control history in a single place, like many older VCS (CVS/Subversion). With Git everyones working copy of the code base, is also a repository that can keep the full history of all global changes. Git was also designed with performance, security and flexibility in mind.

##### Using Git with Teams
There are many different ways to use git, and different workflows work for different teams. I'm only going to be explaining the way my Team uses Git, this workflow might not work for you. I'm head of UI/UX on my team, and also do front end development implementing UI changes. Our app is a very data intensive IOT web application, and code base is quite big, and growing every day. Working efficiently while collaborating is important, and when you have multiple developers all working on different aspects of the app at the same time it can get hectic. This is where Git comes in. Not only does it help with Version Control, but it also helps with collaboration, making sure people aren't working on stale code, and pushing and testing code for production.

##### Working with Branches
Below is workflow chart showing the process of pushing code from a working branch up to the server. Branches are the key. It's a best practice, especially with teams to never be working on the Master branch. The master branch should always just contain the most recent healthy build of your project. When a team member wants to start working they will do the following.

##### Setting Up Local Git Structure:

{% highlight bash %}
#clone master from remote repo to your machine
$ git clone <remote repo path>
{% endhighlight %}

{% highlight bash %}
#change to newly cloned local directory
$ cd local <remote repo path>
{% endhighlight %}

{% highlight bash %}
#create new local master branch from remote master
$ git checkout -b <local master name>
#your local master is the branch you will be pushing
{% endhighlight %}

{% highlight bash %}
#create featured (working) branch from local master
$ git checkout -b <feature branch name>
#work is done on different feature branches / this helps organize changes / and prevents breaking
{% endhighlight %}


After you have created a local working branch from master, you are ready to work. The new branch you created is where all your changes will be, this means whatever work you do, won't effect the stable master branch.

##### Consolidate Changes
On my team we consolidate changes or bug fixes into their own branches. It's better to have different branches for each thing your working on. This helps consolidate code changes, also if something breaks it's very easy to discard or roll back the bad code. For example If I was working on the main Nav of a web app, the working branch could be named app_mainNav, and the only new code that will be in this branch is for that part of the app.

##### Merging Local Changes
Once you are finished with a set of local changes, you will then need to push your changes to the remote repo, so they can be merged with the master branch. I'll explain this some more but first take a look below at this flow chart showing the workflow my team uses.

{% highlight bash %}
#switch to local master branch
$ git checkout <local master branch name>
{% endhighlight %}

{% highlight bash %}
#merge feature branch with local master branch
$ git merge <feature branch name>
#if you have any merge conflicts resolve them and do a $git commit -m""
{% endhighlight %}

##### Push Local Changes:

{% highlight bash %}
#push your local master to your remote repo, and set the upstream
$ git push -u origin <local master name>
#your local master is the branch you will be pushing
{% endhighlight %}

{% highlight bash %}
#last but not least, send a merge request so your local master can be merged into the remote master
{% endhighlight %}

![flow](/assets/images/gitflow/git-team-workflow.png){:height="100%" width="100%"}

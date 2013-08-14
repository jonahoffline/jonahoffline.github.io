---
layout: post
title: "RVM for your Ruby projects"
date: 2013-07-29 23:39
comments: true
categories: 
- Ruby
- Rails
- RVM
---
While doing some pair-programming with a friend of mine, I noticed he had [RVM](https://www.rvm.io) installed but only used one gemset for *everything*. As a result, his machine was slow and polluted with old gem versions. You could say that it was almost a mirror of [Rubygems](http://www.rubygems.org). I wondered how many ruby developers had the same problem so I decided to share this.


## Installing RVM

If you have never used RVM, you've been missing out. It won't do the dishes or clean your room, but it will make you happier. RVM allows you to easily install, manage, and work with multiple ruby environments. Avoiding version conflicts and maintaining any ruby project, gem, or Rails app organized is now a breeze.

Let's get it out of the way and install it along a stable version of Ruby.

	$ \curl -L https://get.rvm.io | bash -s stable --ruby
	
Depending on your internet connection and computer, it will take a few minutes. Once that's done, you will need to reopen your shell window or run:
	
	$ source ~/.rvm/scripts/rvm

Let's verify that RVM is loaded and that everything is installed correctly. 

	$ rvm current

You should now get a Ruby version (e.g., `ruby-2.0.0-p247`). If you didn't, run `rvm notes`.
	
## Using RVM to organize your projects

Instead of globally sharing one gemset for all projects, let's create one for our imaginary **Quantum Kittens** Rails App.

Just enter the directory and run:

	$ rvm --create --ruby-version ruby-2.0.0-p247@quantum_kittens
	
The command will not output anything, but if we run `ls -a` you will notice there are now two files in the directory.
	
	.ruby-version
	.ruby-gemset

From now on, RVM will automatically change into that ruby version (`ruby-2.0.0-p247`) with any gems you install to its self-contained gemset (`quantum_kittens`) every time you enter that directory. You should check these two files into your source control.


#### Other useful RVM commands

This article would not be complete without a few of the most used RVM commands.

To verify the current version and gemset:

	$ rvm current

To get a list of gemsets:
	
	$ rvm gemset list

To get a list of all the installed versions of ruby:

	$ rvm list	
	
To view available versions of ruby to install:
	
	$ rvm list known

To install	another ruby version:
	
    $ rvm install rbx-head
    
To set a default ruby with a new gemset:
	
	$ rvm --create --default use rbx-head@kawaii_gems

To remove a gemset:

	$ rvm gemset delete evil_gems

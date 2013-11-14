---
layout: post
title: "The Science of Fucking Up"
date: 2013-08-28 05:29
comments: true
subject: Growing
reading_time: 5
categories:
- Growing
- Learning
- Experience
- FailDrivenDevelopment 
---
It was my second or third week as a consultant at a prestigious Telecommunications Company. To beat traffic, I would get up at 4 A.M everyday. Each drive would only take me 12 songs, but I had to wait in the parking lot for 36 more songs and two cups of coffee. 

After the introductory twenty-dollar tour, I realized I was in Hell. The whole team that kept their infrastructure from burning had resigned and left the same way you would avoid a plague. Documentation was outdated and mostly useless. There was no version control for their in-house software which was written using .NET (2.0), T-SQL, Java, Python and PHP. As if this wasn't enough, I was alone with two ~~charming~~ managers who didn't seem to be aware of their sinking ship.

There was a list of tasks that had to be done weekly. One of them involved running a few python scripts that would screen-scrape customer data from an ancient server, parse each entry with a RegEx recipe that looked like a black magic spell to finally insert the result into an unpatched vintage SQL Server. These scripts would get the username, unencrypted password and host to scrape from an internal web service. There was no way of telling if something went wrong until a few days. As I fired each process, this is really what went through my mind: 
This is no different from stabbing in the dark. 

I won't get into details, but let's just say the rest of their system was a ghetto. I've read about drug cartels with better workflows. I envied the janitors, even though our jobs were closely related. We both had to clean up these people's shit. 

The week was almost over. One more game of Solitaire and I would finally go home. Suddenly, I get an email saying they can't generate some reports and they're pissed off. After giving away an extra-hour and doing some Sherlock-worthy guess work, I noticed there were two versions of the screen-scraper. An unfinished "backup" made during the development of the script and the final version I should have ran. It's an understatement to say I had fucked up big time. 

### Problems are opportunities in disguise

It could be argued that the situation could have been avoided If I had inherited better documentation but I blame myself. Like many developers, I let my ego get in the way. The little perfectionist inside me had focused more on their flaws and how bad their system was designed instead of taking a more positive approach: doing the best you can with what you have. Problems are opportunities in disguise. 

### Fail Driven Development (FDD)

Since this incident I adopted a personal development cycle I based on [TDD](http://en.wikipedia.org/wiki/Test-driven_development). 

**Fail Driven Development** consists of three steps:

1. Life writes a failing test for you
2. You write your fate, you make it pass
3. Clean up and remove any unnecessary concept, behavior or belief slowing you down

This cycle is constantly taking place, don't be lazy and fix your bugs!




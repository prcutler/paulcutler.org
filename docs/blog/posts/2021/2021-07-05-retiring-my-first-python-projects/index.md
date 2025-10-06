---
title: Retiring My First Python Projects
author: Paul Cutler 
type: post 
date: 2021-07-05T14:30:00 
comments: true
categories:
  - Python
tags:
  - Python
  - NFLPool
  - MLBPool2

---
It’s a sad weekend in my workshop.  I’ve officially retired and archived my first two Python projects, [NFLPool](https://paulcutler.org/project/nflpool/) and [MLBPool2](https://paulcutler.org/project/mlbpool2/).

I vividly remember Thanksgiving weekend a few years back when I decided it was time lo learn to code.  I bought a few O’Reilly books on a Black Friday special and quickly learned that I can’t learn from books.  It would be another year and a half before I buckled down and really learned Python.

I’m of the opinion that if you’re going to be community taught (I don’t believe you’re really self taught - you’re learning from the community of users and teachers, whether that’s in a formal course you’re taking online or asking questions on Reddit or Stack Overflow) you have to have an end goal in mind.  It’s one of the most common questions I see on Reddit:  “I’ve learned the basics, but I don’t know what to do now?”  Most people need an itch to scratch, a problem to solve to really apply what they’ve learned.

NFLPool was that for me.  We had spun NFLPool off of MLBPool2 and I was the commissioner.  I was doing it all in a spreadsheet manually, each Tuesday having to look up the team and player stats and I knew there had to be a different way.  And there was.

MLBPool2 was based on the NFLPool code, which made it easier to get up and running later.  But neither project would have existed if it hadn’t been for [Talk Python’s Python for Entrepreneurs](https://training.talkpython.fm/courses/explore_entrepreneurs/python-for-entrepreneurs-build-and-launch-your-online-business) course.  The skeleton of both sites came from that course and modifying that code base taught me so much about Python and Pyramid, the Python web framework that powers both sites.

I didn’t know if I would stick with it, but here I am four or five years later, still learning and branching out in how I use Python.  I’m still working on another web site, building it twice with two different frameworks (I really want to learn FastAPI) and also learning how to use hardware with Python.  (More on my experiments with the Raspberry Pi, rotary encoders, soldering and more will be recapped in another post).

NFLPool never really had enough players to survive.  MLBPool2 did, but in the second year of it being online, the commissioner changed some of the rules and how points were scored.  Updating the code introduced a bug in how ERA is calculated and I was never able to find the bug.  

I thought I had turned off registration in both applications, but script kiddies are still registering themselves with NFLPool.  Before they find a flaw with SQL injection or something else stupid, I’ve replaced both sites with a landing page that redirects to the project pages here.  If it wasn’t for them, I would have left the site and scores up to show what had been built.  I've officially put both repositories in Archive mode on Github.

In the end, they both served their purposes in giving me motivation to learn how to code and for that I’ll always be grateful.

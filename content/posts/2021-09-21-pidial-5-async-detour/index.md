---
title: Introducing pi-dial - Part 5 - A detour into async
author: Paul Cutler 
type: post 
date: 2021-09-21T18:30:00
categories:
  - Python
  - Hardware
tags:
  - Python
  - Raspberry Pi
  - denonavr
  - pi-dial

---
(Catch up on the [pi-dial series of blog posts](https://paulcutler.org/tags/pi-dial/).)

With the hardware prototyping done, it’s time to write the code that is at the hart of pi-dial.

I need the hardware to do four things, all in Zone 2 of the receiver:
	1. Change the inputs (CD to Phono to Tuner, etc.)
	2. Change the volume up or down
	3. Mute and un-mute the receiver

I mentioned briefly in my first post that the `denonavr` open source project has the methods I’ll need for this.  It is possible to directly interact with the receiver as it has all of the functionality built using custom HTTP calls.  But it’s definitely not optimal, leading to projects like `denonavr`. 

Late last year, the `denonavr` project was re-written to use Python’s `async`  library.  I know of async, but I don’t know how to use async.  

I found the documentation for using async with `denonavr` kind of sparse.  I opened an issue in the project’s Github repo and received some pointers to get started.  

After that, it was time to dive into `async` itself.  I purchased the [Everything Bundle](https://training.talkpython.fm/courses/bundle/everything-bundle-2021-q3) from Talk Python Training earlier this year which included the [Async Techniques and Examples](https://training.talkpython.fm/courses/explore_async_python/async-in-python-with-threading-and-multiprocessing) course.  

I kind of understood it?  But not enough that I am going to use it (right now).  I’m still very much a novice at coding in Python and I’m just trying to build something between a prototype and minimum viable product.  This was not a rabbit hole I wanted to go down right now, but I might in the future.

I did take some time to update the project’s documentation with more `async` examples to make it easier for the next person.  Those changes were merged in a couple weeks ago, which is nice.

Thankfully, the `denonavr` project still includes legacy support, which was pretty easy to get up and running, with the exception of one thing, which I’ll cover next time.

*A brief aside:  I feel bad for users who ask a question and don’t get a response in open source projects.  Even worse, in my opinion, is adding a bot that will automatically	close those questions or issues after a period of time without a response.  Having been involved with a couple of open source projects, I understand how frustrating it can be for users to ask the same questions over and over or have a repository filled with “issues” that really aren’t issues.  But then write some documentation to help those users!  Don’t ignore them and then automatically close the issue.*

Next up:  Finally writing the Python code to power `pi-dial`. 

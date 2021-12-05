---
title: SilverSaucer and FastAPI Progress Update
author: Paul Cutler 
type: post 
date: 2021-12-05T11:00:00
categories:
  - Python
tags:
  - silversaucer
  - silver-saucer
  - Python
  - FastAPI

---

I’ve made significant progress this weekend in taking the [Building Full Web Apps with Fast API](https://training.talkpython.fm/courses/full-html-web-applications-with-fastapi) training from Talk Python.

I’m enjoying the course and it’s cool to learn how `async` works in a web application.  My site will be far less complex than the training and I’ll probably skip the database part, though I might want to wire that up later depending on how fast the Discogs API really is.

One of my favorite things about taking courses from Michael Kennedy and Talk Python is that the design patterns are consistent across courses.  While my knowledge of Python is sill limited, I was able to pick this up quickly as I move from a pattern of `controllers` in Pyramid to doing most of the same work, just now in the `viewmodel` itself in FlasAPI.  At one point I was pretty confused, because I had the knowledge of where we were going in the training, it just wasn’t there yet.  As I stuck with it, it made more and more sense.  (Nice work, Mr. Kennedy!)

Obligatory work in progress screenshot, with a new logo coming soon:

![Silver Saucer homepage running on FastAPI](silversaucer-fastapi.png#center)

After I finish up coding the login piece, I’m going to start work on the Discogs integration.  Hopefully it won’t be too hard to move that over as I did have it working in Pyramid.  I spent way too much time yesterday working on Bootstrap and CSS to tweak the site.  It was a bit frustrating as I really don’t know Bootstrap (or CSS for that matter).   In the end it’s close to what I want, but I never was able to get horizontal lines working.  I would never make it as a frontend developer.

I also had an aha moment for phase 2.  In phase 2, when I select a record to play (or from random), I want it to display the album art on my LED matrix.  I wasn’t sure how that was going to work if I did it on a public website.  I was playing around with the idea of hosting it in the house on a Raspberry Pi for local access only, but doing the login chapter gave me an idea.  

I’m going to disable the ability to register logins on the site and not link to the login page.  I’ll be the only one who can login, and with the stored cookie, it will know it’s me.  If it’s me, the site will send a MQTT message back to the MatrixPortal controlling the LED to display the art.  I just finished setting up my MQTT Mosquitto broker, so hopefully I can get this to work.  MQTT is new to me, but I know CircuitPython already integrates with it.  But that’s why that is phase two.  Let’s not put the cart before the house because I already have so many projects….


#blog# #blog/python

---
title: December 2021 update and next steps
author: Paul Cutler 
type: post 
date: 2021-12-22T10:30:00
categories:
  - Python
tags:
  - silversaucer
  - silver-saucer
  - Python
  - circuitpython

---

Now that I’ve semi deployed [Silver Saucer](https://silversaucer.com), with working SSL, it’s time to think about what’s next as the year comes to an end.

I can either start working on the “Choose an album” functionality or I can start working on the IOT / image piece.

The “Choose” uses similar methods to the random functionality, but first it must return a bunch of lists and then display them in a drop down box.  The user chooses what they want to play, hits submit, and that artwork appears. 
I need to build the methods to return the various lists and decide how many choices and what happens with each one on POST.

I don’t have Javascript installed, so one option is to take the HTMX course offered by Talk Python for interactive drop down menus.  

Either way, some research and some work to do.

The second option I thought was going to be a lot easier than it turned out to be.  I know the image URL location from the Discogs API, now I need to pass that to the MatrixPortal  and 64x64 LED Matrix display and draw it. 

I’ve spent most of the last two days trying to wrap my head around `displayio` and other drawing libraries.  First, the LEDs only support bitmaps, and those have strict rules.  ImageMagick has a `convert` tool [built in to help]([GitHub - todbot/circuitpython-tricks: Some CircuitPython tricks, mostly reminders to myself](https://github.com/todbot/circuitpython-tricks#image-slideshow)) with converting images at the command line.  I can convert them, and display part of them, but I haven’t figured out how to display them at 64x64x yet, and that’s been most of the last two days.

But even before I know which image to draw, I need to send a message from the SilverSaucer.com server to the MatrixPortal.  I’ve successfully installed MQTT using SSL (which also took a good chunk of all day Sunday) to do that.  Now I just need to code the subscriber portion in the MatrixPortal and add the push in the web app.  “Just”. 

So that’s where I’m at.  I need to pick one and stay with it as I’ve been kind of jumping around as I get stuck.  And I’m very stuck, but writing things down does bring a greater clarity for what needs to be done.

---
title: December 2021 Project Updates
author: Paul Cutler 
type: post 
date: 2021-12-01T15:00:00
categories:
  - Python
  - Hardware
tags:
  - Python
  - Raspberry Pi
  - pi-dial
  - silver-saucer
  - 3D-printer
  - CircuitPython

---

Since my last blog post just over a month ago, I've been extremely productive.  I have a few blog posts planned over the next week (no, really, I swear) sharing some updates on a number of projects I've been working on.

The 3D Printer I bought back in September has been keeping me very busy.  Not just learning how to use it, but also constant tweaking and maintenance it needs.  I bought a Creality Ender 3 v2 and as I like to joke about it, I have more time than money to spend on a 3D Printer.  The Ender series is inexpensive, but it does take a lot of work to maintain it.  I read once that you will learn as much about the hardware as you will about 3D printing if you buy an Ender series, and it's definitely true.

Learning CAD software has also been a time consuming process.  Sure, there are thousands of pre-made plans you can print on your printer, but sometimes you need to customize something or build something just for you.  In my case it's a new speaker stand for my AudioEngine P4s that integrates an Adafruit rp2040 Feather with Neopixel FeatherWing.  Trying to figure out how to get the USB-C cable to work inside the stand was more complex than I thought it would be.  As we speak, I'm printing - what I hope - is the final version.

The rp2040 Feather and NeoPixel FeatherWing is another project that I've spend considerable time on the last few months and more on that soon.

I also wrapped up version one of the Pi-Dial project last weekend.  I made some tweaks to the code and it's working exactly as I want.  If and when I get more time, I'm already thinking about version 2 which use Python's `asyncio` library. I could also pick up a Raspberry Pi Zero and make a version that uses that in a much smaller enclsoure.  It may even be possible to embed that in a speaker stand as well, but the LCD would take up most of the front and I'd have to mount the rotary encoders on the side.  I have enough projects though right now...

Last but not least, I've started working on Silver Saucer again.  Looking at the blog, it's almost exactly a year since I spent significant time on it, which amused me.  I just finished merging the change from Pyramid to FastAPI in and now I need to re-write the Discogs integration.  I'll write more on that this week as well.  I also have some cool things planned that will use an Adafruit MatrixPortal and LED matrices to display album art of what I'm listening to, but that's phase two.

More to come.  Really!
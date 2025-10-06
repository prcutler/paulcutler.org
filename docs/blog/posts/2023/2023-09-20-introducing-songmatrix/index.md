---
title: Introducing SongMatrix
author: Paul Cutler 
type: post 
date: 2023-09-20T18:00:00
categories:
  - circuitpython
  - python
tags:
  - circuitpython
  - music
  - python
  - songmatrix

---

I listen to music.  A lot of music.  If I’m in my home office I’m usually listening to a record, and if not, the [radio](https://thecurrent.org).  But I’ve always been an album person, not into playlist (or mixtapes to date myself).  I’ve found by listening to albums front to back, I don’t always learn the song names.

Just a few weeks ago, I came across the `shazamio` Python library. I have a Raspberry Pi already sitting on my desk. I also have a couple extra 64x32 RGB Matrices and I recently picked up one of the new Adafruit S3 MatrixPortals, so I have the hardware and software to start a new project.

Enter [SongMatrix](https://github.com/prcutler/songmatrix) (GitHub).

SongMatrix records a short audio sample on the Raspberry Pi and then sends it to `shazamio` to be identified.  It then sends a MQTT message to Adafruit IO’s MQTT broker with the song title and artist.  The MQTT message is received by the S3 MatrixPortal, which then scrolls the song and artist on separate lines, like so:

![A 32x64 Matrix displaying the song Breathing Underwater on the top row and the artist, Metric, on the bottom row](480p.gif)

I whipped up a proof of concept for the Python part of recording audio and sending it to `shazamio`in one Friday evening.  The CircuitPython part took me a couple weeks and I’ll share some of the challenges in upcoming blog posts (no promises).

A special thank you to todbot for bootstrapping some `asyncio` code to get me started.  And to anecdata for spending a good chunk of yesterday helping me get around the last issue and getting to done.  (Well, it’s never *done*).







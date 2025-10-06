---
title: Updating SongMatrix
author: Paul Cutler
type: post
date: 2025-08-02T06:30:00
categories:
  - circuitpython
  - python
tags:
  - circuitpython
  - music
  - songmatrix
---

# Updating SongMatrix

One of my favorite CircuitPython projects I've done is [SongMatrix](https://www.paulcutler.org/project/songmatrix/).  Using a microphone on a Raspberry Pi, it records the song playing in the background, uploads a sample to `shazamio`, uploads the song and artist to [AdafruitIO](https://io.adafruit.com) via MQTT, and an S3 MatrixPortal listens for the MQTT update and displays it on an LED matrix.

I don't run it all the time, but I do like to use it when I'm listening to a new album to learn the song names.  I know a lot of music and can sometimes tell you the name of the artist or the album within seconds of a song starting, but not so much the song title.

I'm using a [2.5mm pitch LED Matrix](https://www.adafruit.com/product/5036) and I have not found a lot of 3D printed cases for either one or two LED matrices. That is, until a few months ago when I came across the [Transit Tracker project from EastsideUrbanism](https://transit-tracker.eastsideurbanism.org).

It uses two LED matrices in a beautiful 3D printed cases that hold both of them and the S3 MatrixPortal and screws together.  I printed it out months ago but couldn't get SongMatrix to work with 2 matrices.

In theory, I should be able to update the MatrixPortal library by changing:
`matrix = Matrix(width=64, height=32, bit_depth=3)` to `matrix = Matrix(width=128, height=32, bit_depth=3)`
But no joy.  I started over with some simple test programs, and I could get a 128x32 matrix to work without a problem, but as soon as I tried in my [original program](https://github.com/prcutler/songmatrix/blob/main/circuitpython/songmatrix-64x32.py) it did not work.

Next I tried to replace the MatrixPortal library by using the pins directly.  Success! But now it doesn't scroll across the matrix, it's just a static display.  It turns out that using `ScrollingLabel` only scrolls when the character count is larger than the `max_character` when setting the text:

```
title_scroll = ScrollingLabel(
    terminalio.FONT,
    text=song_title_scroll,
    max_characters=20,
    color=0xff0000,
    animate_time=0.3
)
```

To get it scrolling, I just did a `len` on the string returned from AdafruitIO and added a string of spaces to get over the 20 character limit to scroll it.

But the weirdest part?  The original program scrolled the text with less than 10 characters.  I tried to recreate it with a basic `ScrollingLabel` example, and of course I couldn't get it to work.  Don't believe me?  You can see the original scrolling the band Metric which shouldn't be scrolling on the project's [GitHub page](https://github.com/prcutler/songmatrix/).

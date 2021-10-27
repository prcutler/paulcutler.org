---
title: Introducing pi-dial - Part 7 - Fixing the LCD
author: Paul Cutler 
type: post 
date: 2021-10-27T17:00:00
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


In my last post, I teased about 3D printing the enclosure.  That will come in the next blog post, I promise.

First, I wanted to talk about an issue I ran into with how text was displayed on the 16x2 LCD screen.  Using the [RPi_GPIO_i2c_LCD library](https://github.com/AllanGallop/RPi_GPIO_i2c_LCD) when I changed the input, if the input had less characters than the new input, the extra characters were staying on the screen.

For example, if I started on the Xbox One input, I would see:

`Input: XBoxOne`

If I changed to the Vinyl input, I would see:

`Input: Vinylne`

Since XboxOne had 7 characters and Vinyl only had 5, the extra 2 characters were staying on the screen.  If I used the `clear()` method, it caused the line to blink.  When I stopped to think about it, it makes sense, as the method clears the space and redraws it.  Since I’m constantly polling the receiver via the API to check the volume and input, it would redraw the screen based on the sleep call I make in the `while` loop at the end of the `pidial-lcd.py` file.

I really don’t want it to blink.  It’s distracting when sitting on my desk.

A quick search later I came across the [RPLCD](https://github.com/dbrgn/RPLCD) library.  They also have their docs on ReadtheDocs and after quickly scanning that, I used it as a replacement.  I had to change just a few lines of code and voila! It’s `clear` command doesn’t blink and it actually clears the LCD before writing to it again and the extra characters were gone.

I’ve said it before and I’ll say it again:  I love open source.

And make sure you thank an open source maintainer today.

<blockquote class=“twitter-tweet”><p lang=“en” dir=“ltr”>Dear <a href=“https://twitter.com/dbrgn?ref_src=twsrc%5Etfw”>@dbrgn</a>: Thank you for the open source RPLCD Python module for LCD screens on the Raspberry Pi. And the fantastic docs. Helped me finish a project today, much appreciated! <a href=“https://t.co/wPHPrejIOF”>https://t.co/wPHPrejIOF</a></p>&mdash; Paul Cutler (@prcutler) <a href=“https://twitter.com/prcutler/status/1452028122224791554?ref_src=twsrc%5Etfw”>October 23, 2021</a></blockquote> <script async src=“https://platform.twitter.com/widgets.js” charset=“utf-8”></script>

Next up:  3D printing and assembly

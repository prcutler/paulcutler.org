---
title: pi-dial - Part 6 - When is a list not a list?
author: Paul Cutler 
type: post 
date: 2021-09-30T14:00:00
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

In addition to controlling the volume of my receiver’s Zone 2, I want to be able to use a second rotary encoder to change the input.  For example,  I may want to change it from the Phono input that I use to listen to records to the Tuner input to listen to the radio.

The Denon AVR-3806 that I own has twelve total inputs, of which I’ve customized a few of the names.  If I print out the list using the `denonavr` library, I see:

`All inputs:  ['8K', 'AUX', 'AppleTV', 'Bluetooth', 'HEOS Music', 'Phono', 'Retropie', 'SOURCE', 'TV Audio', 'Tuner', 'UBP-X700', 'Vinyl', 'Xbox One']`

I’m using Python, so iterating through the list and / or slicing it to get to a specific position in the list shouldn’t be hard.  *Shouldn’t* being the key word.

Spoiler: It was anything but.

If I attempted to iterate through the list, whenever the list position was equal to 8K, Bluetooth, or Source, the list would stop.  It didn’t matter if I tried to move up or down the list.  Now shame on me for not blogging about this earlier as it’s been almost two months since I worked on this particular piece, because I think there was another position in the list that did something similar.  But of course I don’t have great notes or even a lot of commits to go back and look through.

I’m still very much a novice at coding, so I did what most newbies do.  I wrote multiple if / else statements to try and figure out how to get around this limitation.  I was 100% sure it was my code.  Nothing I did worked, even as I wrote very procedural code to step through the list.  I was on vacation the week I worked on this and spent literally the entire week trying to get this to work.

I finally broke down and asked my wife for help.  In about five minutes she [ripped up my if / else statements and wrote a method](https://github.com/prcutler/pi-dial/commit/7a9b99bf643ac0bbc983a99f793d657496a2234c)that passed a variable on whether the rotary encoder was turning up or down.  And then she ran into the problem where the list would get stuck on positions 0, 3, and 7 (8k, Bluetooth, and Source) as you can see in the code’s comments.
A couple hours later she was able to work around it.  This was a fun way to spend a Friday night together!

Neither of us have any idea why those inputs caused the issue, but she was able to write a method to work around it.

The good news is that it wasn’t necessarily my code, the bad news is that I still have so much to learn about the best way to write my code.

The better news?  The code is done!  I have one program that monitors the current input and volume and displays it on the LCD and I have another program that can change the inputs and the volume.

Next up:  3D printing the enclosure.

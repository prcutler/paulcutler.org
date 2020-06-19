---
title: RetroPie Update
author: Paul Cutler
type: post
date: 2020-04-14T20:00:00
categories:
  - Arcade
tags:
  - Arcade
  - RetroPie
  - MAME
  - Emulation

---

I hooked up the Raspberry Pi to test it out.  I did an update and it broke the boot up process and now wants the username and password.  Think I remember that? Nope!  Of course I don’t remember the password.  So I downloaded a new [RetroPie](https://retropie.org.uk/) image which has led me down a rabbit hole of MAME configuration.  The buttons on the controller don’t seem to be mapped correctly.  

I did downloaded a new [romset from the Internet Archive for MAME 0.209](https://archive.org/details/MAME_0.209_ROMs_merged).  Doing further research, I tried both the mame4all emulator and libretro.  Both had unexpected results.  This led me into further research and it looks like I want to use a MAME 0.78 romset and the mame2003 emulator.  (This is due to RetroPie using the libretro emulation engine as it's primary emulator).  So I downloaded another 50GB from the Internet Archive and I’ll try out those ROMs to see if the buttons map correctly on the knockoff PS3 controller I’m using for testing.  It’s interesting that the joystick buttons are different based on what emulator I’m using.

I did briefly consider not using the Raspberry Pi 3B+ for the arcade cabinet and switching to a PC.  Reading some forums and Reddit posts, a PC is always recommended for MAME.  All I really want to do is play classic 80s arcade games that should mostly work with the Raspberry Pi.  A PC is mostly tempting to add the Dolphin emulator so I can play Super Mario Strikers for the Nintendo Gamecube, but I don’t know if that’s worth the expense or the trouble.  The Pi should more than handle the classic arcade games, Sega Genesis and Nintendo games I want to play.

But doing all the research is fun!
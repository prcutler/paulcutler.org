+++
# Date this page was created.
date = "2023-03-24"

# Project title.
title = "CircuitPython Denon Remote Control Speaker Stand"

# Project summary to display on homepage.
summary = "Control your Denon receiver using CircuitPython and an ESP32-S2 Reverse TFT Feather."

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = ""

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["CircuitPython", "Python", "Denon"]

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = false

# Optional featured image (relative to `static/img/` folder).
[header]
image = "project/denon-remote-control/remote-speakerstand.jpeg"
caption = "Denon AVR CircuitPython remote control speaker stand"

+++

##  Project Overview

The 'circuitpython-denon-remote-control' project is written in CircuitPython to control a Denon audio-video receiver wirelessly.  The hardware is then embedded in a 3D printed speaker stand, which is built for AudioEngine P4 and A5 speakers.

View the [source code on GitHub](https://github.com/prcutler/circuitpython-denon-remote-control) which also includes the 3D printer design files.

## About

I originally wrote a [similar app called pi-dial](https://github.com/prcutler/pi-dial) using the [denonavr](https://github.com/ol-iver/denonavr) Python library and a Raspberry Pi in a 3D printed case to control my Denon receiver's Zone 2.  After creating the [speakerstand-lights](https://github.com/prcutler/speakerstand-lights) project that embedded a Feather and Featherwing in a speakerstand, I still had one speaker stand left without anything in it.  When Adafruit released the[ESP32-S2 Reverse TFT Feather](https://www.adafruit.com/product/5345) inspiration struck as it was perfect for my needs.

### Parts Needed

* [Adafruit ESP32-S2 (or S3) Reverse TFT Feather](https://www.adafruit.com/product/5345)
* [Adafruit Stemma QT Rotary Encoder Breakout](https://www.adafruit.com/product/4991) and [rotary encoder](https://www.adafruit.com/product/377)
* StemmaQT cable
* USB-C cable with an optional right angle connector for mounting in a speaker stand
* 3D Printer - optional, but you probably want some way to mount the Feather

### CircuitPython Code

The code is hardwired to Zone 2, but could easily work with your main zone.  When possible, I tried to use the serial commands over telnet and not the XML post requests.  If you're controlling Zone 1, you can query the volume directly over serial instead of XML, which can sometimes time out.

I used the three buttons on the front of the Reverse TFT Feather to control my AUX1, Tuner, and CD inputs.  The `if` statement changes the display name as I use the CD input for my phono pre-amp so I renamed it "Vinyl" and AUX1 I use for "CD".

The rotary encoder changes the volume up and down and the button mutes and unmutes the receiver as well as displaying a white screen with big letters saying "MUTED" to remind me to unmute it.

### 3D Printing New Speaker Stands

I re-used my speakerstand design from the `speakerstand-lights` project using OnShape.  I don't have any experience with CAD and it shows, especially where the cables lay inside.  I hope to re-design this properly some time in the future.  Included are all the files you would need, including a normal speaker stand with rounded edges and an angled version.  The embedded version includes an STL file, STEP, and 3MF.

You will need to print the Reverse TFT front plate from BlitzCityDIY's [Octoprint enclosure](https://www.printables.com/model/392357-circuitpython-octoprint-controller-and-monitor-cas) project and attach it using 2 M2 and 2 M2.5 screws.


### Credits

* This project couldn't have been completed without the [`denonavr` Python library](https://github.com/ol-iver/denonavr).  Everything I needed was well documented for the XML queries. Denon's serial control protocol is well documented, though there are far fewer Zone2 commands.
* BlitzcityDIY for her [Octoprint enclosure](https://www.printables.com/model/392357-circuitpython-octoprint-controller-and-monitor-cas) which also featured a square faceplate for the ESP32-S2 Reverse TFT Feather.
* Neradoc for porting [ElementTree](https://github.com/Neradoc/Circuitpython-ElementTree) to CircuitPython for parsing XML.

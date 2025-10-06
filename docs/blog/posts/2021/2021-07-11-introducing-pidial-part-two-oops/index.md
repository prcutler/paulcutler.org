---
title: Introducing pi-dial - Part Two - Oops
author: Paul Cutler 
type: post 
date: 2021-07-11T13:00:00
categories:
  - Python
  - Hardware
tags:
  - Python
  - CircuitPython
  - Raspberry Pi
  - denonavr
  - pi-dial

---
Previously: [Introducing pi-dial Part 1](https://paulcutler.org/posts/2021/07/introducing-pi-dial-part-one/)

During this year’s PyCon, I completed two exercises in the Microsoft booth virtually.  A week later I was rewarded with two $50 gift certificates to Adafruit!  (Thanks Microsoft!)
 
Using the gift certificates, I bought a soldering iron and the parts I needed to make the [CircuitPython Media Dial](https://learn.adafruit.com/media-dial).  But I’m impatient, and while I was waiting for those to ship I thought I’d try and build a prototype in CircuitPython using a [Circuit Playground Express](https://learn.adafruit.com/adafruit-circuit-playground-express/overview) (aka CPX) I already had.

I ran into a couple errors trying to get one of the libraries in the [CircuitPython Bundle](https://github.com/adafruit/Adafruit_CircuitPython_Bundle) to load on the CPX.  I’ve already been lurking in the [Adafruit Discord channel](http://adafru.it/discord) which is a very friend community and I decided to ask for help.    After fixing my library issue and talking about my goals for the project, a kind person pointed out a problem that I hadn’t thought of:

*There is no network connection on the Circuit Playground Express **or** the Trinket I purchased that powers the Media Dial.*

Oops.

I take network connectivity via wireless or wired for granted on all my devices.  It just never occurred to me that the microcontrollers don't have network access unless you physically add it.

I started to think about how I could get around it and researched how I could fix this.  Two ideas jumped out at me:  

1. Add a wifi co-processor, using a second circuit board that is soldered to the [Trinket M0 microcontroller](https://www.adafruit.com/product/3500) that I already purchased for the project.
2. The Media Dial project as created sees the dial as a USB device and the dial rotations as a keypress.  I could write a Python application that runs on the Mac I’ll plug the dial into to listen for a certain keypress from the Trinket M0 and then send the commands to the receiver from this new Python program.

I quickly abandoned #1.  I have no idea how to modify or create designs for a 3D printer and all the wifi co-processors were much bigger than the Trinket M0.  I’m not going to figure out how to cram those together.

The second option was intriguing.  On the plus side, by running a Python program on macOS, I get access to the `denonavr` library making interacting with my receiver a breeze.  But the more I thought about it, the more I questioned the solution.  The way it would work:

* The Media Dial is seen on macOS as a USB device.  This shouldn’t be too hard, the [code is available in the guide on Adafruit](https://learn.adafruit.com/media-dial/code).  (“This shouldn’t be too hard” - famous last words.)
* If each turn of the rotary encoder is a key press (that can be programmed using CircuitPython in the code linked above), my Python application listens for that keypress and then sends an API call to my receiver.  
	* When turning the rotary encoder, is each step a keypress?
	* How quickly does each step turn and does it turn the volume up or down too quickly?
	* How much lag is there between turning the rotary encoder, the CircuitPython program interpreting that, and then sending it to the Python program on my Mac, which sends the API command over the network to the receiver.
	
I looked into which keys presses are reserved in macOS for shortcuts and programs, looking for a keypress that doesn’t conflict with anything else.  I only need 3:  volume up, volume down, and a button that turns mute on or off depending on its state.  

The other concern I thought of was having to start the Python application every time I reboot my MacBook.  Coding two different apps seems like a lot of work and I started to think about it differently.  What if I used a Raspberry Pi instead?  Yes, it’s a lot bigger and bulkier, but I only have to write one application and I can wire the buttons directly to the GPIO buttons on the Pi.  The tradeoff of a bigger physical device instead of a dial seems worth it compared to the above.  Besides, this is more of a learning exercise.  I'll consider this a prototype to see how I do in adding a rotary encoder to a Raspberry Pi.

So that’s what I’m doing.  More on that in the next blog post.

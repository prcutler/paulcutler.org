---
title: Introducing Silver Saucer
author: Paul Cutler
type: post
date: 2020-07-15T09:00:00
categories:
  - Python
tags:
  - Pyramid
  - Python
  - API
  - Discogs
  - pytest
  - Silver Saucer
  - Bootstrap

---
# Introducing Silver Saucer
I’ve started my next Python project:  Silver Saucer, which will be hosted at silversaucer.com.  I originally bought the domain about ten years ago when I was thinking of going into business for myself, which never happened and I hung onto the domain name because I liked it.  It was inspired by Neil Gaiman’s poem, *The Day The Saucers Came*, which I also have a framed art print of:

{{< figure src="day-the-saucers-came.jpg" title="The Day the Saucers Came" link="day-the-saucers-came-original.jpeg" >}}

Once upon a time, I was also a big fan of *The X-Files*, so it seems fitting.

With the pandemic here, I’ve had a little time to work on some long dormant projects, this being one of them.  I’m stuck on another Python project (more because of the hardware than the coding), so I thought I’d find some time to work on this.

I have a few different goals of things I want to learn and practice:

## Pyramid

It’s my third project using the [Pyramid web framework](https://www.trypyramid.com).  I don’t have an urge to learn Flask or another framework - I would like to get better at Pyramid, which I know a little.  I also really like the Pyramid community.  The few times I’ve become stuck and asked for help in the Pyramid IRC channel, they’ve been both welcoming and helpful.  My first two Pyramid projects were based on the first training Talk Python offered for Pyramid, which used a package called `pyramid_handlers` which is no longer the recommend way to build a web app in Pyramid.  I’m doing it the recommended way this time, using a class based approach.

## Bootstrap and CSS
I know a little of HTML, enough to get by.  But CSS and Bootstrap, not so much.  I’ve already integrated a Bootstrap theme and tweaked it where it’s almost working, but I’m just hacking at it - I don’t really know what I’m doing and it’s something I want to get better at.  I should probably find some good HTML / CSS tutorials and go through those.

## Discogs API Integration
The goal for Silversaucer.com is to integrate with the [Discogs API](https://www.discogs.com/developers/)).  Discogs.com is a website that lets you catalog your record collection and also includes community features and a marketplace where you can buy and sell records (or CDs or almost any kind of media).  There are two things I want to build using the Discogs API:

### Play a random record
I know that Discogs already has a feature on their website where you can have it randomly choose an item in your collection and if you shake the mobile app it will also show you a random item in your collection.  I want to take that to the next level and sort by type (record, 45, CD, etc.).

### On this day
The second things I want to build is a page that shows all records released for today’s date.  This one is going to be more complicated and I’ll share more in a separate blog post.

## Testing
I’ve blogged about it before, but I struggle to learn `pytest`.  I’m going to continue to try and learn more about software testing, starting with this app.

## Infrastructure
I’ve already hooked up Silver Saucer to Azure Pipelines to automatically do continuous integration.  I want to integrate `pytest` and code coverage next.  After that I may look into continuous delivery, but there’s is a lot about Azure that I don’t know. 

Plenty of things to learn and keep me busy during these interesting times.

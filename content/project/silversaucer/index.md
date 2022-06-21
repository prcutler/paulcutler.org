+++
# Date this page was created.
date = "2020-07-15"

# Project title.
title = "Silver Saucer"

# Project summary to display on homepage.
summary = "A web application built with the [FastAPI web framework](https://fastapi.tiangolo.com/) in Python that interfaces with the [Discogs API](https://www.discogs.com) to interact with my music collection."

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = "project/silversaucer/silversaucer-final.png"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Silver Saucer", "Python", "pyramid", "fastapi", "discogs"]

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = false

# Optional featured image (relative to `static/img/` folder).
[header]
image = "project/silversaucer/silversaucer-final.png"
caption = "Silver Saucer"

+++

{{< figure src="silversaucer-final.png" title="Silver Saucer Screenshot" link="silversaucer-final.png" >}}

### Project Status: Completed

# Summary

Silver Saucer is a domain I registered many years ago and kept because I like the name.  The logo is inspired from both a poem by Neil Gaiman, *The Day the Saucers Came* and *The X-Files*.

The best way to continue to learn Python is to build and make projects.  This project was a learning exercise to integrate my record collection with the Discogs API to display different data about albums in my collection.

You can view my [blog posts about Silver Saucer and my progress here](https://paulcutler.org/tags/silver-saucer/).

## Feature Goals

SilverSaucer has three main pieces of functionality:
* Build a website that integrates with the Discogs API to display information about an album, either chosen at random or picked specifically.
* Integrate with an Adafruit PyPortal and using CircuitPython, display the album art on the PyPortal.
* Build an "On this Day" feature to display albums released on a specific day.  This required a number of steps to integrate the MusicBrainz data into the app.

## Development goals

### Switch web frameworks

After starting with Pyramid, I switched to FastAPI halfway through the project.  I'm glad I made the switch, as it helped me understand views and HTTP methods better, as well as learning the new community framework favorite.


### Discogs API Integration
The goal for Silversaucer.com is to integrate with the [Discogs API](https://www.discogs.com/developers/)).  Discogs.com is a website that lets you catalog your record collection and also includes community features and a marketplace where you can buy and sell records (or CDs or almost any kind of media).  There are two things I want to build using the Discogs API:

### Play a random record
I know that Discogs already has a feature on their website where you can have it randomly choose an item in your collection and if you shake the mobile app it will also show you a random item in your collection.  This is a learning project and random records will be displayed for both albums and singles / EPs.

### Adafruit PyPortal
When an album is picked or randomly chosen, if I'm the logged in user, the album art will be displayed on the PyPortal.  The image URL saves the picture with Pillow converting it for the PyPortal.  A message is sent via MQTT, which the PyPortal is monitoring, and the new image loads after the web page loads.  I used CircuitPython on the PyPortal to monitor MQTT and download and display the image.

### On this day
Lastly, I want to capture and display the release date for each record in my collection.  It turns out Discogs only reliably stores the year, but MusicBrainz will usually have the date.  Using the `discodos` tool, I was able to get MusicBrainz IDs for about half my collection and entered the other half manually.  The web app then calls the MusicBrainz API to get the release date and stores that in the database for each record.  The "On this day" feature then shows a list of all records released for the current calendar date.






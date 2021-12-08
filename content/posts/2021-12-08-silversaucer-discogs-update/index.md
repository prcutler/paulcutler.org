---
title: Silver Saucer Discogs Integration
author: Paul Cutler 
type: post 
date: 2021-12-08T11:00:00
categories:
  - Python
tags:
  - silversaucer
  - silver-saucer
  - Python
  - FastAPI
   - Discogs

---

The progress continues in moving Silver Saucer to FastAPI.  I've spent almost all of my free time learning FastAPI from the Talk Python course.  It would probably have gone faster if I was directly following the training course, but of course I'm doing my own thing.

I'm trying to do two things at the same time.  First, build this in FastAPI, but use my own content, including CSS, page structure, and integrating the Discogs API instead of using a database.  Second, I'm re-using some code (mostly the services that call the Discogs API) from the old Silver Saucer Pyramid site.  I haven't touched that code in almost a year (for shame!) so I have to review that as I go.

Yesterday was a good day as I was able to wire up the Discogs integration using 90% of that old services code.  It turns out when I create the class to manage the call, it's pretty specific as the first time I got it to work, I thought I was pulling in the record title, but instead it was the image URL, which I quickly converted to an image since I had something working:

![Discogs returning an album image of Liz Phair's Exile in Guyville](exile.png#center)

From there, I was quickly able to call the rest of the data I wanted from the API and display it on the page.  My memory of how the release date works must be off or requires more research.  I thought I could pull both the release date of the specific album.  For example, if it's re-issued like Garbage's BeautifulGarbage was last month, it would show a November 2021 date.  But there was a main release date that should show 2001, but I can't seem to find it in the API.  Oh well.

I was also able to update the HTML for the `Genres` and display that better than I did on the last site, parsing the list and showing it as sub-bullets.  Another obligatory screenshot of everything working when clicking a random album:

![Discogs returning an album image of Japandroids last album](japandroids.png#center)


I need to start coding the 7" / EP random function and then start on manually choosing a record.  I have a couple questions on the training and thankfully Talk Python offers office hours, which are today!

Lots to do and I'm having fun doing it.
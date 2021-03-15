---
title: Silver Saucer Update - March 2021
author: Paul Cutler 
type: post 
date: 2021-03-15T12:30:00 
comments: true
categories:
  - Python
tags:
  - Python
  - FastAPI
  - Silver Saucer

---
Following up on my last blog post, I did deploy Silver Saucer a couple days later. I spent a day trying to track down
why MLBPool2 kept loading when I visited silversaucer.com and it turns out that the nginx web server defaults to the
application with the lowest port number. I had made a mistake in the nginx configuration in one little place that took
me forever to figure out. And with that, Silver Saucer is live on the web.

It still has a nasty viewport problem and the screen height is not 100% and it’s driving me crazy. Maybe if I had
finished my Coursera class on HTML, CSS and Javascript I would have figured it out…

A bad habit that I have is when I get stuck, I move on to a different project. I’m hoping that my subconscious will fix
it, but it’s more out of frustration. So what did I do? I bought more training courses from Talk Python and decided to
learn the [https://fastapi.tiangolo.com/](https://fastapi.tiangolo.com/) web framework instead. I was surprised to see
such a new
project [https://www.jetbrains.com/lp/python-developers-survey-2020/](https://www.jetbrains.com/lp/python-developers-survey-2020/)
in the recent PSF survey, especially as it was the first time being included as a question.

I decided to build my site along with the training, rather than the PyPI clone the training has you do. After sorting
through a couple of different bugs, guess what? I still need to learn CSS.

I’ve switched courses, moving from Coursera to Pluralsight, and am taking a new class to learn HTML & CSS. I’ll get
there one of these days.




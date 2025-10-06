---
title: The python3-discogs Library
author: Paul Cutler 
type: post 
date: 2021-12-13T11:00:00
categories:
  - Python
tags:
  - silversaucer
  - silver-saucer
  - Python
   - Discogs
   - open-source
   - docs

---

In June 2020 [Discogs](https://discogs.com) announced they were going to discontinue support for the Python library they maintained.  Shortly after, a few members of the community picked up where Discogs left off and [announced a community version](https://www.discogs.com/forum/thread/822690) of the library.

I remember Discogs’ announcement but I forgot about the community.  I had [starred their repository](https://github.com/joalla/discogs_client) at some point but randomly came across it again late last week. 

I started to refactor my project on Friday to use the API to see if it would be easier than using `requests` to parse all the JSON.  And it was.  In one method I think I went from about 40 lines of code to 5.  Yay APIs!

I didn’t understand the API thoroughly and got stuck on a few parts.  The documentation is pretty good and has examples using the Python REPL but I still had a couple problems trying to put it together.

It turns out that the community members are very responsive and helpful to questions.  I quickly received some pointers and help on the right way to do things and by the end of the weekend I not only had re-written the code to get a random album, but it was trivial to use the same code to get a random EP or single.  In fact, I bet my code is way more Pythonic now as I’m only using one method for both.

This is another example of the beauty of open source.  One group discontinues support but another is able to pick it up and keep it going.  

With all the help I received, I wrote up a lot of the functions to use the API that would appear in a Python program and [started a discussion and submitted a pull request](https://github.com/joalla/discogs_client/discussions/67)to update the documentation.  The community has been welcoming and it’s the least I can do to give back.  


---
title: Silver Saucer Random Play Progress
author: Paul Cutler 
type: post 
date: 2020-12-18T08:00:00 
categories:
  - Python
tags:
  - Silver Saucer
  - Python
  - Pyramid
  - Discogs
  - API

---

I’ve made some good progress over the last few days on being able to pick an album at random out of a given folder and
get information about it.

All of the work has focused on the back-end. Once I know I’m getting the right data out of Discogs, I’ll hook up the
front-end to display it, but for now, this has been a little more complex than I expected.  (It always is, isn’t it?)

One thing that’s jumped out at me was I don’t understand how people do TDD (Test Driven Development). The amount of
trial and error I do, even on “simple” things like building the right URL for the API call is ridiculous. I know it’s
because I’m a novice at Python and I don’t do this for a living all day every day, but I have a lot of respect for those
that do TDD. One of my original goals was to do this in TDD, but I have my excuses.

You can tell I’m a novice by how procedural my code is. Do this, then do that. It was working well in a very procedural
manner, so yesterday I refactored it all. Yup, I ripped it up and started over. Well, not from scratch. I could
visualize in my head how to make the code more Pythonic and I was able to re-use some of the code, but most of it was
refactored in
the [play_service](https://github.com/prcutler/silversaucer/blob/main/silversaucer/services/play_service.py). A good
example is going back to the folder example. I had hard coded each folder ID and each folder had it’s own method to get
a random album release ID and its data.

I’ve been able to take the folder selected by the user (LP, EP or single) and just pass variable that to the method
in `play_service.py`. This allowed me to use the same method to get the release ID information and the method doesn’t
care if it’s a single or full album.

I still need to fix the loop I’m iterating through in the JSON, but I’m really close. This is one of the downsides to
being a hobbyist - so much I don’t remember, including basic things, like how to iterate through a dictionary.

Practice makes perfect and I needs lots of practice. I told myself I need to think of some more projects to work on, but
one project at a time. In the meantime, I should sign up for something
like [Python Morsels](https://www.pythonmorsels.com/) and keep up with it.

This weekend I’m hoping to fix looping over the list in the dictionary and also fix API call that deals with the pagination of results from Discogs.  You can see what a mess it is in the `play_service.py` file and I know there has to be a better way to programmatically determine the pagination than a long `if / else` statement.  (And if I ever get over a 1000 records it will break!  Or my wife will break me when I have that many…)
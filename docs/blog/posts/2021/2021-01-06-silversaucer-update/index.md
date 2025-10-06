---
title: Silver Saucer Update
author: Paul Cutler 
type: post 
date: 2021-01-06T16:00:00 
comments: true
categories:
  - Python
tags:
  - Silver Saucer
  - Python
  - Pyramid
  - Discogs

---
Now that I have the ability to pick a random record to play using the Discogs API, I’ve completed one of the two big
features.

I’m now debating what to do next. I have a few options, all still focused on the random album feature.  (I may have to
cancel the “On This Day” future, but that’s a different discussion for a different time).

## Learn CSS

I need to learn CSS as the theme I’m using needs to be updated. The text colors in the theme are too dark and I had to
use a hack to show the text in white. This also means that the link colors are also appearing as white and you can’t
tell that they are links. In the past I’ve been able to get away with just poking at a CSS file to get done what I want,
but I really should take the time to learn it. The CSS file for Silver Saucer is huge and there are parts of it when I
look at it that I have no idea what it does.

## Bootstrap

I *think* I need to learn CSS before I tackle Bootstrap. Right now when the album results are returned, everything is
centered on the page. I played around with trying to justify it left and right and it doesn’t work at all visually. I
need to create a Bootstrap container to put the text in so I can justify it correctly.

## Release Date

The **Release Date** returned is when that particular version of an album was released. If it’s a re-release or
repressing, that date can be very different from when the album was originally released. I think I can use the master
release number to go get a list of all releases and then look at the first release in that list to get the “real”
release date. It doesn’t always work in some random testing I did, but it’s a start. My idea to look at the Musicbrainz
API doesn’t look like it’s any better. The other challenge with this feature is working with `datetime` objects, which
can be frustrating. Especially considering Discogs might return the release date in multiple different formats,
including just the month, month and year, or date / month / year. That will be fun to standardize.

## Miscellaneous

I also need to fix the data returned in **Genre**. It’s a list that I currently show as a list of bullets, each on its
own line. It doesn’t look quite right and I need to probably update the CSS or when iterating over the list, put it on
one line. I haven’t quite figured out what to do with it yet.

I also, in theory, could deploy what I have now. But I think I'll wait just a bit.

## Next Steps

I’m leaning towards tackling CSS first. I've started the Responsive Web Design class on [Free Code Camp](https://www.freecodecamp.org/), and it's good content, but the way they have you practice I don't feel as if the information is
sticking in my head. I’ve also signed up for a free  (to audit) [five week course on Coursera](https://www.coursera.org/learn/html-css-javascript-for-web-developers) to learn
HTML, CSS, and Javascript. Part of me really wants to learn just a little Javascript, but most of me doesn’t - I’d
rather focus on getting better at Python as I don’t feel like I’m anywhere close from transition from novice Python to
intermediate Python. But if I’m going to continue to focus on using Python for web development, which is where my
passion seems to lie at the moment, I need to get better at HTML and CSS. The structure of an actual class is helpful,
so I’ll probably move forward with the Coursera class for the time being.
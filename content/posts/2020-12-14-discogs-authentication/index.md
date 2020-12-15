---
title: Discogs Authentication
author: Paul Cutler 
type: post 
date: 2020-12-15T13:00:00 
categories:
  - Python
tags:
  - Silver Saucer
  - Python
  - Pyramid
  - Discogs
  - API

---

I was ready this morning to write a new blog post chronicling all the problems I had yesterday trying to authenticate
against the Discogs API. After finding the motivation to sit down and code for a few hours, I ended the day with almost
nothing done. I could access the parts of my collection that were public, but the parts that required authentication I
couldn’t figure out.

I sat down with my copy of coffee this morning, re-read
the [Discogs API authentication documentation](https://www.discogs.com/developers/#page:authentication), and voila!  It
just clicked. Sometimes you just need a good night’s sleep.

You have two options for authentication when building an app with the Discogs API:  full Oauth that allows users to
login and validate their login, or pass a user token as part of the API query. Since my app is just going to use *my*
Discogs information, the user token is perfect. Both authentication options give you options for a higher rate limit and
the ability to return an image - and this last one will be important later.

I thought I would tackle what would be the easiest part first - have the app pick a random album for me to play.

It was a lot harder than I expected, but I’ve made good progress.

Now that I could get back details of my collection via authentication, I had Discogs return a list of all the folders
I’ve organized my music into. I put each of the following into its own folder, as when I hit the random button, I don’t
want it to pick a 45 or 7” record with only two songs on it. I have 10 folders, with 0 and 9 included by default:

* 0 - all
* 1 - 10” (10” records, mostly EPs)
* 2 - 12” (12” singles or EPs)
* 3 - 7” (7” or 45 rpm singles)
* 4 - Autographed (currently empty, but you can have a release in more than one folder)
* 5 - Cassette
* 6 - CD
* 7 - Digital
* 8 - LP
* 9 - Uncategorized

The JSON returned looks like this:

```
{
    "folders": [
        {
            "id": 0,
            "name": "All",
            "count": 799,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/0"
        },
        {
            "id": 2162486,
            "name": "10\"",
            "count": 19,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162486"
        },
        {
            "id": 2198941,
            "name": "12\"",
            "count": 30,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2198941"
        },
        {
            "id": 2162483,
            "name": "7\"",
            "count": 76,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162483"
        },
        {
            "id": 2162485,
            "name": "Autographed",
            "count": 0,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162485"
        },
        {
            "id": 2162487,
            "name": "Cassette",
            "count": 1,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162487"
        },
        {
            "id": 2162488,
            "name": "CD",
            "count": 6,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162488"
        },
        {
            "id": 2198943,
            "name": "Digital",
            "count": 1,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2198943"
        },
        {
            "id": 2162484,
            "name": "LP",
            "count": 666,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/2162484"
        },
        {
            "id": 1,
            "name": "Uncategorized",
            "count": 0,
            "resource_url": "https://api.discogs.com/users/prcutler/collection/folders/1"
        }
    ]
}
```

I then got stuck for a while before I realized I should be using the folder IDs in the `resource_url` and not the JSON
number of 0-9.

That - plus authentication - are challenges for someone like me still learning. But progress is being made. Lots of
trial and error with string concatenation to get the URLs and tokens right. The next thing to solve for:  Discogs only
returns 100 items in a list, making you interact with pagination to go deeper. I’ll need to do this to take the random
number generated of while album to play to get its data, including the image to show, when a random album is chosen. 
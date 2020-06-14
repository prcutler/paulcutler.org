---
title: NFLPool 2017 Recap
author: Paul Cutler
type: post
date: 2018-01-29T13:58:33+00:00
url: /blog/2018/01/nflpool-2017-recap/
categories:
  - Python
tags:
  - MLBPool
  - NFLPool
  - Python

---
The NFLPool 2017 season wrapped up a month ago. The application performed admirably. Every week I logged in, downloaded the weekly statistics from [MySportsFeeds][1], and the scoring calculations updated and posted on the standings page. I emailed the players every other week with the update and link to the [standings][2] (and the reminder that the team standings points would not be final until the end of the season due to MySportsFeeds shows division standings doesn’t account for the correct tiebreakers). Everything looked good and it was working as expected.

Or so we thought.

After week 17 was complete, I ran the update again and sent out the preliminary results. I worked with Brad at MySportsFeeds to update the division standings feed to rank the teams correctly according to the NFL’s tiebreakers. Then, one player caught that some of his individual leaders weren’t assigning points correctly. Digging in, I saw that in my picks, some of my players weren’t having their points assigned either.

I was so focused on the team standings and not individual player standings that there was a bug in the code. Week 1 worked correctly, but weeks 2-17 did not calculate the individual player performance correctly &#8211; and none of us caught it! Kelly was able to [fix the SQL query][3] she wrote and voila, everything worked! The only catch was that a week had gone by and the way that I programmed the [standings page][4] to display the title it now says “Week 18” instead of “Week 17”.

I’m pretty proud of myself for creating my first Python application (even if I didn’t write the SQL queries that do the scoring calculations). Everything worked great and I’ve learned so much about Python (and still have so much to learn). I have a list of things to improve and enhance for the 2018 season. In no particular order:

  * Update / fix the `datetime` function when a user submits their picks. One player got locked out too soon.
  * The traversal to the standings is `www.nflpool.xyz/standings` &#8211; this shows the current standings. This needs to add a year, to both allow players to see a previous season’s history &#8211; such as `www.nflpool.xyz/standings/2017` &#8211; I’ll probably need to add a template page for standings then to list out all the available years as well as figure out what I want to do in the navigation.
  * Write a function that if the week is 17, call it final on the template page’s header.
  * Figure out how curl can call the get request to update the stats &#8211; it has to use my login to access the admin panel’s URL to call the get request and I don’t know how to do that in curl.
  * Lots of other enhancement plans, such as porting the app from SQLite to MySQL, but the above list are the big ones. I’m trying to make sure I capture any [bugs or enhancements on Github][5].

Speaking of MySQL, NFLPool was always intended to do two things:
  
1. Automate our NFLPool league
  
2. Serve as a testbed for MLBPool2

I’m happy to say that [MLBPool2 is now under active development][6]. I have exactly 8 weeks from today before the Major League Baseball season kicks off, so I have about 6 weeks to get it working. And I’ve already been able to get it to work with MySQL! But MLBPoo2 development is a different blog post for later this week.

 [1]: https://mysportsfeeds.com
 [2]: https://nflpool.xyz/standings
 [3]: https://github.com/prcutler/nflpool/commit/9c6070569b3ebfaeb362cd6085b6e6029a8b0b45
 [4]: https://www.nflpool.xyz/standings
 [5]: https://github.com/prcutler/nflpool/issues
 [6]: https://github.com/prcutler/mlbpool2
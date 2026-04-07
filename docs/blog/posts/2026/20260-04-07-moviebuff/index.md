---
title: Moviebuff
author: Paul Cutler
type: post
date: 2026-04-07
categories:
  - movies
tags:
  - movies
---

Moviebuff is a Django application originally written by [retiolus](https://codeberg.org/retiolus/moviebuff) that was released last August. I’m not sure how I originally came across it, but I remember it being demonstrated on Mastodon. Moviebuff allows you to track and rate the movies you watch and share them on the Fediverse.

I already have a [music site](https://silversaucer.com) and I’ve been tracking [what I watch manually](https://www.paulcutler.org/blog/2026/04/01/what-im-watching---q1-2026/), so I was kind of excited for Moviebuff. I forked it right away, but there wasn’t any installation instructions and I’ve never used Django. I was able to reverse the first few things needed in the `.env` file, such as the Django secret key, an API key from [The Movie Database](https://www.themoviedb.org), but I couldn’t figure out how to get Federation working. The code to add Federation didn’t appear to be in the original repository or any of its branches.

So there it sat. I debated a few times about opening an issue in the Moviebuff repository asking for help, but I didn’t want to bug the maintainer and I was just grateful that anything had been shared and open sourced.

After successfully using Claude Code to help create the [circuitpython-bambulabs](https://github.com/prcutler/CircuitPython_bambulabs/) library, I pointed Claude at Moviebuff and away it went. It surprised me again when it was able to add Federation to the project based on the scaffolding that was already there, no database changes needed.

I’ve done a few projects in Pyramid and FastAPI, so Python based web frameworks weren’t totally new to me. Partnered with Claude, I went to work.

Things I’ve updated and changed:

- Added dark mode and made it the default with a toggle to change light or dark mode on the home page
- Added working Federation based on the buiding blocks present in the app
- Changed Federation to only post when a movie is rated. Also added a Share to Fediverse button using HTMX that appears when a movie is added to the Watched Movies list
- Added an environment variable and code to enable or disable registration (to avoid spammers)
- Disabled the registration pages if the user is unauthenticated and registration is disabled
- Updated the home page to show a legend, the five most recent movies rated, movie posters for the four most recent movies rated, and HTMX to page through the rated movies
- In the Dashboard, added HTMX to page through all the Watched Movies
- In each movie card, added the star ratings for the movie
- Updated the datetime fields to be MON/DAY/YEAR and added commas to the movie's budget
- Added a Font Awesome film icon in the upper left and made it and Moviebuff clickable to return to the home page
- Added a custom footer that matches [silversaucer.com](~https://silversaucer.com~)
- Added a CONTRIBUTING.md and CODE_OF_CONDUCT.md
- Added installation instructions in the README

You can see it in action at [https://moviebuff.silversaucer.com](https://moviebuff.silversaucer.com). I’ve added most of the movies I watched in Feburary and March and I’m still debating about adding earlier movies.

The code [lives at Codeberg](https://codeberg.org/prcutler/moviebuff) and I’ve made a [synchronized mirror on GitHub](https://github.com/prcutler/moviebuff). If you like it, give it a star! And if you really want to know what I’ve watched, you can follow me on Mastodon at `@prcutler@moviebuff.silversaucer.com`.

I’m so grateful to retiolus for creating the app and releasing it under an open source license. I’m looking forward to rating, cataloging, and sharing the movies I watch.

![Moviebuff homepage screenshot](moviebuff.png)
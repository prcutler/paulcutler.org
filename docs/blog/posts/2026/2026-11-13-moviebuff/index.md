---
title: MovieBuff
author: Paul Cutler
type: post
date: 2026-11-13
categories:
  - movies
tags:
  - moviebuff
  - movies
  - tv
---

MovieBuff is a web application developed by [retiolus](https://retiolus.net)
that tracks all the movies and TV shows you watch. If you’ve used Letterboxd
or Trakt, you might be familiar with the concept.

retiolus [first released it on Codeberg](https://codeberg.org/retiolus/moviebuff)
late last year and I was immediately interested. I already use
[Discogs](https://www.discogs.com/user/prcutler/collection) to track my music
collection, [Listenbrainz](https://achordion.xyz/user/prcutler) for what I
listen to, and this was perfect for my watch history. After it hadn’t been
contributed to for a few months, I forked it and vibe coded my own version
of it (shame on me). I had been looking for a solution to do exactly that,
but didn’t want to use something like Letterbox or Trakt - why let them train
on my data? I had been posting on my blog what I watched every quarter for
2025 and early 2026 and this fit exactly what I was looking for. Best of all,
it was Federated - if you use Mastodon, you could easily follow me and see
what I was watching and what I rated.

I love how the [README](https://codeberg.org/retiolus/moviebuff/src/branch/main/README.md)
describes the project:

> * **A diary, not a database.** Every viewing is a dated entry, with an
  optional half-star grade and a review; watch it again and it is logged again.
> * **Films and series in one place**, seasons and episodes included,
  catalogued from TMDB. One search, one profile, one set of shelves.
> * **Cast and crew** on every title, and a page for each person with their
  filmography.
> * **Series without spoilers.** What people say past the episode you reached
  is folded until you open it.
> * **One search box** for titles, people, accounts on any server, hashtags
  and pasted links.
> * **Shelves worth browsing** — Watched, Watching, Watchlist — sorted and
  filtered by decade, genre, films or series.

And read the [README](https://codeberg.org/retiolus/moviebuff/src/branch/main/README.md)
for more.

About two months ago retiolus updated MovieBuff. Up until then it had only
worked with movies, but support for TV shows was then added, as well as a host
of new features. A few weeks ago I wiped my version of MovieBuff and
installed it from upstream.

The docs have excellent instructions for
[how to deploy](https://codeberg.org/retiolus/moviebuff/src/branch/main/docs/deployment.md)
a server. The docs say you need Debian 12 or Ubuntu 24.04, but I succesfully
installed it on Fedora 44 with only a few things needing to change, mainly
using Valkey instead of Redis and the PosgreSQL Python library needed a newer
version than what is in requirements.txt. Other than that, the installation
went flawlessly and I even updated to 0.1.1 without issues by following the
instructions in the docs.

There are a ton of features, including the ability to make it a progressive
web app on your phone or tablet and it feels like a real app on your mobile
device.

A big thank you to retiolus for creating MovieBuff. I’ve never self hosted a
federated app before and so far so good. If you’re on Mastodon and want to
follow me, I’m at @prcutler@moviebuff.silversaucer.com. My instance is
also open to sign-ups - if you’re interested in joining, you can
[register for an account](https://moviebuff.silversaucer.com/register/) and
join the server to track what you watch.

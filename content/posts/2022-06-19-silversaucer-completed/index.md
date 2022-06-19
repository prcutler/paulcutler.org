---
title: SilverSaucer completed!
author: Paul Cutler 
type: post 
date: 2022-06-19T11:45:00
categories:
  - python
tags:
  - circuitpython
  - python
  - fastapi
  - pyportal
  - hardware
  - silversaucer
  - fastapi

---
Just like that, I crossed the finish line and SilverSaucer.com is finished.  I wasn’t planning on finishing it so quick after my blog post, but on Friday it just clicked and the “On this day” feature was completed in just a few hours.

I always thought the “On this Day” feature was a pipe dream.  I had no idea how I was going to tie a Discogs release to MusicBrainz and then import that date.  But after discovering the discodos app a few weeks ago and working with the database having clicked last week, I was able to finish it up after discovering a key feature:  the LIKE operator in SQL and SQLAlchemy.  


today = pendulum.today(tz="America/Chicago")
print("Today: ", today, today.month, today.day)

if today.month < 10:
    search = "0" + str(today.month) + "-" + str(today.day)
else:
    search = str(today.month) + "-" + str(today.day)

async with db_session.create_async_session() as session:
    query = (
        select(Album)
        .filter(Album.mb_release_date.like(“%” + search))
        .order_by(Album.mb_release_date)
    )
    print(query)

    results = await session.execute(query)
    query_results = results.scalars()


The Pendulum library comes to the rescue again as it is still my favorite way to work with datetime objects.

This returns a list of rows from the database where the results are today’s date, not including the year.  (There is one bug related to 6/18 I can’t track down where it displays a different result - but not both - when an order_by is added to the query).

I’m pretty happy with how everything has turned out.  I’ll probably do a couple more blog posts about the project, including reviewing the project goals.

It feels weird to be done.  Not necessarily elation, not relief, just weird.
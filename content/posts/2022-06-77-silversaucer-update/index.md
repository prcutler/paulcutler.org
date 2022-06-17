---
title: June 2022 SilverSaucer Update
author: Paul Cutler 
type: post 
date: 2022-06-17T13:00:00
categories:
  - python
tags:
  - circuitpython
  - python
  - fastapi
  - pyportal
  - hardware
  - silversaucer

---
# Silver Saucer Progress (June 2022)
As usual, I haven’t blogged my progress on SilverSaucer and I’ve had some major progress [since January](https://paulcutler.org/posts/2022/01/silver-saucer-progress-january-2022/).  

First, I did follow-up on that blog post by switching from a MatrixPortal with a 64x64 LED to a PyPortal Titano.

![Liz Phair's self titled album displayed on a PyPortal](lizphair-pyportal.jpeg)

In FastAPI, I did two things.  I added a service that uses the  `Pillow`  library to convert the image from the Discogs image URL to a small bitmap that  the PyPortal can use.

The second thing is that sends a message using the MQTT protocol.  The PyPortal is watching for that message, and when received displays the Bitmap like above. 

```
async def get_discogs_image(release_image_url):
    image_dl = requests.get(release_image_url, stream=True).raw
    download = Image.open(image_dl)
    download.save('static/img/album-art/image_600.jpg')

    img = Image.open('static/img/album-art/image_600.jpg')
    img.quantize(colors=16, method=2)
    smol_img = img.resize((320, 320))
    convert = smol_img.convert(mode="P", palette=Image.WEB)
    convert.save('static/img/album-art/image_300.bmp')


async def publish_image(image_url):
    client = mqtt.Client()
    client.username_pw_set(config.mqtt_user, config.mqtt_pw)
    client.connect("mqtt.silversaucer.com", 1883)
    client.publish("albumart", "Ping!")
    client.disconnect()

```

That was a pretty big breakthrough to get hardware working with the website back in April or May.

I then spent early last week playing with a command-line tool called `discotools`.  I help with a little of the documentation in the `python3-discogs-client` library and one of the co-maintainers wrote `discodos` for DJs to catalog their collection.  It also has the ability to match Discogs Release ID to MusicBrainz ID and using it I was able to get about half (or 400) of my MusicBrainz IDs assigned into the database.  (Which is a different story about doing unnatural things with tables).

Then in the last week or so, everything has started to come together.  Last week I was struggling with understanding the different kind of objects database queries could return.  I was having a hard time understanding and differentiating between `scalar, scalars, one_or_none, and lists`.  That finally clicked and in a couple of days I had re-written the random results page to mostly use the database and the page load time went from about 10 seconds down to about 2 seconds, a huge improvement.  After the initial database import, which takes forever as Discogs rate limits you to one request per second, the `play-album` page uses the database for all information except the genres and tracklist, which are still called using the Discogs API.  It turns out that the Discogs API is very slow when querying an object in your personal collection. If you do a general query on a public release object, it’s way faster.  The combination of those two things led to the speed improvement.

From there I was able to quickly re-factor the play-single method to match the play-album, so I can randomly return an EP or single to play.  Understanding the database query, I also added a list result to the admin page showing a list of all releases that don’t have an associated MusicBrainz ID.  Last night in just hours I created the template with form and the get and post methods to manually enter the ID and store it in the database.  

I also wrote a method that for the existing database entries that have the MusicBrainz ID, to query the MusicBrainz API and get the release date for that album.  It worked, but the dates the API has stored include the year, year and month, and year, month and date, which is what I really want.  But just like that, over half the work to build the “On this Day” feature has been done and I just need to manipulate the dates above to get the one I want.

The finish line is in site.




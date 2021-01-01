---
title: Wiring Up Play Singles
author: Paul Cutler 
type: post 
date: 2021-01-01T14:30:00 
comments: true
categories:
  - Python
tags:
  - Silver Saucer
  - Python
  - Pyramid
  - Discogs
  - API

---
Earlier this year when I finished cataloging all my records in Discogs, I then put each one into a “folder”, a way for
Discogs to separate different kinds of records. It’s setup by the user, so I created a folder for each type of music I
have, and the number is the ID that Discogs assigned to each one:

```
all_folder = 0
lp_folder = 2162484
twelve_inch_folder = 2198941
ten_inch_folder = 2162486
seven_inch_folder = 2162483
cd_folder = 2162488
tape_folder = 2162487
digital_folder = 2198943
```

CD, Digital and Tape don’t currently have any items in them, but I hope to at least catalog my CD collection some day,
but that’s a different story.

In the music controller, the method to get an album’s information looks like this:

```
@view_config(route_name="play", renderer="silversaucer:templates/play/play.pt")
def play(_):

    album_release_id = RandomRecordService.get_folder_count(2162484)
    release_data = RandomRecordService.get_album_data(album_release_id)
    return {"release_info": release_data}

```

Here I’ve hard coded the folder ID (2162484) from Discogs in the method as I only want to use the folder that has only
full albums (no singles, 45s, etc.).

Now it’s time to wire up the code to play a single from one of three folders:
* 7” or 45 
* 10” EPs 
* 12” singles / remixes

It looks similar to the method above, but I’ve added a random method to pick one of the three folders for me and pass
the folder ID to the play service that I’ve already written for full albums:

```
def play_single(_):

    random_folder = randint(0, 2)
    if random_folder == 0:
        single = 2162483
    elif random_folder == 1:
        single = 2162486
    else:
        single = 2198941

    album_release_id = RandomRecordService.get_folder_count(single)
    print(album_release_id)
    release_data = RandomRecordService.get_album_data(album_release_id)
    print(release_data)

    return {"release_info": release_data}

```

This is where I appear to have outsmarted myself. I thought I had blogged about this, but apparently not. At one point I
had refactored the first play method above - I had added the play service to accept the folder ID and pass that. I was
pretty proud of myself because after the refactoring, I figured this would work for exactly what I’m trying to do now -
pass the folder ID of other folders. But no, it wasn’t meant to be as it errors out:

```
  File "/Users/prcutler/workspace/silversaucer/silversaucer/controllers/music_controller.py", line 35, in play_single
    release_data = RandomRecordService.get_album_data(album_release_id)
  File "/Users/prcutler/workspace/silversaucer/silversaucer/services/play_service.py", line 178, in get_album_data
    discogs_main_id = release_json["master_id"]
KeyError: 'master_id'
```

There is no `master_id` returned because singles don’t have a master release!  Only full albums have a master release to
track all the regional releases and special pressings.

I need to think through this and decide if I’m going to write a new method in `play_service` to handle getting back the
release information for the single or if I should write an `if` statement to account for the Key Error and return a
different dictionary without the `master_id`.

I was so proud of myself for doing something I thought was Pythonic, too!

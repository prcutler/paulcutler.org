---
title: Displaying the Album Information
author: Paul Cutler 
type: draft 
date: 2020-12-23T08:30:00 
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

In my [last blog post](https://paulcutler.org/posts/2020/12/iterating-through-the-folder-dictionary/), I was able to 
pass the folder to Discogs to get a list of albums, and then pick one at random and give me information back about 
the album picked.  That information was returned as a dictionary and now it is time to wire it up to the Chameleon 
template in Pyramid that will display the HTML.

Here's an example of the JSON:

```
{'release_title': 'Massey Fucking Hall', 'release_uri': 'https://www.discogs.com/Japandroids-Massey-Fucking-Hall/release/16118824', 'artist_name': 'Japandroids', 'artist_url': 'https://api.discogs.com/artists/1473872', 'release_date': '2020-06-26', 'discogs_main_id': 1829048, 'discogs_main_url': 'https://api.discogs.com/masters/1829048', 'main_release_date': 2020, 'release_image_uri': 'https://img.discogs.com/BVmRNi_A5_Vm8X0ntzUDh8figvE=/fit-in/300x300/filters:strip_icc():format(jpeg):mode_rgb():quality(90)/discogs-images/R-16118824-1604177632-7503.jpeg.jpg', 'genres': ['Rock']}
```
In the controller that handles the routing for the page I have:

```@view_config(route_name="play", renderer="silversaucer:templates/play/play.pt")
def play(_):

    album_release_id = RandomRecordService.get_folder_count(2162484)
    print(album_release_id)
    release_data = RandomRecordService.get_album_data(album_release_id)
    print(release_data)

    return {"release_info": release_data}
```



It was way easier than expected.  (And if you know me, you know that the random record picked above is perfect, as 
I'm a huge Japandroids fan.)  The first thing I did was connect the image URI that the Discogs API passes in the 
Chameleon template:

```<img class="mb-5" src="${release_info.release_image_uri}" alt="${release_info.release_title}" />
```

That worked, which was awesome.



Random thoughts and musings:
* Every time the page loads, it refreshes the API call.  So if you click a link to the artist page on Discogs, for 
  example, and then click the back button, that album data has been replaced.  Not sure how to work around that, 
  though I have some ideas.  Probably a good question in IRC with the Pyramid team.

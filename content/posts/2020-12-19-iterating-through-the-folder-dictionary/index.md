---
title: Iterating Through the Folder Dictionary
author: Paul Cutler 
type: post 
date: 2020-12-19T07:00:00 
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

After taking a break and coming back to it, I finally was able to iterate through the dictionary containing the folders
I’ve sorted my records in to on Discogs.

Dictionaries are a basic object in Python, but my struggles show that to be good - at anything - takes practice. And I
haven’t been practicing. Thank goodness for Stack Overflow!

I embedded all kinds of `print` statements trying to figure out how to play with the JSON from Discogs.

After lots of trial and error, Google searches and Stack Overflow searches, I’ve got it.

After making the API call to Discogs, we get the JSON back:

```
record_json = response.json()

json_data = record_json
json_folders = json_data[”folders”]
```

`json_folders` is a list, so we add the last line above. Now I had to make a `for` loop to iterate through that list -
which is a list of dictionaries.

The `if` statement looks to see if `folder` - which we passed from the controller when the user clicked which kind of
album they want a random answer to, matches the folder ID found in the JSON.

```
for get_folder_id in json_folders:
    print(json_folders)
    print(len(json_folders))

    if get_folder_id[”id”] == folder:

        lp_count = get_folder_id[”count”]
        print(”Folder passed = “, folder, ”LP Count is :”, lp_count)
        # folder_test = 2162484
        print(folder, lp_count)
```

Voila!  From there, I get a random number between one and the count found in the JSON. That number is then passed to the
pagination request to get the album ID.

Next up:  Either fix the pagination method to reduce the if / else statement or move on to getting the album release
information. I also need to remove a ton of print statements and clean up and remove all the methods I don’t have to use
after refactoring this. Progress!m hoping to fix looping over the list in the dictionary and also fix API call that
deals with the pagination of results from Discogs. You can see what a mess it is in the `play_service.py` file and I
know there has to be a better way to programmatically determine the pagination than a long `if / else` statement.  (And
if I ever get over a 1000 records it will break!  Or my wife will break me when I have that many…)
---
title: Preparing Silver Saucer for Deployment
author: Paul Cutler 
type: post 
date: 2021-03-93T12:30:00 
comments: true
categories:
  - Python
tags:
  - Python
  - Pyramid
  - Silver Saucer

---
Pyramid, my favorite Python web framework, was
released [version 2.0](https://docs.pylonsproject.org/projects/pyramid/en/2.0-branch/whatsnew-2.0.html) late Sunday. The
biggest change is dropping legacy Python support. I've been running the beta version of 2.0 the last couple of months
while developing Silver Saucer.

The Pyramid 2.0 release helped me change gears from my hardware project back to Silver Saucer. Under the mantra of
“release early, release often” I decided to start prepping to deploy Silver Saucer. I knew I had a few things to work on
still, especially the big “On This Day” feature I haven’t started.

Of course I didn’t save any notes from when I last deployed a Pyramid web app. I started to make a list of things I
needed to do on my DigitalOcean droplet and realized that Silver Saucer’s IP on my server wasn’t set up correctly which
was why I kept getting an SSL error. That was an easy fix when I remember [Dependabot](https://dependabot.com/) was
still broken on Github.

I had tried adding a pre-commit hook to use the `black` linter to my Github repository. It required me to create
a `pyproject.toml` file. But doing this caused Github’s Dependabot to think I was using Poetry to manage my Python
modules, when I’m not. I didn’t have any luck on the Github forums, so I just removed the file from now. Dependabot
started working again right away - spewing out over two dozen pull requests to go through. It took Azure Pipelines a
little while to catch up in testing out all the builds with the PRs, but only one or two failed and I still have one
more PR to test and / or fix.

With that done, I thought I’d fix just one or two little things. This led me down a path of refactoring the theme,
especially how the header works. I had the header image included in every page, and I was able to put it in just the
layout template.

I also have a weird CSS bug with the viewport where it’s not filling the website screen 100% vertically. I spent hours
on that but my CSS skills aren’t there yet, especially when using a complex CSS theme created by someone else.

I’m going to push Silver Saucer live in the next few days. The irony of creating a random Discogs player when
I [just started listening to my entire collection alphabetically](https://paulcutler.org/posts/2021/02/listening-to-my-record-collection-alphabetically/) is not lost on me. Release early, release often!
---
title: Password Validation in NFLPool and MLBPool2
author: Paul Cutler
type: post
date: 2018-04-27
categories:
  - Python
tags:
  - Python
  - NFLPool
  - MLBPool2

---
When I first learned to work with Pyramid thanks to the Talk Python course Python for Entrepreneurs, I used the account registration system directly from the course for NFLPool.  When I wrote MLBPool2, I augmented it to require the user to use a much stronger password than the course taught.  (You can see the original code from [NFLPool here](https://github.com/prcutler/nflpool/blob/master/nflpool/viewmodels/register_viewmodel.py)).

In MLBPool2, I required the user to use a password between 8 and 24 characters and it must have at least one lowercase letter, at least one upper case letter, a number, and a symbol:

A nice error message is shown each time the user doesn’t do it correctly.  I was pretty proud of myself for figuring this out (and for using Stack Overflow to get some tips on how to do it).

But…. It hit me a couple weeks ago that it works great for user registration, but if they lose their password or want to reset it, none of that functionality is there.  When resetting a password, the user clicks the reset password link which emails them a one-time link to reset their password.  And none of the password requirements I was so proud of are in the methods for resetting a password.  

It’s going to require a big re-write - right now it only has one input field for the new password.  I’ll need to add a second field to require the user to enter the new password twice (similar to registration) and then add all of the requirements and the error messages to the viewmodel. So I’ll be working on that over the next week or so.

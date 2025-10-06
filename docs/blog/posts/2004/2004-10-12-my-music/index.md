---
title: My Music
author: Paul Cutler
type: post
date: 2004-10-12T14:43:38+00:00
url: /blog/2004/10/my-music/
categories:
  - Entertainment
  - Linux
  - Microsoft
  - Music
  - Technology

---
So I have a lot of music. With over 700 CDs ripped, and some other misc. music, it&#8217;s quite a bear to manage it all.

For the last few years, I&#8217;ve used [Netjuke][1] on my Linux server. During the upgrade process this past spring, I put my music on two seperate hard drives, seperate from the third which holds the OS. What I love about Netjuke is that it&#8217;s database driven, making it very easy to search, and a nice web interface, that is semi-skinnable. It&#8217;s also GPL.

The downside is that Netjuke 2.0 has been in development for almost (or just over?) a year. Netjuke 1 was released in Aug. &#8217;03, and no updates since. Netjuke 2.0 development has been quiet for almost 6 months, with no updates, and the CVS is unusable. And there is talk that it will be propietary, not GPL, which doesn&#8217;t make me happy.

I&#8217;ve been looking at other projects, first [Andromeda][2], which is a PHP script that is not database driven. I had used Andromeda before Netjuke, and purchased it again this past spring when I had some installation problems with Netjuke 1.0, but still wasn&#8217;t happy with it.

On the Netjuke forums, I came across [Jinzora][3], which looks similar to Andromeda, but has more functionality through PHP scripting. Features include ID3 tagging, server side playback (which Netjuke can do kind of), file downloading, RSS feeds, and a slim version for adding via an iframe.

I still have some questions that the FAQ, Wiki and forums didn&#8217;t answer around multiple directories (I have my Ogg and MP3 files in seperate directories, but those directories have identical artists, but different albums).

I still have some work to do to finish cleaning up some ID3 tags, and getting some newer music on the site and syncing it all up, but this is another project to add to my list. I still have to figure out why the ID3 tags for some live Dave Mathews stuff isn&#8217;t working in Netjuke too.

In addition, I need to get a linux box up with a sufficiently big enough hard drive so I can rsync nightly or weekly to back it all up. My Mirra won&#8217;t back up a network drive, and I had mapped my music directories on my linux box over Samba to my extra Windows box hoping it would. Dammit.

Speaking of music, I need to find out how Windows serving works. A while back I received [Omnifi][4] for the car and my home receiver. While pretty cool to transfer my music to my car&#8217;s hard drive, the car version was way to sensitive and doesn&#8217;t work. I still have the set top box hooked up to my home theater, and that works streaming from my extra Windows box where I have some of my music duplicated from my server. The downside is that Omnifi uses software to manage your music collection called SimpleCenter. This is one of the worst designed music interfaces ever created. The one neat feature it has is &#8220;Watch Folders&#8221; where you point it towards your music folder, and it automatically notices when you add music to that folder and adds it to your collection. It does not support Ogg, but does support Rhapsody and some internet music stations.

I had purchased The Killers new CD, ripped it to MP3 (bleh) and put it on my Windows box. Firing up the Omnifi, lo and behold I see a Musicmatch server on it &#8211; sure enough, from my [Linksys boombox installation][5], Musicmatch has the identical ability that SimpleCenter, including watch folders, and what not. So I import all the music on that Windows box into MusicMatch, and can use that on my Omnifi. From managing my music on my PC, I prefer the MusicMatch interface &#8211; it&#8217;s not my favorite either, but it has some better features built-in including ID3 tagging, and the interface is cleaner to use, but it has too many advanced features to get you to buy crap.

So the questions becomes what is the SDK that they&#8217;re using &#8211; terminology is identical (Watch Folders, etc) and what would it take to get it ported to Linux. If I could have my whole collection on my server serving my house (with the exception of Ogg dammit, and I&#8217;m not re-encoding that stuff), I would be golden.

So much work, so little time.

 [1]: http://www.netjuke.org
 [2]: http://www.turnstyle.com/andromeda/home.asp
 [3]: http://www.jinzora.org/index.php
 [4]: http://www.omnifimedia.com/home/
 [5]: http://www.silwenae.net/blog/index.php?p=46
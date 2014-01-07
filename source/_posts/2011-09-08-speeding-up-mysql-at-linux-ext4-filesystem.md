---
layout: post
title: Speeding up MySQL at linux and ext4 filesystem 
published: true
categories: tips
comments: true
---
Since i switched back from Mac OS X to Linux, i noticed some of my rails apps were running its tests much slower (almost 10 times slower in few cases). 

After many wrong guesses and false alarms, i found out that MySQL doesnt like much ext4 ubuntu default settings. 

I hope it can help fellow googlers facing this very same issue. After adding some minor tweaks at my ext4 partition, my test suite now runs under 3 seconds. Before those changes, it used to last almost 80s!  

## TL ; DR 

Add __barrier=0__ to your fstab, restart your machine, and MySQL will run *much* faster. 

Mine fstab entry is currently like this, feel free to change that accordingly to your needs:

    # / was on /dev/sda6 during installation
    UUID=98e8b440-fd76-4e49-b45a-e8e3c9dec2e4 / ext4    errors=remount-ro,noatime,data=writeback,barrier=0,nobh 0 1


For more information regarding ext4 and those tweaks im using, check this *awesome* [blog post](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/) from [Nick Gauthier](http://www.ngauthier.com/) 

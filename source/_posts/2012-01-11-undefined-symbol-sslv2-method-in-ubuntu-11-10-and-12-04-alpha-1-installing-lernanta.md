---
layout: post
title: Undefined symbol SSLv2_method in Ubuntu 11.10 and 12.04 Alpha 1 installing Lernanta
published: true
categories: tip
comments: true
---

Today i spent a couple of hours trying to get [Lernanta](http://github.com/p2pu/lernanta) the Open Source application that supports [P2PU's](http://p2pu.org) courses. If you are not familiar with any of those, i highly reccommend giving it a try. While trying to set up my local installation according to the [Lernanta Installation Guide](https://github.com/p2pu/lernanta/wiki/Lernanta%27s-Setup-Install), i ended up facing the following error: 

    Could not import users.views. 
    Error was: /home/vitor/.virtualenvs/lernanta/local/lib/python2.7/site-packages/M2Crypto/__m2crypto.so: 
    undefined symbol: SSLv2_method

After a little bit of researching and googling around, i found out that this error was related to the absence of SSLv2 in Ubuntu's OpenSSL package. The Ubuntu people build OpenSSL without SSLv2 support because the protocol has known security issues. This was introduced in 11.10 version and it also happens in 12.04 Alpha 1.

The following links are related to this issue.

* https://github.com/saltstack/salt/issues/391
* https://lists.launchpad.net/openstack/msg06427.html

## Solution:

The installation guide instruct us to create our virtualenv using the command:
    
    mkvirtualenv lernanta

However, virtual env now changed its default behavior. It seems that since 1.7 version is out one must provide the --system-site-packages trigger modifier to have the old behavior back and have virtualenv also look for system wide packages and use the apt-get version we installed while following the Installation Guide. 

    mkvirtualenv --system-site-packages lernanta


Creating your virtualenv this way, will make virtualenv work as expected in documentation and, finally, make your Lernanta installation work as expected. 

More information about this subject can be found in this link. 

* https://github.com/pypa/virtualenv/issues/210

I hope it was helpful!

See you next time, 



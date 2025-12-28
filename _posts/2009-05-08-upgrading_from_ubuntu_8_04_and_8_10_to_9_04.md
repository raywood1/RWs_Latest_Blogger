---
layout: post
title: "Upgrading from Ubuntu 8.04 and 8.10 to 9.04"
date: 2009-05-08
---

<div class="post-body">
<p>I had Ubuntu 8.04 (Hardy Heron) on one machine and 8.10 (Intrepid Ibex) on another.  I discovered that 8.10 does, but 8.04 does not, permit an in-place update to 9.04 (Jaunty Jackalope).  In other words, I would have to install 9.04 from scratch, using the installation CD, on the machine where 8.04 was installed; but I could update online, without doing a complete new installation with the CD, on the machine running 8.10.

The online update was straightforward.  Following <a href="https://web.archive.org/web/20190906053748/http://blog.taragana.com/index.php/archive/upgrade-ubuntu-810-to-ubuntu-904-and-ext3-to-ext4/">advice</a>, I took the following steps:
<ol><li>Go to System/Administration/Update Manager</li><li>Click the <strong>Check</strong> button to check for new updates.</li><li>If there are any updates to install, use the <strong>Install Updates</strong> button to install them, and press <strong>Check</strong> again after that is complete.</li><li>A message will appear informing you of the availability of the new release.</li><li>Click <strong>Upgrade</strong>.</li><li>Follow the on-screen instructions.</li></ol>The difference here between 8.04 and 8.10 was that 8.04 would not give me that message informing me of the availability of the new release.  That is, once you get as far as 8.10, all of your future updates can be done online.

Note that the online installation process is much slower than the CD-based installation process.  It tied up my machine for hours.  By contrast, I was able to download and burn the ISO for the CD mostly in the background, while continuing to use the machine for other things.  The advantage of the online upgrade is that you don't have to reinstall everything you had previously installed on Ubuntu.

<a href="https://web.archive.org/web/20190906053748/http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21">Websites</a> advising on the upgrade process also provide information on upgrading from the ext3 to the ext4 filesystem.  I did not thoroughly review this process before proceeding with that upgrade.  It seemed to work fine, but then I was not able to reboot my system.  I got Error 24.  I tried reinstalling GRUB, but was not successful, and it looked like others had had the same experience.  From what I could gather, it appeared that the upgrade causes problems only on the boot partition.  Once I reinstalled from scratch, everything seemed OK; there did not seem to be any problems on any other newly upgraded ext4 partitions.  There seemed to be two pieces of advice about upgrading from ext3 to ext4 on the boot partition:  that it's not necessary, and that some programs are not yet ready for it.

The next step for me was to <a href="https://web.archive.org/web/20190906053748/http://raywoodcockslatest.blogspot.com/2009/05/installing-ubuntu-904-jaunty-jackalope.html">install everything from scratch</a>, now that I had wiped out my previous Ubuntu installation.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

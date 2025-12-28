---
layout: post
title: "Synology DS109 NAS:  Unable to Mount - Network Is Unreachable"
date: 2010-10-28
---

<div class="post-body">
<p>I was running Ubuntu 10.04 (Lucid Lynx) on a computer to which <a href="https://web.archive.org/web/20150123170304/http://raywoodcockslatest.blogspot.com/2010/10/ubuntu-1004-connecting-to-synology.html">I had connected a Synology DS109</a> network-attached storage (NAS) unit.  I had resolved a <a href="https://web.archive.org/web/20150123170304/http://raywoodcockslatest.blogspot.com/2010/10/synology-ds109-nas-no-more-connections.html">"no more connections can be made" error</a> on a separate computer, also attached to the DS109, that was running Windows XP.  Now I had a new problem on the Linux machine.  This time, the WinXP machine was connecting to the Internet and to the Synology without a problem, but the Ubuntu computer (referred to here simply as the Ubuntuter) was not connecting to either.<br/>
<br/>
The symptoms included the following:  in Firefox, I was getting "Firefox can't find the server" errors for most webpages; in Nautilus, I would get "Unable to mount" errors when I clicked on the name of a partition on the Synology; and in Synology's DiskStation Manager (DSM), its web-based access to the DS109, an attempt to log in to http://[IP address] (using the IP address from DSM &gt; Control Panel &gt; System Information) gave me a "Processing. Please wait ..." message.<br/>
<br/>
I tried rebooting the Ubuntuter.  That achieved nothing.  Typing "sudo mount -a" gave me this:<br/>
<blockquote>mount error(101): Network is unreachable<br/>
Refer to the mount.cifs(8) manual page (e.g., man mount.cifs)</blockquote>I typed "man mount.cifs."  From that, I gathered that I should type something like "sudo mount -ta cifs," though that precise command didn't work.  The "mount -a" command was supposed to mount everything in /etc/fstab, but apparently it could not mount the fstab items that had network locations.  I tried connecting the Ubuntuter directly to the modem, bypassing the router and the rest of the network (i.e., the Synology and the other computer).  This did nothing.  Apparently it was not just a Synology problem.  I rebooted with an Ubuntu live CD and tried Firefox that way.  It was not able to reach webpages either way (i.e., while connected to the router or directly to the modem).  It seemed I had a hardware problem.  I was using a new Gigabyte GA-MA785GM-US2H motherboard.  It looked like <a href="https://web.archive.org/web/20150123170304/http://www.newegg.com/Product/Product.aspx?Item=13-128-394&amp;SortField=0&amp;SummaryType=0&amp;Pagesize=100&amp;PurchaseMark=&amp;SelectedRating=-1&amp;VideoOnlyMark=False&amp;VendorMark=&amp;IsFeedbackTab=true&amp;Keywords=network&amp;Page=3#scrollFullInfo">a few of its reviewers at Newegg</a> cited intermittent problems in connecting.  The solution, it seemed, was to return the board or try adding a network interface card (NIC).  I tried the latter.<br/>
<br/>
But while I was doing that, I noticed that the little plastic tab on the ethernet cable was gone.  It was possible for the plug to just slide out of the socket.  So I replaced the cable.  That worked on the next bootup.  So at this point the solution seemed to be either (a) if one reboot doens't work, try another, (b) the NIC connector is competitive and will get its act together if you install another card that might take its place, or (c) a better cable.  I gave it some time, to see which it would be.  After several days, I could say with confidence that the simple replacement of the cable made all the difference.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

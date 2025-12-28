---
layout: post
title: "Firefox and FEBE Problems in Ubuntu 9.10 (Karmic)"
date: 2010-01-18
---

<div class="post-body">
<p>As noted in <a href="https://web.archive.org/web/20190906053806/http://raywoodcockslatest.blogspot.com/2010/01/configuring-64-bit-ubuntu-910-karmic.html">a previous post</a>, I was having problems with using FEBE to restore a profile with all of my settings and add-ons preset.  This post describes the steps I took in a failed effort to fix that problem.<br/>
<br/>
I completely uninstalled Firefox, <a href="https://web.archive.org/web/20190906053806/http://swiss.ubuntuforums.org/showpost.php?p=8509740&amp;postcount=6">first</a>, by searching for it in Synaptic and marking it (3.5.7) for complete removal and clicking Apply, <a href="https://web.archive.org/web/20190906053806/http://ohioloco.ubuntuforums.org/showpost.php?p=8291746&amp;postcount=3">and then</a> by navigating to Home in Nautilus and deleting the .mozilla/firefox folder.  It was a hidden folder, so in Nautilus I had to set View &gt; Show Hidden Files to see it.  Then I reinstalled Firefox 3.5.7 in Synaptic and reinstalled FEBE.  To run FEBE in Firefox, I selected Tools &gt; FEBE &gt; Restore Profile (kill the pop-up reminders) &gt; Create new profile (I called mine Working).  This gave me a box that offered to let me name a new profile, but that was not taking any text input.<br/>
<br/>
With the aid of <a href="https://web.archive.org/web/20190906053806/http://softwarebychuck.com/febe/tutorial/febeRestoreProfile.html">the tutorial</a>, I discovered that closing Firefox would actually not close the Restore Profile window.  Now I was able to create my new profile and then Start Profile Restore.  Again, it did what it did before:  "Profile restore in progress ... Please wait" continued for much longer than the "minute or two" recommended by the tutorial, and the hard drive light was not running. I killed FEBE and restarted Firefox.  It did not show FEBE as being installed.   It did show other extensions (Tools &gt; Add-ons) that it had not shown previously. <br/>
<br/>
I installed FEBE again, this time from within the Add-ons window instead of from the Mozilla webpage, and again restarted Firefox.  Now Firefox showed only the two add-ons (FEBE 6.3.2 and Ubuntu Firefox Modifications 0.8) that it had shown at the start.  I went through the profile restore steps again.  To get the "Start profile restore" button to light up, I had to switch back and forth between the default and Working profiles.  Then I started the restore again.  Again, no action.  After a minute or two, I killed it and tried restoring a different profile.  Still nothing.<br/>
<br/>
Another flaky thing that Firefox was doing:  it was opening a tiny window sometimes.  This little window could be expanded, but there was nothing in it.  In Synaptic, I did a Quick Search for Firefox and uninstalled all versions that were installed.  I then reinstalled 3.5.7 and tried again in FEBE.  Still no profile restore.  At this point, I gave up and reinstalled.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raja**:
so i have the same problem... what is the solution

**raywood**:
Raja -- reinstalling was the only solution that worked for me.  Good luck!


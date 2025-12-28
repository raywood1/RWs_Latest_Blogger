---
layout: post
title: "Windows XP & Ubuntu RAID 0 Dual Boot:  Error:  No Such Device"
date: 2010-09-28
---

<div class="post-body">
<p><a href="https://web.archive.org/web/20140612013859/http://raywoodcockslatest.blogspot.com/2010/09/dual-boot-raid-0-ubuntu-1004-and.html">I had set up</a> a dual-boot system with Ubuntu 10.04 on a two-drive RAID 0 array and Windows XP SP3 running from a third hard drive.  I replaced the WinXP drive with a different one, copying the files over from the old drive's partitions to the new one, and rebooted.  When I selected the Windows XP option in the GRUB2 boot menu, I got an error message:<br/>
<blockquote>error: no such device: [apparently a UUID number]</blockquote><blockquote>error: invalid signature.</blockquote><blockquote>Press any key to continue...</blockquote>As described in <a href="https://web.archive.org/web/20140612013859/https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408/comments/90">comment 90</a>, within <a href="https://web.archive.org/web/20140612013859/https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408">a long thread</a> on this Ubuntu bug, with an alternate approach in <a href="https://web.archive.org/web/20140612013859/http://ubuntuforums.org/showpost.php?p=8170878&amp;postcount=6">another post</a>, the solution to this problem was said to involve editing grub-<wbr/>mkconfig_<wbr/>lib.  Since I was able to get into Ubuntu (though not Windows), I took the approach described in comment 90.  In Ubuntu, in Terminal, I typed these commands:<br/>
<blockquote>sudo apt-get update</blockquote><blockquote>sudo apt-get install grub-common</blockquote>The first command ended with errors along the lines of "could not connect to archive.getdeb.net."  This turned out to be an indication that the getdeb repository was down.  I repaired it by <a href="https://web.archive.org/web/20140612013859/http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html">editing sources.list</a> to refer to a mirror site instead.  Next, I typed this:<br/>
<blockquote>sudo gedit /usr/lib/<wbr/>grub/grub-<wbr/>mkconfig_<wbr/>lib</blockquote>and changed gedit's Edit &gt; Preferences to show line numbers.  I went down to line 174, ready to insert a # sign before whatever was on that line.  But it was just "fi" which, I thought, marke the end of an "if" statement.  What they wanted me to add did not look like it belonged there.  The long thread had not been visited for nearly four months; I suspected the file had been changed in a bid to fix the problem.<br/>
<br/>
I got that error in the first place, as noted above, not because of an obvious malfunction in GRUB2, but because I had moved the partition containing the Windows XP program files.  <a href="https://web.archive.org/web/20140612013859/http://ubuntuforums.org/showthread.php?t=1195275">I heard</a> that just typing "sudo update-grub" would cause GRUB2 to search for operating systems.  And it did:  in the process of "Generating grub.cfg," it reported that it found Windows XP on /dev/sdc1.  I wondered if that would fix the problem by itself, so I rebooted and selected the Windows option again from the GRUB menu.  And that was it.  Problem solved!</p>
<div style="clear: both;"></div>
</div>

---
### Comments

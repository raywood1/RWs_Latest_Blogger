---
layout: post
title: "PsYDM in Ubuntu -- A Bust"
date: 2010-01-18
---

<div class="post-body">
<p>I had installed 64-bit Ubuntu 9.10.   I wanted to configure several partitions to open automatically.  For this purpose, I tried using PySDM instead of editing /etc/fstab as root.<br/>
<br/>
PySDM didn't show the names I had given my partitions, so as a guide I also started GParted (System &gt; Administration &gt; GParted, previously known as Partition Editor).  I used the names from GParted in the Name fields on PySDM.  Go by the names under the Partition List at the left side of PySDM.)  For Options, in place of the original "defaults" entry, I followed <a href="https://web.archive.org/web/20190906053746/http://ubuntuforums.org/showthread.php?t=872197">the advice</a> to enter this for ntfs partitions:<br/>
<br/>
auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137<br/>
<br/>
But then I found that the Assistant button in PySDM would allow me to set these options by clicking check boxes that would explain what I was doing, except that the Owner UID was still obscure.  I changed one or two options in Assistant.  This changed "auto" (in my case) to nls=iso8856-1.  The rest of the line (after "auto") was also changed to this:  users,umask=000,utf8,gid=1000,user,owner,uid=1000.  For drive C in a dual-boot Windows XP system, I wound up with this instead:  nls=iso8859-1,users,noauto,umask=000,utf8,gid=1000,user,owner,uid=1000.<br/>
<br/>
For ext3 partitions, the advice on what to enter varied, according to the type of partition:<br/>
<br/>
root partition ( / ): relatime,errors=remount-ro <br/>
home partition (/home): nodev,nosuid,relatime <br/>
other partitions (aside from swap): defaults,users<br/>
<br/>
But when I tried entering "defaults,users" for one such partition, PySDM just shortened it to "users."  I didn't have a separate /home partition.  For all ext3 partitions other than root, I wound up using this instead:  "owner,check,errors=remount-ro,users,user."  I clicked Apply after entering the information for each partition.<br/>
<br/>
PySDM seemed to be confused in some regards.  Some of this confusion disappeared when I unplugged USB flash drives and clicked Refresh.  That is, it seemed to work best with partitions on internal SATA drives.  But it was still linking two separate partitions:  when I would make a change in one, it would make the same change in the other.  So I seemed to have two partitions with the same name.  I tried uninstalling and reinstalling PySDM in Synaptic.  (I think I had already tried closing and reopening the program.)  Eventually, I decided there are <a href="//web.archive.org/web/20190906053746/https://www.google.com/search?hl=en&amp;q=pysdm+bugs&amp;sourceid=navclient-ff&amp;rlz=1B3GGGL_enUS318US318&amp;ie=UTF-8">serious bugs</a> in PySDM, so I uninstalled it and edited fstab manually.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

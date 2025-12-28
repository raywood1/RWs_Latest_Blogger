---
layout: post
title: "Error While Resizing Vista NTFS Partition with GParted"
date: 2010-02-06
---

<div class="post-body">
<p>I was using the GParted 0.5.1 live CD to resize an NTFS partition.  (I had already backed up the data on the partition.)  When I tried to resize in GParted, I got an error:<br/>
<br/>
<blockquote>An error occurred while applying the operations<br/>
<br/>
See the details for more information.<br/>
<br/>
IMPORTANT<br/>
if you want support, you need to provide the saved details!<br/>
See http://gparted.sourceforge.net/larry/tips/<br/>
save_details.htm for more information</blockquote><br/>
I clicked OK.  Unfortunately, the details did not explain what had gone wrong.  I rebooted into Vista and then did a complete shutdown.  (Previously, I had just hibernated the system.)  I allowed a minute or so for the memory to clear, and then rebooted with the GParted live CD.  This time, it worked.  The problem was that I had hibernated instead of completely shutting down Vista before using GParted.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

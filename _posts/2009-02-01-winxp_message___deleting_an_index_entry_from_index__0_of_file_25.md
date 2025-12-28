---
layout: post
title: "WinXP Message:  Deleting an index entry from index $0 of file 25"
date: 2009-02-01
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20190809230359/http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-and-vmware-trying-again-on.html">previously encountered</a> the message, "Deleting an index entry from index $0 of file 25," when booting my Windows XP system.  I assumed it was just some sort of generic screwup or random housekeeping performed by Microsoft.  Now I'm not so sure. 

This time around, I got that message, repeated about a million times, after going into Ubuntu Linux on my dual-boot system.  I went into Ubuntu to delete a large folder -- about 10GB -- that WinXP was taking forever to delete.  I knew Ubuntu would be much faster, and it was.  But now it seemed the reason for that message might be that Windows was trying to catch up with what Ubuntu did.  Files were supposed to be there, according to some information available to Windows; but those files were no longer there; so now Windows had to match up its records with the realities.

If that theory is correct, one solution might be to use Windows for working with files on NTFS filesystems (i.e., those recognized by Windows, shown to be NTFS in GParted or other drive partitioning software), and restrict Linux operations to files on partitions that are formatted Linux-style (e.g., ext3).  Another possibility would be to do joint Linux-Windows operations on files on a removable drive, and then make sure that drive is not connected (so that Windows won't spend minutes or hours checking it out) when Windows is booted.  I have heard there are utilities that allow work on ext3 partitions from within Windows, so that might provide another option.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
I've got the same problem (but replace 25 with 15944) after resizing XP partition in GParted in an effort to give Ubuntu more space. Anyway, managed to accidentally format my Ubuntu partition, got grub 15 error. Got windows loading using XP disc, but now stuck with CHKDSK trying to fix 15944. How did you resolve your recurring error?

**raywood**:
I think I'm only having that problem now with my external hard drive, when I have it turned on at bootup.  If I boot the system without that drive turned on, it seems like I rarely (if ever) have this problem.  But I don't know how to fix it when it does happen.  If I tell Computer Management to do a disk check on reboot, and have the external drive turned on, I can pretty much count on getting a bunch of those "Deleting an index entry" error messages.


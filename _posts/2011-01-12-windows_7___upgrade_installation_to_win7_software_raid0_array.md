---
layout: post
title: "Windows 7:  Upgrade Installation to Win7 Software RAID0 Array"
date: 2011-01-12
---

<div class="post-body">
<p>I was trying to install an upgrade version of Windows 7 on a RAID0 array.  This post contains some notes on what I learned about the possibilities.<br/>
<br/>
I had a new basic hard drive.  I started by installing Win7 on that drive.  The upgrade version of Windows 7 required a previous version of Windows to be installed.  It was not enough just to have the previous disc or serial number.  I was interested in upgrading from Windows XP.  To accomplish this installation, then, I had to install my copy of Windows XP and then upgrade from there.<br/>
<br/>
Having done that, I used Disk Management (diskmgmt.msc) in Win7 to create a couple of Windows 7 software RAID0 arrays on two other empty hard drives.  Unlike other RAID solutions, Win7 was willing to create multiple arrays and single-drive partitions on a pair of drives being used in a RAID0 array.<br/>
<br/>
I hoped to install Win7 into one of those arrays (which I called PROG-FUTURE), and to put my data into another.  Of course, since this was RAID0, I planned to have a good backup scheme for the data.<br/>
<br/>
I went ahead and copied my data into that RAID0 data array.  Later, when it came time to try to install the Win7 upgrade to the PROG-FUTURE array, it seemed that this might have been a mistake.  An attempt to install WinXP to PROG-FUTURE got as far as the point where the installer recognized the various partitions on my drives.  It saw the entire hard drive as a single dynamic disk.  In other words, WinXP might have been willing to install to at least one of the two drives I was using for my RAID arrays.  It gave no sign that it would install itself in any array format to two drives simultaneously.<br/>
<br/>
I was not sure whether an attempt to install WinXP, Win7, or any other operating system to a dynamic drive would run into problems.  There did exist a <a href="https://web.archive.org/web/20190906053719/http://www.dynamic-disk.com/how-to-use-dynamicdiskconverter.html">Dynamic Disk Converter</a> program, and probably others like it, that would apparently be able to convert the dynamic disk to a basic disk format.  I could not say how well such programs would work.<br/>
<br/>
It had occurred to me that perhaps I could use the Universal Restore feature of Acronis True Image Home 2011 (ATIH) to restore a working Win7 installation to the PROG-FUTURE array.  <a href="https://web.archive.org/web/20190906053719/http://raywoodcockslatest.blogspot.com/2011/01/acronis-true-image-home-2011-restoring.html">My attempts</a> along those lines did not succeed.  As far as I could tell, ATIH was not capable of restoring a RAID0 array.<br/>
<br/>
Another possibility was to use Ubuntu 10.10 to copy Windows 7 program files from a Win7 installation on a basic drive to the PROG-FUTURE array.  This did not appear feasible at this time, however, because Ubuntu evidently could not see the Win7 RAID0 array as such.  I also wasn't sure whether the resulting partition would actually boot.<br/>
<br/>
An attempt to install directly from the Win7 upgrade CD to the PROG-FUTURE array failed early in the process, when I received this error message:<br/>
<blockquote>Windows cannot be installed to this hard disk space.  The partition contains one or more dynamic volumes that are not supported for installation.</blockquote>It appeared, in other words, that Windows 7 could not be installed to a software RAID0 array created by Win7 itself.  I found <a href="https://web.archive.org/web/20190906053719/http://superuser.com/questions/62925/how-do-i-convert-a-windows-7-ultimate-install-to-raid-0">a thread</a> suggesting that there were ways to make it work, but it seemed that the process was tricky and prone to problems.  It appeared that the array would probably better be created from some other software or by using a RAID0 controller on the motherboard or on a separate controller card.  Another possibility that I had not heard of previously was <a href="https://web.archive.org/web/20190906053719/http://en.wikipedia.org/wiki/VHD_(file_format)#Windows_7_support_for_Native_VHD_Boot">native virtual hard disk (VHD) boot</a>.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

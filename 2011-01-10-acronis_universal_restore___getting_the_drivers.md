---
layout: post
title: "Acronis Universal Restore:  Getting the Drivers"
date: 2011-01-10
---

<div class="post-body">
<p>As shown in another post in this blog, I was in the process of using the Universal Restore feature of Acronis True Image Home 2011 (ATIH) to restore an Acronis drive image from one drive to another.  For this purpose, <a href="https://web.archive.org/web/20190906053705/http://kb.acronis.com/content/13671">Acronis made clear</a> that I would need certain motherboard drivers to succeed:<br/>
<blockquote>You [must] have drivers for the hard disk drive controller or chipset drivers for the new computer. These drivers are critical for booting the operating system. You can download the drivers for your motherboard on the Vendor's web-site. Please note, if you downloaded the drivers in *.exe, *.cab, *.zip format, you should extract them first. The driver files should have the *.inf, *.sys or *.oem extensions. </blockquote>My motherboard was a Gigabyte <a href="https://web.archive.org/web/20190906053705/http://www.gigabyte.us/products/product-page.aspx?pid=3447#ov">GA-MA785GM-US2H</a>.  I went to Gigabyte's download webpage and indicated that I wanted drivers for 32-bit Windows 7.  They offered me several kinds of drivers:  audio, chipset/VGA, LAN, and SATA RAID.  Plainly, Acronis was not telling me to get the audio or LAN drivers.  I definitely needed the chipset/VGA driver.  How about the SATA RAID driver?  I wasn't using hardware RAID.  I was relying on Windows 7 software RAID, and it did not require the floppy-based pre-Windows installation procedure that those SATA RAID drivers required.  The description of the chipset driver said "AMD Chipset Driver (include chipset\sata raid\vga driver)."  That sounded like the all-purpose thing Acronis wanted.  So I guessed that I probably needed only the chipset/VGA driver.<br/>
<br/>
The chipset driver was a 62MB download called motherboard_driver_chipset_amd_7series-v2.0_win7-32.exe.  My first question was, how do I extract drivers from an .exe file?  I tried running it.  Fortunately, it unzipped itself.  Apparently it was packaged as an executable whose purpose in executing was just to let itself breathe.  Next, how to find the .inf, .sys, or .oem file(s) needed?  I focused Windows Explorer on the unzipped folder and typed *.inf in the search bar at the top right-hand corner of the Windows Explorer screen.  I hit Ctrl-A to select everything that the search produced, Ctrl-C to copy them all, and then went off and created a new folder (not on drive C) and hit Ctrl-V to paste these copies into there.  I did the same thing for .sys and .oem.  There weren't any .oem files, but I came up with 16 of the other two kinds.<br/>
<br/>
Those may or may not have been the right drivers.  I hoped that ATIH would look at the folder, when doing its Universal Restore, and would see what it wanted in there.  Unfortunately, as described in another post in this blog under the title, "Acronis True Image Home 2011:  Restoring Windows 7 to RAID 0," this was pretty much where the matter died.  The responses to <a href="https://web.archive.org/web/20190906053705/http://forum.acronis.com/forum/17860">a question I had posed</a> in Acronis's support forum were indicating that I could not restore to a Win7 software RAID0 array.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

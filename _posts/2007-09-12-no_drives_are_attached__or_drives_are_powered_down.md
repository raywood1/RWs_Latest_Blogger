---
layout: post
title: "No Drives Are Attached, or Drives Are Powered Down"
date: 2007-09-12
---

<div class="post-body">
<p>I was starting to build <a href="https://web.archive.org/web/20180904032933/http://raywoodcockslatest.blogspot.com/2007/08/quick-and-easy-desktop-computer.html">a second computer</a>.  I installed a <a href="https://web.archive.org/web/20180904032933/http://www.newegg.com/Product/Product.aspx?Item=N82E16827248008">Philips SPD2513BD DVD burner</a>.  I didn't notice that it was a SATA drive, and I was a little bummed about using up one of my two SATA connections, in this new computer, when I could have used one of the IDE/ATA connectors instead.  But in the worst case I could swap it with the IDE burner in the other computer.  I liked the specifications and the looks of this drive, and I had already paid shipping, so I decided to make a go of it.

My plan for a quick and easy Windows XP Professional installation, on this new computer, was to use DriveImage 2002 to install a drive image PQI file containing a complete snapshot of an earlier WinXP installation.  That way, I would not have to go through the whole rigmarole of installing Windows, sitting there hitting keys to get it to download updates, etc.  I would just re-install this already complete previous installation, change a few hardware items, and be done with much of the installation chore.

Unfortunately, it didn't work quite that way.  When I tried to boot from the Drive Image CD, I got this error message:
<blockquote>No Drives Are Attached, or Drives Are Powered Down
The Device Driver Is Not Installed</blockquote>The message was obviously incorrect, insofar as it was coming from a CD that was loaded in the DVD drive.  I had previously booted Bart PE and had seen, there, and also in an Ubuntu bootup, that the system was indeed recognizing both the DVD drive and the hard drive.  I did a Google search for the error message, but came up with no answers.  I was stumped.

I searched for the error message <a href="https://web.archive.org/web/20180904032933/http://groups.google.com/groups?q=%22No+Drives+Are+Attached,+or+Drives+Are+Powered+Down%22&amp;sourceid=navclient-ff&amp;ie=UTF-8&amp;rlz=1B3GGIC_enUS235&amp;um=1&amp;sa=N&amp;tab=wg">in Google Groups</a> as well.  There, I got the idea to check the BIOS.  No clues in the BIOS, but I then thought of trying to boot Drive Image from the floppy disk.  (I had recently recopied Drive Image to fresh floppies.)  But that gave me a Grub Error 22.  Evidently this system was not willing to boot from the floppy, even though I did have it third in the BIOS bootup sequence.  I tried moving it to first.  That worked.  The floppy booted.  Apparently Grub had come preloaded ... or, as I thought about it, perhaps I had not completely reformatted the hard drive after installing Ubuntu on it.  I postponed the Drive Image process to verify that, rebooting with PartitionMagic 8.0.  Of course, it wasn't prepared to load that, either, not from the CD anyway, so I reverted to the original plan and proceeded to load Drive Image from the floppy, figuring I would fool with the partition issues later.  But then -- I had forgotten -- Drive Image was able to identify and delete the partition, so PM wasn't needed.  I was surprised and pleased that DI was able to read the PQI, given that it was saved on a DVD rather than a CD.  I hadn't been sure that DVD technology was in the mainstream back in 2002.

I still got Grub Error 22, so I researched it and <a href="https://web.archive.org/web/20180904032933/http://www.neowin.net/forum/lofiversion/index.php/t405091.html">got the advice</a> to boot from the WinXP program CD, go into Recovery Console, and use FIXMBR and FIXBOOT.  That solved the problem.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

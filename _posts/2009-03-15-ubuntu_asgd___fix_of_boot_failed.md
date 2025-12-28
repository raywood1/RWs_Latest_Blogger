---
layout: post
title: "Ubuntu ASGD:  Fix of Boot Failed"
date: 2009-03-15
---

<div class="post-body">
<p><a href="https://web.archive.org/web/20190906053750/http://raywoodcockslatest.blogspot.com/2009/02/ubuntu-grub-error-22-error-15.html">I previously used</a> Auto Super Grub Disk (ASGD) to restore the GRUB bootloader after a Windows XP installation wiped it out.  That is, I had Ubuntu 8.10 (Intrepid Ibex) up and running on a dual-boot system with WinXP, but then I had to reinstall Windows and, when I did so, I no longer got a bootup option to go into Ubuntu instead of XP.  Now the system automatically went right into Windows when I booted it, with no Ubuntu option.  So I tried running ASGD, as described in that previous post, to fix the problem, but ASGD gave me no joy.  Then I tried booting with the alternate Ubuntu CD (again, see the previous post for details), but this time it didn't seem to be working as I had written it up previously.

This time, when I chose the "Rescue a broken system" option on the Ubuntu Alternate CD, the "Execute a shell" option gave me a prompt that didn't respond as I had described in my previous post.  There was something not right, so I had to revisit the problem.  The shell in question was ash (that's the name of the program that was waiting there to accept my command-line instructions), and the "grub" command didn't mean anything to ash.  So I typed "exit" to get out of the shell, and reviewed the "Ubuntu installer main menu," there in the Rescue option on the Alternate CD.

Another possibility on that menu was "Enter rescue mode."  I tried that.  It asked me what device I wanted to use as a root system.  I did know the answer to that because, following my previous instructions, I had already run "fdisk -l" and had seen that my Linux program partition was located on sdc5 (also known as hd(2,4), because the hd count begins at 0, not 1).  So I named /dev/sdc5 as the "device to use as root file system," there in the rescue mode option.

That appeared to be the step I had neglected to write up in my previous instructions.  Now, sure enough, I did get an option to "Execute a shell in /dev/sdc5."  I thought I would give it another go, and this time typing "grub" did produce a "grub" prompt.  So I entered the same commands as before:
<blockquote>root (hd2,4)
setup (hd2)
quit
exit
</blockquote>and then I chose the "Reboot the system" option.  And, sure enough, that was all I needed to do.  It worked again.

So, basically, after reinstalling Windows, if ASGD and rebooting didn't give me a GRUB menu, the thing to do was to reboot with the Alternate Ubuntu CD, designate (hd2,4) as my Linux partition, and then reboot from the hard drive.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

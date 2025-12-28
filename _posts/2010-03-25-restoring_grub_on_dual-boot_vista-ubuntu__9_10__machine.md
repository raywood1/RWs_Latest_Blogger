---
layout: post
title: "Restoring GRUB on Dual-Boot Vista-Ubuntu (9.10) Machine"
date: 2010-03-25
---

<div class="post-body">
<p>I had Ubuntu 9.10 (Karmic Koala) installed.  I reinstalled Microsoft Vista.  This knocked out the GRUB boot menu.  To restore the boot menu, I followed some Ubuntu <a href="https://web.archive.org/web/20190906053700/https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows">community documentation</a>.  The steps I used there, boiled down for my purposes, were simply to reboot from the Ubuntu CD, go into the Ubuntu partition via the Places menu, type "mount | tail -1" to make sure the Ubuntu partition was now mounted (in my case, it said something like "/dev/sda2 on /media/UBUNTU type 3" because I had named the partition using GParted), type "ls /media/UBUNTU/boot" to make sure I had the partition containing GRUB (along with memtest86+ and other files), and then run "sudo grub-install --root-directory=/media/UBUNTU /dev/sda."  That last command did not end in a number (e.g., sda2); it was simply the drive containing the boot partition.  In place of UBUNTU in my example, I would have typed the long UUID if that was what the mount command had given me.<br/>
<br/>
That pretty much fixed it.  When I rebooted, I did have a GRUB menu.  But when I opted to go into Ubuntu, I got an error message:<br/>
<blockquote>One or more of the mounts listed in /etc/fstab cannot yet be mounted:</blockquote><blockquote>SWAP: waiting for UUID=[UUID number]</blockquote><blockquote>Press ESC to enter a recovery shell.</blockquote>I pressed ESC.  I went to Applications &gt; Accessories &gt; Terminal and typed "sudo gedit /etc/fstab."  This opened fstab.  The lines weren't wide enough to view clearly, so I expanded the box.  Fstab contained an entry for SWAP, which (above) was the partition that didn't boot in my case.  I started another Terminal session and typed "blkid" to see what the UUIDs were.  I saw that the UUIDs and the /dev entries for SWAP didn't match.  I changed the fstab line for SWAP to match what blkid had given me, for both the UUID and the /dev location.  (I had to use the right-click option to copy from the Terminal output for blkid.)  I saved fstab and rebooted.  That seemed to fix it; the boot proceeded normally.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

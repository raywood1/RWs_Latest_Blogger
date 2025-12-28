---
layout: post
title: "Ubuntu 10.04 Installation:  The Streamlined Version"
date: 2010-09-09
---

<div class="post-body">
<p>In <a href="https://web.archive.org/web/20190906053708/http://raywoodcockslatest.blogspot.com/2010/09/ubuntu-1004-installation-another-go.html">another recent post</a>, I described the process of installing Ubuntu 10.04.  This post offers a streamlined version of that post.  That is, it describes another such installation, performed on the basis of that post.<br/>
<br/>
The first step was to install Ubuntu from the live CD.  As before, in this step I installed everything into one root partition.  When installation was complete, I copied my saved fstab from a separate partition to replace the existing /etc/fstab, and then typed "sudo gedit /etc/fstab."  There, I replaced the UUID for the root partition with the new one shown in another Terminal session via "sudo blkid."  I saved and closed fstab.  This part still did not go smoothly -- I still had not mastered the translation of <a href="https://web.archive.org/web/20190906053708/https://help.ubuntu.com/community/Partitioning/Home/Moving#Copy%20/home%20to%20the%20New%20Partition">the Ubuntu Community Documentation webpage</a> into terms that fit my situation -- but essentially I typed "cd /" and then "sudo mv /home /old_home" to park the newly installed but largely empty /home folder; then "sudo mkdir /media/home."  On reboot, my desktop was restored to its previous condition.  I deleted the /old_home folder.<br/>
<br/>
Next, I went to the folder where I had saved my backup copy of sources.list and typed "sudo cp sources.list /etc/apt/."  I opened sources.list, copied the commented command lines, and ran them.  They generated what appeared to be error messages.  In Software Sources, I triggered a reload.  It closed without errors.  In Synaptic, I installed these programs:  acroread, acroread-fonts, adobe-flashplugin, boinc, dvgrab, fdutils, gparted, mplayer, nautilus-open-terminal, ntfs-config, p7zip-full, sysinfo, ubuntu-tweak, unetbootin, and webhttrack, as well as these font packages:  ttf-mscorefonts-installer, sun-java6-fonts, ttf-sil-gentium, ttf-sil-gentium-basic, ttf-dustin, and ttf-georgewilliams.  As before, I typed "sudo sh" to install my .bin and .bundle downloads (e.g., GoogleEarthLinux.bin) and double-clicked to install my .deb downloads.  Then I went into Update Manager, and ran and reran it until I was all caught up.<br/>
<br/>
Monitor driver installation and BOINC configuration were as described in the "Settings and Adjustments" section of <a href="https://web.archive.org/web/20190906053708/http://raywoodcockslatest.blogspot.com/2010/09/ubuntu-1004-installation-another-go.html">the previous post</a>.  The GRUB2 menu edits, as described more carefully in that post, were as follows:  to get rid of the Memtest+ options, I typed "sudo chmod -x /etc/grub.d/20_memtest86+."  To let Ubuntu remember which operating system it had used last, I typed "sudo gedit /etc/default/grub," changed the first line to be "GRUB_DEFAULT=saved," and added a second line that said "GRUB_SAVEDEFAULT=true.  To limit the number of Ubuntu kernels shown, I typed "sudo gedit /etc/grub.d/10_linux," added "GRUB_DISABLE_LINUX_RECOVERY=true" at the top, and changed two lines at the bottom to be three that read as follows:<br/>
<blockquote>list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`<br/>
list=`version_find_latest $list`<br/>
done</blockquote>I saved and closed that and typed "sudo update-grub."  I typed "sudo vmware" and made some root adjustments there.  I rebooted and everything looked good.  There were a few rough spots, but I could see that this might not take very long at all, once you got the hang of it.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I should have added the installed-software procedure:   Make the backup list of programs installed in an existing Ubuntu setup with "dpkg --get-selections > installed-software.log," and then restore it in a new Ubuntu setup with "dpkg --set-selections < installed-software.log."

**raywood**:
... followed by dselect.  See http://ubuntuforums.org/showthread.php?t=261366

**raywood**:
For a more complete installation, I should have started Firefox, to let its add-ons get caught up with their updates.  Likewise any other programs that were likely to be updated.  Also, Startup Applications were not retained from the previous installation; I had to do that manually.

**raywood**:
I have added ntp in Synaptic.  Also, regarding the comment on dselect, the only option I used was Install.

**raywood**:
Found an older but clearer explanation of the process of moving the /home folder:  http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html

**raywood**:
In one case where the /home folder process did not work right, I found the problem was actually not with the way I had adjusted Ubuntu, but with the home folder.  Restoring a replacement of it from an Acronis True Image backup fixed that problem.

**raywood**:
To make the Launchpad software source work properly, I had to go to Applications > Accessories > Passwords and Encryption Keys > File > New > PGP Key > Continue.  After quite a delay, it generated a key.  Then I typed "gpg --list-keys."  I copied the eight-digit number that came after "pub #####/" (i.e., after the word "pub" and after the five-digit number and the slash).  (It was actually a combination of eight letters and numbers.)  I pasted that at the end of this command:  "gpg --send-keys --keyserver keyserver.ubuntu.com [eight-digit number]."  Then I typed "gpg --fingerprint" and copied the "Key fingerprint" number (a total of 40 letters and numbers) and pasted it into the box in the appropriate webpage on the Launchpad site, which I found by logging in at https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories.  This prompted them to send me an email with an OpenPGP key.  I copied the key, beginning with the first dash on the line that said "BEGIN PGP MESSAGE" and continuing through the last dash on the line that said "END PGP MESSAGE."  I saved that key in a text file called X.TXT.  Then, in the folder where I saved it, I typed "gpg -d X.TXT."  This opened up the secret instructions.  The instructions included a link to a webpage.  I went there and clicked on the button to confirm.  I was done.  Easy!  (not)


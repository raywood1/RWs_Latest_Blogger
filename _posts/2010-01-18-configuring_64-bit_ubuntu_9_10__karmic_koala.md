---
layout: post
title: "Configuring 64-Bit Ubuntu 9.10 (Karmic Koala)"
date: 2010-01-18
---

<div class="post-body">
<p>In <a href="https://web.archive.org/web/20190906053804/http://raywoodcockslatest.blogspot.com/2009/05/installing-ubuntu-904-jaunty-jackalope.html">a previous post</a>, I described the steps I followed in setting up x64 Ubuntu 9.04 (as refined in <a href="https://web.archive.org/web/20190906053804/http://raywoodcockslatest.blogspot.com/2009/08/installing-ubuntu-904-jaunty-jackalope_25.html">a later post</a>).  This post does the same for Ubuntu 9.10.  I won't re-describe steps that are already spelled out in some detail in that previous post and in the other webpages to which it refers.  I'll still provide most of the details here, just not as much in-depth explanation.<br/>
<br/>
<b><u>Deciding on a Clean Install</u>.</b>  I was installing on a machine where I had previously been running 9.04.  I installed 9.04 on top of 8.10 on that machine, and this seemed to lead to some unusual problems -- you know, the kind of issue that brings up almost nothing in a Google search.  The better approach was apparently to do a clean install.  So now it was time to do that, replacing 9.04 with 9.10.<br/>
<br/>
My first question was, what should I preserve from my previous setup, and how can I preserve it?  <a href="https://web.archive.org/web/20190906053804/http://www.linuxquestions.org/questions/susenovell-60/how-to-save-settings-passwords-etc.-before-doing-clean-install-from-10.2-to-10.3-596228/#post2944205">One suggestion</a> was to try this:<br/>
<blockquote>tar cf /media/[backup drive]/[backup folder]/[backup filename].tar /etc /home<br/>
</blockquote>That didn't work for me, as my /home directory contained 32GB.  Another post in that same thread suggested installing your stuff to a separate /home partition, so that your settings wouldn't be wiped out by future clean installations.  I found <a href="https://web.archive.org/web/20190906053804/https://help.ubuntu.com/community/Partitioning/Home/Moving">a guide</a> to moving the /home partition.  I started to use GParted to make a 50GB /home partition.  I chose ext3 because ext4 still seemed to have <a href="https://web.archive.org/web/20190906053804/http://ubuntuforums.org/showthread.php?t=1133719&amp;page=28">some issues</a>.  I discovered that Ubuntu's manual installer has an option not to format the partition you're installing to, so as to preserve your old settings.  I decided against both of these approaches because I did want to wipe out my old /home partition, with its mistakes and assorted junk.  So I installed Ubuntu as described in the previous post, working from a CD.  I went into System &gt; Administration &gt; Update Manager &gt; Check.  This gave me 184 updates and a reboot.<br/>
<br/>
<b><u>Software Sources</u>.</b>  Next, I went into Applications &gt; Ubuntu Software Center &gt; Get Free Software &gt; search for "restricted extras" &gt; select Ubuntu restricted extras &gt; Install.  Next, System &gt; Administration &gt; Hardware Drivers &gt; NVIDIA accelerated graphics driver (version 185) (because I had an NVIDIA video card) &gt; Activate &gt; Close.  Next, System &gt; Administration &gt; Software Sources &gt; Ubuntu Software tab &gt; Download From &gt; Other &gt; Select Best Server &gt; Choose Server (whichever one it highlights) &gt; Close.  Also, in Software Sources, go to the Other Software tab, select the two entries that are already there, and click Add to add more.  The additional lines come from <a href="https://web.archive.org/web/20190906053804/https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates">the X-Updates website</a>.  There, click on "Technical details about this PPA," specify Karmic, and copy the two deb lines there, one at a time, into the APT line, clicking "Add Source" after each.  Next, on that same webpage, follow the Signing Key instructions, just below the deb lines.  Click Close.  This will bring up "The information about available software is out-of-date."  Click Reload.  If you don't get a "Reload" option when you click Close, go back into Third-Party Software and unclick and then re-click some item and try again.<br/>
<br/>
<u><b>Synaptic</b></u><b>.</b>  I had read an <a href="https://web.archive.org/web/20190906053804/http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8045903&amp;postcount=3">upgrade tip</a> that said I could automatically reinstall my installed Synaptic applications by using System &gt; Administration Synaptic Package Manager &gt; File &gt; Save Markings As &gt; Save full state and then, after the upgrade, use Synaptic &gt; File &gt; Read Markings.  I had saved as advised; now I tried the read (restore) step.  It did not work well for me.  After this and a few more misadventures, I wound up reinstalling Ubuntu from scratch.  For posterity, the next few paragraphs describe the failed approach.  After that, I describe the alternate approach, the one that I had used in previous installations.  <br/>
<br/>
<br/>
To try the Read Markings approach, I started by going to Places &gt; Computer and double-clicking on the drive where I had saved the backup.  Then Apply.  But that gave me an error:  "Could not apply changes!  Fix broken packages first."  So I went into Synaptic &gt; Edit &gt; Fix broken packages.  That, in turn, generated this message:  "An error occurred.  The following details are provided:  E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."  Adapting <a href="https://web.archive.org/web/20190906053804/http://www.linuxforums.org/forum/debian-linux-help/59318-package-problem-broken-dependency-more.html">some older advice</a>, I closed Synaptic and then typed this:<br/>
<br/>
sudo -i<br/>
apt-get clean<br/>
apt-get autoclean<br/>
apt-get update<br/>
apt-get upgrade<br/>
apt-get dist-upgrade<br/>
<br/>
Now I tried Synaptic again.  The steps just taken did not seem to change anything; but after tinkering with the same options, Edit &gt; Fix broken packages seemed to work, and Apply proceeded to download 259 files.  Since the more automated Markings approach seemed to work, the advice for the next installation would be to uninstall any unwanted packages before running the Save Markings step.<br/>
<br/>
Instead of all that, on the second installation I selected and installed these packages from within Synaptic:  boinc; boinc-manager; fdutils (if you expect to be using a floppy drive); gparted; ntfs-config; ntfsprogs; p7zip-full; sysinfo; and webhttrack. (If numerous items come up in response to your search, click on the Package heading to sort them alphabetically. Also install other related packages, if given the option.) (If some of my later descriptions don't work for you, it may be because you didn't install one of these.)  For my e-mail, I preferred thunderbird, so I added that, and uninstalled evolution.  Some of these may ask if you want to "Mark additional required changes?" Click "Mark" and go on to the next one. Then click Apply. Some of these programs may already be shown as being installed on your system. If so, no problem.<br/>
<br/>
<u><b>Other Programs</b></u><b>.</b>  To install Google Earth, I didn't use a previous download (see above). Instead, I typed these two lines:  First, "wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin," and then "sh GoogleEarthLinux.bin" (as always, without quotation marks).<br/>
<br/>
I didn't have to install Firefox -- it came installed with Karmic -- but, as in the past, I hoped to speed up my customization by using the FEBE add-in.  I had made a FEBE backup before this reinstallation.  Now, to restore my previous settings, I <a href="https://web.archive.org/web/20190906053804/https://addons.mozilla.org/en-US/firefox/addon/2109">installed FEBE</a>.  Unfortunately, Firefox did not seem to be functioning properly. I address this set of problems in <a href="https://web.archive.org/web/20190906053804/http://raywoodcockslatest.blogspot.com/2010/01/firefox-and-febe-problems-in-ubuntu-910.html">a separate post</a>.  (I think the problem may have been that I tried to use a FEBE backup of a Windows XP Firefox installation.  Firefox on Ubuntu does not use the same add-ons.)  To have a browser, I downloaded <a href="https://web.archive.org/web/20190906053804/http://www.opera.com/download/?os=linux-x86-64&amp;ver=10.10&amp;local=y">64-bit Opera</a>.  (At this point, 64-bit Google Chrome was <a href="//web.archive.org/web/20190906053804/https://www.google.com/support/forum/p/Chrome/thread?tid=76937011a558491e&amp;hl=en">apparently unstable</a>.)  Opera came as a .deb file, so I just double-clicked to install it.  On the reinstall, I didn't even bother with FEBE at this point; for the time being, I just used Opera in its basic form.<br/>
<br/>
VMware Workstation 7 came as a .bundle file, which required the same installation steps as .bin files.  First, I typed "chmod +x" [filename] and then "./"[filename]. I designated "/home/[username]" as the installation directory.  (In all cases, fill in the bracketed names with your actual names.)<br/>
<br/>
I didn't have any .tar files to install at this point.  If I had, my notes said I should have used tar -vxf filename.tar.gz (or possibly tar xvfz instead), tar xvf filename.tar, and tar yxf filename.tar.bz2.<br/>
<br/>
<u><b>Drive Automount</b></u><b>.</b>  I wanted some partitions to be mounted automatically at startup.  In the past, I had <a href="https://web.archive.org/web/20190906053804/https://help.ubuntu.com/community/AutomaticallyMountPartitions">manually edited</a> /etc/fstab to do this.  This time, I decided to try <a href="https://web.archive.org/web/20190906053804/http://pysdm.sourceforge.net/">PySDM</a>, which was apparently short for Python Storage Device Manager (System &gt; Administration &gt; Storage Device Manager).  Unfortunately, <a href="https://web.archive.org/web/20190906053804/http://raywoodcockslatest.blogspot.com/2010/01/psydm-in-ubuntu-bust.html">my efforts</a> suggested there were serious bugs in PySDM, so I uninstalled it and edited fstab manually.  I began by typing "sudo ntfs-config" and then "sudo gedit /etc/fstab."  I also ran System &gt; Administration &gt; GParted for a GUI reference, to help me see what I was supposed to be doing.  I plugged in all of my USB drives, typed "sudo blkid" to get the universal identifier (UUID) for each partition, and copied and pasted that into fstab.  I refreshed GParted (Ctrl-R) and created a comment line for each partition shown in GParted.  This was about the point when things seemed so grotesquely screwed up (because of PySDM, it seemed) as to warrant a complete reinstallation.  When I rebooted, it looked like everything was getting automatically booted without a problem.  I saved a copy of my resulting fstab in case I had to reinstall again.  I noticed that the booted partitions were all represented by icons on the desktop.  I wanted to remove those, so I typed "gconf-editor" and went into apps/nautilus/desktop, unnclicked volumes_visible, and closed the Configuration Editor, and the icons were gone.<br/>
<br/>
<br/>
<br/>
<u><b>Miscellany</b></u><b>.</b>  Ubuntu 9.10 used Grub2, which no longer used menu.lst.  <a href="https://web.archive.org/web/20190906053804/http://stream-recorder.com/forum/edit-grub-entries-ubuntu-9-10-no-t5122.html?s=3c190dd1cf8b5606e63df8a4a7a73ccb&amp;">I heard</a> it was no longer possible to edit the Grub menu to remove entries for older kernels; instead, you had to remove the whole kernel, and then the menu entry would go away too.  ||  In System &gt; Preferences &gt; Startup Applications, I added Thunderbird, Firefox, and VMware Workstation.<br/>
<br/>
The next steps are going to be to <a href="https://web.archive.org/web/20190906053804/http://www.cyberciti.biz/faq/linux-backup-thunderbird-email-profile/">restore my Thunderbird profile</a> backup and finish the automation of the <a href="https://web.archive.org/web/20190906053804/http://onlyubuntu.blogspot.com/2008/05/how-to-backup-using-rsync-in-ubuntu.html">rsync scripts</a> I have been playing with for some months now.  But those steps will have to come later.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
On the multimedia front, I also added more plugins to my Ubuntu installation.  See http://raywoodcockslatest.blogspot.com/2010/01/plugins-needed-in-ubuntu-910.html

**raywood**:
I also tried and, for reasons of stability, I untried AVIDemux and Winff for video editing.  I did find, though, that commands like these would combine multiple VOBs from a DVD into one VOB:mplayer dvd://1 -dumpstream -dumpfile /media/DVDout01.vobHopefully they combined those VOBs in some coherent order.  Haven't checked that yet.In the process of installing and uninstalling those programs, I also installed (and decided to keep) mplayer and ffmpeg.  With more time, I think ffmpeg might prove to be an excellent command-line converter, though the editing is still apparently best done in Windows.

**raywood**:
From Synaptic, I also installed xournal to edit PDFs.

**raywood**:
In the new Ubuntu installation, I wanted Grub2 to boot up whatever operating system I had used last, instead of always defaulting to Ubuntu.  Following the advice at https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202, I edited /etc/default/grub and changed one line to say GRUB_DEFAULT=saved.  After saving that file, I typed "sudo update-grub" and it worked.

**raywood**:
In Synaptic, I also added dvgrab to capture video.

**raywood**:
I changed the automatic fsck setting.  By default, fsck checks hard drive partitions after every 30 reboots.  I don't reboot often, so it can be quite a while between checks.  The system was acting funky, so I decided to make it check more frequently.  I could have specified a smaller number of reboots with the -c option, but instead I chose to specify a number of days with the -i option, as follows:sudo tune2fs -i 5d  /dev/sdb5That uses tune2fs to change the setting so that it checks that particular partition every five days (d).  I could have specified weeks (w) or months (m) instead.  That's for the partition where Ubuntu is installed (/dev/sdb5).  I also entered similar commands, on a slower timeframe, for other ext3 (Linux) partitions.  I found these partitions by using sudo fdisk -l.

**raywood**:
I also installed AutoFsck so that fsck would run at shutdown rather than startup, unless I chose otherwise.  That way, I would not have to wait an hour for the computer to get back up and running.  See https://wiki.ubuntu.com/AutoFsck


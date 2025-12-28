---
layout: post
title: "Synology NAS:  Mapping the Network Drive"
date: 2010-10-31
---

<div class="post-body">
<p>I had newly installed Ubuntu 10.10 and was trying to communicate with my <a href="//web.archive.org/web/20190906053722/https://www.google.com/search?hl=en&amp;q=synology+ds109&amp;sourceid=navclient-ff&amp;rlz=1B3GGLL_enUS403US403&amp;ie=UTF-8">Synology DS109</a> network-attached storage (NAS) unit.  I had <a href="https://web.archive.org/web/20190906053722/http://raywoodcockslatest.blogspot.com/2010/10/synology-ds109-nas-unable-to-mount.html">previously resolved some problems</a> with this unit, but some had remained unresolved; and now, in any case, I was starting over.<br/>
<br/>
<a href="https://web.archive.org/web/20190906053722/http://www.synology.com/support/download.php?lang=enu&amp;m=DS109">I had downloaded</a> and installed DiskStation Manager (DSM) 3.0, the Synology Assistant, and the User's Guide.  DSM was a web-based program, apparently running on the DS109, that I accessed by simply typing the DS109's address (e.g., 192.168.2.1) into the Firefox address bar.  I was able to connect to the DS109 by typing the username and password that it needed (i.e., not my Ubuntu username and password).<br/>
<br/>
As outlined in <a href="https://web.archive.org/web/20190906053722/http://raywoodcockslatest.blogspot.com/2010/10/ubuntu-1004-connecting-to-synology.html">a previous post</a>, I had also created a mount point ("sudo mkdir /media/SYNDATA") for the DS109's SYNDATA partition.  The fstab (i.e., "sudo gedit /etc/fstab") contained a line that had worked previously to let me contact that partition.  The line I was using was this:<br/>
<blockquote>//192.168.2.1/SYNDATA  /media/SYNDATA  cifs  user,uid=ray,gid=users,rw,suid,credentials=/etc/cifspwd,iocharset=utf8  0  0</blockquote>where "ray" was my Ubuntu user ID, not my DS109 user ID.  The DS109 user ID was contained in the /etc/cifspwd file; and now, as I looked at this, I realized that reinstalling Ubuntu from scratch had surely wiped out that file.  So I recreated it ("sudo gedit /etc/cifspwd"), using my DS109 user ID and password, in this form:<br/>
<blockquote>username=[DS109 username]<br/>
password=[DS109 password]</blockquote>and that's all that file contained.  Example:  if my DS109 username had been Joe, the first line in this two-line file would have been "username=Joe," and the second line would have been "password=JoesPassword" (wahtever that user's actual password was).  Then I typed these commands<br/>
<blockquote>sudo chmod 0600 /etc/cifspwd<br/>
sudo mount -a</blockquote>These were the basic steps recommended in a relevant <a href="https://web.archive.org/web/20190906053722/http://forum.synology.com/wiki/index.php/Mapping_a_Network_Drive#How_to_map_a_drive_using_a_Linux.2FUnix_Environment">page in Synology's wiki</a>.  The problem -- or at least *a* problem -- as I eventually figured out (or re-figured; Synology's tech support may have originally suggested it), was that the "credentials" part of the fstab line was not working.  If I replaced "credentials=/etc/cifspwd" with "username=Joe,password=JoesPassword" (and then saved fstab), then the "sudo mount -a" command worked:  SYNDATA appeared in Nautilus like any other partition.  So what would happen if I put exactly that -- username=Joe,password=JoesPassword -- on the same line in /etc/cifspwd, instead of putting them on two separate lines?  No dice.  The cifspwd file was a dud.  I left the username and password information in the fstab, and deleted the cifspwd file ("sudo rm cifspwd").<br/>
<br/>
So the short answer I arrived at, here, was that the Synology wiki was wrong, at least for my purposes.  I needed to take all the other steps -- creating a mount point, etc. -- but instead of creating the cifspwd file, I just needed to enter a line in /etc/fstab of this form:<br/>
<blockquote>//192.168.2.1/SYNDATA  /media/SYNDATA  cifs  user,uid=[Ubuntu username],gid=users,rw,suid,username=[Synology username],password=[Synology password],iocharset=utf8  0  0</blockquote>and possibly the "iocharset" part was optional.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

---
layout: post
title: "Resuming a VMware Virtual Machine:  Could Not Open /dev/vmmon"
date: 2010-05-16
---

<div class="post-body">
<p>I was tweaking Ubuntu 10.04 (Lucid).  One step I took was to clean out old entries from the GRUB menu.  This involved removing some old kernels.  <a href="https://web.archive.org/web/20170805165228/http://raywoodcockslatest.blogspot.com/2010/05/tweaking-ubuntu-1004.html">That process</a> may have <a href="https://web.archive.org/web/20170805165228/http://ubuntuforums.org/showpost.php?s=db5a0cae882b49f1d9f268f55ca4a223&amp;p=5306430&amp;postcount=18">caused a problem</a> for VMware Workstation 7.  When I tried to resume a previously suspended virtual machine, I got this error:<br/>
<blockquote>Could not open /dev/vmmon:  No such file or directory.  Please make sure that the kernel module `vmmon’ is loaded.</blockquote><a href="https://web.archive.org/web/20170805165228/http://blog.solutionperspectivemedia.co.uk/?p=6">One source</a> recommended adding some extra lines to the VMware startup script.  I killed VMware and tried that.  I typed “sudo gedit /etc./init.d/vmware and added those lines at the start of that file, right after the end of the introductory comments.  But it didn’t work, and I wasn’t surprised; the code seemed a bit scrambled.  I closed Workstation and tried “sudo vmware.”  But that didn’t help either.  What did finally solve the problem was <a href="https://web.archive.org/web/20170805165228/http://www.uluga.ubuntuforums.org/showpost.php?p=9207863&amp;postcount=2">a simple command</a>:  “sudo service vmware start.”  Then I started VMware and was able to restore my virtual machine OK.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Thanks that worked for me.HP DV7 Ubuntu 10.04 Lucyd X64 running Vmware 8

**Anonymous**:
Thanks, it worked for me too. Running VMWare Workstation 8 x64 on Linux Ubuntu Server 11.10.But is there a way to execute this command automatically when starting VMWare from the menu?

**Anonymous**:
thanks.. that's so helpfulllllli'm on lmde

**Anonymous**:
thanks, so simple but so time saving ;) take care


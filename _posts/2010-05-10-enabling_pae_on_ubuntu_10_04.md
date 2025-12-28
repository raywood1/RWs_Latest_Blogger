---
layout: post
title: "Enabling PAE on Ubuntu 10.04"
date: 2010-05-10
---

<div class="post-body">
<p>I had written <a href="https://web.archive.org/web/20190906053706/http://raywoodcockslatest.blogspot.com/2010/05/ubuntu-1004-adjustments-software-source.html">a string of posts</a> on the process of installing and tweaking Ubuntu 10.04 (Lucid Lynx).  As part of that effort, I wrote a post on using a PAE-enabled kernel, which would permit 32-bit Ubuntu 9.10 to access more than 3GB - 4GB of RAM.  Unfortunately, that post somehow got vaporized.  This post provides the steps needed to use PAE in Ubuntu 10.04.<br/>
<div style="font-family: 'Times New Roman'; font-size: medium; margin-bottom: 0px; margin-left: 0px; margin-right: 0px; margin-top: 0px;"><br/>
</div>I found an <a href="https://web.archive.org/web/20190906053706/https://help.ubuntu.com/community/EnablingPAE">Ubuntu community webpage</a> that said that, in Lucid, the CD and DVD installers would automatically install the PAE-enabled kernel.  I had installed 10.04 using Update Manager, however, and I was not seeing the PAE kernel listed in the GRUB boot menu when I started the system.  Following the advice on the community webpage regarding how to install PAE manually, I went to System &gt; Administration &gt; Synaptic Package Manager and searched for PAE.  This showed me that, sure enough, the packages named in the community webpage (i.e., linux-generic-pae and linux-headers-generic-pae) were not installed.  When I marked those two for installation, they automatically brought along some others.<br/>
<div style="font-family: 'Times New Roman'; font-size: medium; margin-bottom: 0px; margin-left: 0px; margin-right: 0px; margin-top: 0px;"><br/>
</div>After Synaptic downloaded and installed those packages, I rebooted the system.  I didn't notice what the BIOS and GRUB said when it rebooted, so when Ubuntu was back up, I typed "uname -r" in Terminal.  It said 2.6.32-22-generic-pae.  So it appeared the PAE updated had been successful.  I typed "free -m" to see how much RAM I had.  It saw a total of 8068 (i.e., 8GB).  So it had worked:  the PAE kernel was recognizing more than 4GB of RAM.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Sandra**:
Dear Ray,I just upgraded my computer to use ubuntu 10.04, since having it on 8.04 with PAE didn't help my memory problem. I have 4 GB of physical memory, and the OS has always seen 3.2 GB.I saw your instructions, and it turned out that in my 10.04 installation, PAE was enabled. I still see 3.2 GB of memory. Any ideas on why this would be the case? Any help you could provide will be greatly appreciated. Thanks!

**raywood**:
Not sure.  I Googled for this:pae 10.04 OR lucid 3.2GB -2009 -2008 -2007 -2006 -2005 -2004 -2003 -intitle:torrentOne of the hits said to check your BIOS.  There may be a limit in there.Good luck!

**Sandra**:
Hi, Ray! I just checked what the BIOS says, and it just says I have 4096 MB of memory... When I type free -m I get the following:total       used       free     shared    buffers     cachedMem:          3275       2103       1171          0        744        793-/+ buffers/cache:        565       2709Swap:        15257          0      15257Sandra.

**raywood**:
When your machine is booting, hit Del or whatever key it says to adjust your BIOS settings.  May have to research the right one for your machine.  See if there's a memory limit setting in there.

**Dan**:
Do you perhaps have an integrated graphics card installed that uses some of your 4GB Ram? I have a laptop where that is the case, i.e. that 4GB show in Ubuntu as 3.2GB only.Also, can you perhaps install additional 2-4GB and see if free -m now shows more than 4GB total Ram? Then you can tell for sure whether it works or not.BTW, my 9.10 always showed 12GB, without any modification after installation, I assume the new 10.04 will too, once I finally upgrade.

**raywood**:
Dan -- I think the deal with the 3.2GB is that that's all that a 32-bit operating system will ordinarily recognize, even if you do have 4GB.The PAE did make a difference.  When I am using VMware, I have several GB more, now, available for virtual machines.  So it's not just what's being reported on bootup; that extra RAM is actually working for me.

**Jorg**:
@Sandra: It might be that your machine's motherboard doesn't support more than 4GB memory address space. I have that problem with my Latitude D620. The memory address space is used to address all hardware in your system, incl. graphics, etc. So if 4GB is the physical hardware limit, you will only have ca. 3.2GB available for RAM. Check the specs of your motherboard. (I have 64bit ubuntu, separate graphics, and still only 3.2GB of my 4GB RAM available for that reason)


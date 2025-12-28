---
layout: post
title: "WinXP Error:  Invalid UI Language Registration List"
date: 2009-01-09
---

<div class="post-body">
<p>I got this error inside a VMware virtual machine (VM), running Windows XP Pro in VMware Workstation 6.5.0 on Ubuntu Hardy Heron 8.04:
<blockquote>Registry Corrupt

The UI Language registration list is invalid.</blockquote>This registry corruption was not detected and fixed by either System File Checker (Start &gt; Run &gt; sfc /scannow) or Advanced WindowsCare.  Clicking OK on the dialog also did not end it; it just came back with the same message.  Rebooting did not remove it:  it came back when I went into WinXP's <a href="https://web.archive.org/web/20170405170223/http://support.microsoft.com/kb/308423">Disk Management</a> and right-clicked on my C drive.   <a href="https://web.archive.org/web/20170405170223/http://www.google.com/search?q=%22registry+corrupt%22+%22windows+xp%22+OR+winxp+%22ui+language+registration%22&amp;sourceid=navclient-ff&amp;ie=UTF-8&amp;rlz=1B3GGGL_enUS293US308">A Google search</a> suggested that this was probably due to my recent installation of Corel WordPerfect Office X4.  That seemed likely; it wasn't happening in any other VM, and this was the only VM in which I had installed Corel Office.  It was apparently related specifically to CorelDraw, which was odd because I hadn't even installed that part of Corel Office.  The solution, according to <a href="https://web.archive.org/web/20170405170223/http://coreldraw.com/forums/p/1748/6342.aspx">one post</a>, was as follows:
<blockquote>Open the c:\Programs\Corel\CorelDRAW Graphis Suite setup files\CGS13 directory and look for the EN.msi file. Double click on this installs the language pack and then all is sweet.</blockquote>In my case, a search indicated that the EN.msi file was in two locations:

C:\Program Files\Corel\WordPerfect Office X4\Setup\WPO14
and
C:\Program Files\Corel\WordPerfect Office X4\Setup\WPO14\Lightning

I went into the first one, double-clicked on EN.msi, and the Windows Installer fired up.  It said "Preparing to install ..." and then, "Please wait while Windows configures WordPerfect Office X4 - EN."  Then it said, "1: EN.msi: This installation cannot be run by directly launching the MSI package.  You must run setup.exe."  So, OK, I found setup.exe (which would have been on the installation CD, but this was a downloaded version so I had to look in the installation files), ran it, and chose the Repair option.  I got an error message:
<blockquote>WordPerfect Office X4

The system cannot find the file specified.

c:\program files\corel\wordperfect office x4\setup\ica_en.msi</blockquote>That seemed relevant.  I clicked OK (the only option) and allowed the repair to complete.  The ending message said, "Your system has not been modified" and "The system cannot find the file specified."  So I ran setup.exe again, and this time I selected Remove.  Meanwhile, I found <a href="https://web.archive.org/web/20170405170223/http://www.sawmillcreek.org/showthread.php?t=34763">another post</a> that identified the problem as being caused by installing a version of Corel on a machine where another version had been previously installed; but that wasn't the case in this virtual machine, where I had not installed any version of Corel previously.  Anyway, after removing Corel, I rebooted the virtual machine.  When it came back, I ran Advanced WindowsCare (now called <a href="https://web.archive.org/web/20170405170223/http://www.iobit.com/advancedwindowscareper.html">Advanced SystemCare Free</a>), which had a registry fix feature that, I hoped, would eliminate any traces of Corel (since that was what others had said they had needed to do, in order to resolve this problem).  (I didn't run the Startup Manage and Privacy Sweep options.)  I re-ran AWC until there were no more errors, and then tried running Disk Management again.  This time it ran OK.  I noticed that my virtual machine was running out of virtual disk space, so I shut it down and used VMware to expand it, thinking that maybe this was why it had not installed correctly.  To do the resizing, I went to <a href="https://web.archive.org/web/20170405170223/http://raywoodcockslatest.blogspot.com/2008/08/vmware-in-ubuntu-settling-in.html">my previous (very long) post</a> on the process, searched that webpage for "resize," and followed the procedure described there.

When I was finally back in the (now enlarged) VM, I reinstalled Corel and rebooted.  Disk Management gave me no more problems.  Apparently I got the installation problem because I didn't have enough disk space available, and making more space available resolved it.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Roka**:
thanxxxxxxxxxxxxxxxxxxxxxxxxxxx

**Mitch**:
That is exactly what I did up to the virtual memory bit.  I have never had a problem with my virtual memory, but will try and see what happens.  I will let you know one way or the other. Mitch

**Mitch**:
it didn't work for me, any ideas

**Mitch**:
the virtual memory bit didn't work for me.  Any other ideas?

**raywood**:
Mitch -- thnaks for asking.  I'm pretty rusty on this.  Haven't been working in WinXP for a while.  But in case anyone else comes across this post and has the same problem, let me summarize what I think was going on.  I was working in a WinXP virtual machine in VMware Workstation on Ubuntu.  In other words, my real operating system was Ubuntu Linux, but VMware was making it possible for me to have an imitation computer, running inside Ubuntu, and that virtual machine was giving me a working copy of Windows XP.  So the problem as described here was that my virtual machine wasn't big enough.  Windows XP was running out of space.  Or at least the Corel software was.  For some reason, enlarging the virtual machine solved that problem.  I'm not sure what the solution would be for a person who's not working in a virtual machine, but maybe a memory manager program would make a difference.  I'm usingRizone Memory Booster.  It seems to help.  Or at least it makes me feel better.  Anyway, good luck!


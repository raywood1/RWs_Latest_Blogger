---
layout: post
title: "Windows XP Boots But Won't Run Programs"
date: 2007-10-20
---

<div class="post-body">
<p>A new hassle on the seemingly endless road to getting a working XP system!

I replaced the motherboard.  The new one was a <a href="https://web.archive.org/web/20190906053844/http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ProductID=2416">Gigabyte GA-M61P-S3</a>.  It was a technological step backwards from <a href="https://web.archive.org/web/20190906053844/http://raywoodcockslatest.blogspot.com/2007/08/msi-p6n-sli-platinum-motherboard.html">the MSI mobo</a> I had installed previously, but it seemed much more stable for practical purposes.  But it seemed that I would still have to deal with some new issues in the hardware and/or software of the revised system.

One such problem:  WinXP would boot up and run programs in Safe Mode, and it would also boot up in Normal Mode, but it would not actually run programs in Normal Mode.  It was not even completing its bootup sequence:  programs in the Startup folder were not running.

I assumed the problem was that I had installed some program or driver that was not running right.  But which one?  I had installed a boatload of programs <a href="https://web.archive.org/web/20190906053844/http://raywoodcockslatest.blogspot.com/2007/10/installed-new-motherboard-dont-want-to.html">after installing the new motherboard</a>.  That is, I had had to reinstall WinXP and all programs from scratch.  I hadn't installed them one or two at a time; I had installed them by the dozens, in one fell swoop.  So I really had no idea which one might have been responsible.

It seemed that the problem must be related to startup.  So I rebooted into Safe Mode and temporarily renamed the C:\Documents and Settings\All Users\Start Menu\Programs\Startup folder to "Holding" instead.  But that didn't solve the problem, so when I was next back in Safe Mode, I renamed it back to Normal Startup.  While in Safe Mode, I ran Start &gt; Run &gt; MSCONFIG and, on the General tab, I selected Diagnostic Startup.  The system rebooted and went into Normal Mode without a problem.  I checked MSCONFIG again.  It had reverted to the Normal Mode setting after doing its one-time diagnostic startup.  So I tried rebooting again.  This time, Normal Mode ran OK.  It seemed that one bootup in Diagnostic Startup may have been enough to reset whatever was the problem.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

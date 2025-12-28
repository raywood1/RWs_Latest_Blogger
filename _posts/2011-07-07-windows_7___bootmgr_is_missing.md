---
layout: post
title: "Windows 7:  BOOTMGR Is Missing"
date: 2011-07-07
---

<div class="post-body">
<p>One time, upon rebooting the system, I got this message:<br/>
<blockquote>BOOTMGR is missing<br/>
Press Ctrl+Alt+Del to restart</blockquote>I rebooted from the Windows 7 DVD and went to the "Repair your computer" option.  It said "Searching for Windows installations."  Then it showed me the System Recovery Options dialog, listing "Windows 7 Ultimate (recovered)."<br/>
<br/>
But that's not what it showed me the first time.  The first time, it showed me nothing.  I read <a href="https://web.archive.org/web/20190906053818/http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/">somewhere</a> that somebody found that they needed to run the Repair Your Computer option a couple of times before it would work, so possibly that was what finally populated this dialog with a Windows 7 entry.  But what I think may have solved the problem was that I booted with an Ubuntu 10.10 Live CD, went into System &gt; Administration &gt; GParted, and used their filesystem repair option (or whatever it was called, exactly) on my Windows 7 partition.  (I'm <a href="//web.archive.org/web/20190906053818/https://www.google.com/search?rlz=1C1CHKZ_enUS439US439&amp;sourceid=chrome&amp;ie=UTF-8&amp;q=ubuntu#sclient=psy&amp;hl=en&amp;rlz=1C1CHKZ_enUS439US439&amp;source=hp&amp;q=ubuntu+gparted+%22live+cd%22&amp;pbx=1&amp;oq=ubuntu+gparted+%22live+cd%22&amp;aq=f&amp;aqi=g-v1g-j1&amp;aql=undefined&amp;gs_sm=e&amp;gs_upl=6621l9560l3l12l8l2l0l0l0l417l1786l2-4.1.1l6&amp;bav=on.2,or.r_gc.r_pw.&amp;fp=c9cd00fa582aeac9&amp;biw=1013&amp;bih=929">not sure</a> if GParted is included in more recent versions. If not, <a href="//web.archive.org/web/20190906053818/https://www.google.com/search?rlz=1C1CHKZ_enUS439US439&amp;sourceid=chrome&amp;ie=UTF-8&amp;q=ubuntu#sclient=psy&amp;hl=en&amp;rlz=1C1CHKZ_enUS439US439&amp;source=hp&amp;q=ubuntu+gparted+%22live+cd%22&amp;pbx=1&amp;oq=ubuntu+gparted+%22live+cd%22&amp;aq=f&amp;aqi=g-v1g-j1&amp;aql=undefined&amp;gs_sm=e&amp;gs_upl=6621l9560l3l12l8l2l0l0l0l417l1786l2-4.1.1l6&amp;bav=on.2,or.r_gc.r_pw.&amp;fp=c9cd00fa582aeac9&amp;biw=1013&amp;bih=929">the 10.04 version</a> will still be available for a while.)<br/>
<br/>
Anyway, I did now see Windows 7 Ultimate (recovered).  I clicked Next &gt; Startup Repair.  It said "Searching for problems" and then "Attempting repairs."  Then it said, "Restart your computer to complete the repairs."  I did that.  The problem was solved.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**aalia lyon**:
Awesome Article !!! you can get full solution of your problem .go through this link.BOOTMGR Missing in Windows 7Thank youAalia lyon


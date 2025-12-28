---
layout: post
title: "Windows 7 CHKDSK /R:  Corrupt MFT:  False Alarm"
date: 2011-12-07
---

<div class="post-body">
<p>I was using Windows 7.  I rebooted with the Windows 7 program DVD, went into the System Recovery Options, and selected Command Prompt.  At the prompt, I checked each partition on my drive with CHKDSK /R.<br/>
<br/>
There were five partitions.  For the first two, no problem.  On the third one, CHKDSK ran into problems partway through.  I don't remember the exact problem or wording, but as I recall it happened in the first of the five stages of partition checking.  It would give me an error message after getting partway through, and then quit.  I ran it again and noticed that it seemed to be progressing further through the partition, so I kept running it.  Once or twice, it seemed to regress, but I figured it was cleaning up something from the previous round.  Eventually it did complete the partition check.<br/>
<br/>
So I moved on to the fourth partition.  Now, however, I got an error message.  I didn't write it down, but according to the <a href="https://web.archive.org/web/20151205113857/http://www.techsupportforum.com/forums/f16/corrupt-master-file-table-462577.html" target="_blank">multiple</a> webpages <a href="https://web.archive.org/web/20151205113857/http://www.win7heads.com/repair-recovery/41414-corrupt-master-file-table.html" target="_blank">I consulted</a> for <a href="https://web.archive.org/web/20151205113857/http://forums.majorgeeks.com/showthread.php?t=241944" target="_blank">information</a> on how to <a href="https://web.archive.org/web/20151205113857/http://answers.microsoft.com/en-us/windows/forum/windows_7-system/corrupt-master-file-table-on-spare-hdd/8b0de31c-b49e-4ab2-8dbb-32c150350408" target="_blank">resolve</a> it, from <a href="https://web.archive.org/web/20151205113857/https://www.google.com/search?q=%22Windows+7%22+%22corrupt+master+file+table%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">a Google search</a>, the message was something like this:<br/>
<br/>
<blockquote>Corrupt master file table. Windows will attempt to recover master file table from disk.<br/>
<br/>
Windows cannot recover master file table. CHKDSK aborted.<br/>
<br/>
</blockquote>And it wasn't just on that one partition.  I was now getting that error message on every partition on that drive -- including the ones that had just passed CHKDSK with no problems -- but I wasn't getting any such message on the other drive that I had in that computer.<br/>
<br/>
If I hadn't made a backup just before running CHKDSK, the suggested solution would apparently have been to try recovering my data with something like <a href="https://web.archive.org/web/20151205113857/http://www.cgsecurity.org/wiki/TestDisk_Download" target="_blank">TestDisk</a>.  But before doing that, or wiping the drive and recreating my partitions and restoring the data from backup, I took a look with <a href="https://web.archive.org/web/20151205113857/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=nQ8&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Gparted&amp;oq=Gparted&amp;aq=f&amp;aqi=g5g-c1g4&amp;aql=&amp;gs_sm=e&amp;gs_upl=9611l9611l0l10003l1l1l0l0l0l0l209l209l2-1l1l0" target="_blank">GParted</a>, which I usually ran by booting from an <a href="https://web.archive.org/web/20151205113857/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=O7S&amp;tbo=1&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;biw=1036&amp;bih=878&amp;tbs=qdr%3Am&amp;q=Ubuntu+Gparted+%22live+CD%22&amp;oq=Ubuntu+Gparted+%22live+CD%22&amp;aq=f&amp;aqi=g1g-v3&amp;aql=&amp;gs_sm=se&amp;gs_upl=7913l9293l0l9544l10l8l0l0l0l0l214l940l3.1.3l7l0" target="_blank">Ubuntu live CD</a>.  It didn't see any problems.  I rebooted with the Windows 7 CD and ran CHKDSK /R again.  Now it didn't see any problems either, on any of the five partitions.  So wiping the drive and recovering or restoring data would apparently have been unnecessary.  I wondered whether the process of retrying multiple times (or the condition that made it necessary to retry) on that third partition had somehow confused CHKDSK or my drive.<br/>
<br/>
I hadn't experienced this before.  Possibly it was something unusual about my Windows 7 DVD, or about that particular bootup.  Another possibility was that maybe I should not have been running two separate sessions of CHKDSK at the same time.  That is, the System Recovery Options dialog would let me keep clicking on the Command Prompt option to open additional windows.  (I used Alt-Tab to switch between them.)  So I was running CHKDSK /R in each of two separate command windows.  I had one session working on the partitions on the first drive, and the other session working on the partitions on the second drive.  I figured they were independent of each other.  I had done this before without a problem, but only once or twice.  This time, the problem had emerged only in the second command window.<br/>
<br/>
Was that the cause of the problem?  It seemed that I'd have to wait until the next time I ran CHKDSK /R to see if I got the same issue again.  At present, the solution seemed to be that, if I got that weird crashing in the first stage of disk checking, or if a partition that had just passed CHKDSK was now being reported as corrupt, I should just reboot and take another look, using either GParted or the Windows 7 DVD.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

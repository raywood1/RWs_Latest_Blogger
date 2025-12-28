---
layout: post
title: "Windows 7:  BSOD:  PROCEXP111.SYS"
date: 2012-03-21
---

<div class="post-body">
<p>My computer was sailing along, when suddenly I got a Blue Screen of Death (BSOD).  The message began, oddly, with a sentence fragment:<br/>
<blockquote>to your computer.<br/>
<br/>
PROCEXP111.SYS<br/>
<br/>
PAGE_FAULT_IN_NONPAGED_AREA<br/>
<br/>
If this is the first time you've seen this Stop error screen, restart your computer.  If this screen appears again, follow these steps:<br/>
<br/>
Check to make sure any new hardware or software is properly installed.  If this is a new installation, ask your hardware or software manufacturer for any Windows updates you might need.<br/>
<br/>
If problems continue, disable or remove any newly installed hardware or software.  Disable BIOS memory options such as caching or shadowing.  If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode.<br/>
<br/>
Technical information:<br/>
<br/>
*** STOP: 0x00000050 (0xFFFFFA8100043F20, 0x0000000000000000, 0xFFFFF880073B6DDD,0x0000000000000000)<br/>
<br/>
*** PROCEXP111.SYS - Address FFFFF880073B6DDD base at FFFFF880073B5000, DateStamp 47194089<br/>
<br/>
Collecting data for crash dump ...<br/>
Initializing disk for crash dump ...<br/>
Physical memory dump complete.<br/>
Contact your system admin or technical support group for further assistance.</blockquote>I probably didn't need to type out all that information, but doing so provided a constructive outlet for frustration.  Besides, you never know what archaeologists of some future civilization will find absolutely crucial for understanding what they are digging out of the rocks.<br/>
<br/>
This was the second time I'd gotten this BSOD, so evidently it was not going to be good enough to simply reboot and hope for the best.  To respond to the BSOD's first bit of advice, there wasn't any new hardware or software.  On the software side, I had recently restored a backup image of drive C that I had made more than a month earlier.  The first BSOD had occurred within the past few days, prior to the restoration.  In other words, I was suddenly getting BSODs on an install that had worked fairly well for weeks, with and also without software changes made during those weeks.<br/>
<br/>
I did notice something atypical on the hardware side.  I had two different USB external drives connected.  That, itself, was not unusual, though it had not happened often.  The unusual part was that the system would not reboot without one of them being turned off.  It would get as far as giving me a message, which I think was "Loading Operating System," and then it would pause until I shut one of those USB drives off.<br/>
<br/>
I wasn't actually doing anything in particular on the computer when the BSOD happened.  They had been up all night; I had just returned to the system in the morning; and at the moment I wasn't even using that computer; I was working on the other machine.  By the time I got to writing these notes, I didn't recall if I had even done anything on that computer.  Not much, anyway; nothing that would seem to have provoked the crash.<br/>
<br/>
As I worked through this issue, I was guided by two posts I had written up a few months earlier, regarding a different STOP error.  <a href="https://web.archive.org/web/20151125203932/http://raywoodcockslatest.blogspot.com/2012/01/windows-7-bsod-memory-dump.html" target="_blank">One</a> was a closer look at the "memory dump" concept mentioned toward the bottom of the BSOD; <a href="https://web.archive.org/web/20151125203932/http://raywoodcockslatest.blogspot.com/2012/01/windows-7-stdriver64sys-bsod.html" target="_blank">the other</a> was a more general-purpose review of possibilities.  The memory dump investigation came to mind at this point because, on reboot, Windows 7 gave me a dialog that said, "Windows has recovered from an unexpected shutdown.  Windows can check online for a solution to the problem."  I hadn't always gotten this dialog after a crash.  It dimly seemed that something I had changed about my system, during the process of working through the prior memory dump post, had given me this information; otherwise I had to use something like <a href="https://web.archive.org/web/20151125203932/https://www.google.com/search?q=Bluescreenview+Nirsoft&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">BlueScreenView</a> to see it.  The dialog gave me an option, "View problem details."  I took that option and got some technical information that I wasn't eager to read.  It pointed me toward two "Files that help describe the problem."  I copied the addresses of those files (without the actual filename), pasted them into the address bar in Windows Explorer, and looked at them.  One was an XML file that, if I just double-clicked on it (or if I pasted the full path and filename in Windows Explorer), would open as code in Internet Explorer.  This file was arguably more readable in Firefox, but I didn't see anything particularly informative in it.  The other was a minidump file that I opened in BlueScreenView.  (In Notepad, it was semi-gibberish.)  Problem is, I hadn't fared too well in interpreting the page dump, last time around, and that was still the case this time.  Following that previous guidance, I did notice that this day's minidump, and also the one from the previous BSOD, did contain lines referring specifically to PROCEXP111.SYS, named in the BSOD.  But, as before, I didn't know what else, if anything, I could do with the memory dump information.<br/>
<br/>
Two other things worth noting about this crash.  First, after the crash, Glary Registry Repair found an unusually large number of registry errors.  Since I ran Glary every day, I suspected these were a result, not a cause, of the crash.  Second, in recent days the system had been functioning extremely slowly.  This seemed to depend on the number of programs running, but not entirely.  In particular, I was having the <a href="https://web.archive.org/web/20151125203932/http://raywoodcockslatest.blogspot.com/2012/03/windows-7-assigning-process-priorities.html" target="_blank">previously noted</a> slowdowns that I had attributed to resource-hog programs (especially GoodSync and BeyondCompare).  Sometimes I noticed that, when those programs were out of the picture, the system sped up considerably; at other times, there seemed to be a lingering effect where the system continued to seem screwed up.  This was what had prompted me to do the system restore.  In that previous post, I mentioned trying Process Hacker to put a speed limit on these resource-intensive programs; but I also noted that this had not seemed to make much difference.  I wasn't sure that there was anything particularly wrong about the Windows 7 installation as a whole, and certainly wasn't eager to reinstall from scratch.<br/>
<br/>
<a href="https://web.archive.org/web/20151125203932/https://www.google.com/search?q=PROCEXP111.SYS&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> led to <a href="https://web.archive.org/web/20151125203932/http://www.runscanner.net/lib/PROCEXP111.sys.html" target="_blank">the information</a> -- surprising to me, but obvious once stated -- that PROCEXP111.SYS was related to Sysinternals <a href="https://web.archive.org/web/20151125203932/http://4sysops.com/archives/sysinternals-process-explorer-a-better-task-manager/" target="_blank">Process Explorer</a>.  I had <a href="https://web.archive.org/web/20151125203932/http://raywoodcockslatest.blogspot.com/2012/03/windows-7-assigning-process-priorities.html" target="_blank">just begun using</a> Process Explorer, after several weeks of using Process Hacker, to <a href="https://web.archive.org/web/20151125203932/http://raywoodcockslatest.blogspot.com/2012/03/windows-7-assigning-process-priorities.html" target="_blank">control certain programs</a> -- especially GoodSync -- that made excessive resource demands, to the point of making the computer unusable while they were running.  I hadn't noticed specifically whether the previous BSOD named PROCEXP111.SYS as the culprit; but since it had occurred just one day earlier, probably PROCEXP111.SYS was named in that one too.  I probably could have figured this out from the minidump, with sufficient time investment.<br/>
<br/>
I wasn't sure how to interpret this information.  Generally, Microsoft Sysinternals tools like Process Explorer had seemed relatively stable.  It seemed possible that the crash named PROCEXP111.SYS because, unlike Process Hacker, Process Explorer was actually succeeding in putting the brakes on some overly grabby programs, and they didn't like it.  That is, it may have been a problem with Process Explorer, but it may instead have been a problem with these other programs -- that, basically, they would either run at their preferred speed or not at all.<br/>
<br/>
I tried <a href="https://web.archive.org/web/20151125203932/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=PROCEXP111.SYS+OR+%22Process+Explorer%22+BSOD+Vista+OR+%22Windows+7%22&amp;oq=PROCEXP111.SYS+OR+%22Process+Explorer%22+BSOD+Vista+OR+%22Windows+7%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=173l274l0l898l3l2l0l0l0l0l392l639l2-1.1l2l0&amp;gs_l=serp.3...173l274l0l898l3l2l0l0l0l0l392l639l2-1j1l2l0.frgbld." target="_blank">another search</a>.  This led to <a href="https://web.archive.org/web/20151125203932/http://forum.sysinternals.com/process-explorer-bsod_topic21756.html" target="_blank">the suggestion</a> that I should be using a more recent version.  I hadn't checked, but now I saw that mine was v. 11.04, copyright 2007.  Oops.  Upon closer examination, I saw that they were now up to <a href="https://web.archive.org/web/20151125203932/http://technet.microsoft.com/en-gb/sysinternals/bb896653.aspx" target="_blank">v. 15.13</a>.  I downloaded and installed the upgrade.  I wasn't sure how long it might be until the next BSOD due to Process Explorer, so I decided to close this post at this point.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
As of a couple weeks later, it appeared that Process Explorer was indeed the culprit.  I had stopped using it, and had not experienced a recurrence of this particular BSOD.  I did haveother BSODs, though.


---
layout: post
title: "Windows 7:  Windows Explorer:  CDs and DVDs:  Files Ready to Be Written to the Disc"
date: 2011-03-25
---

<div class="post-body">
<p>When loading a program DVD, I noticed that Windows Explorer showed its files in two groups:  "Files Currently on the Disc" and "Files Ready to Be Written to the Disc."  This wasn't a DVD/RW disc, so this grouping didn't make sense.  I wanted to get rid of it.  I ran <a href="https://web.archive.org/web/20190513231615/http://www.google.com/search?q=%22Files+ready+to+be+written+to+the+disk%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;as_qdr=all&amp;num=50&amp;cad=h">a search</a> and got <a href="https://web.archive.org/web/20190513231615/http://www.sevenforums.com/tutorials/654-you-have-files-waiting-burned-disc-stop-message.html">advice</a> to paste this address into the address bar in Windows Explorer:<br/>
<blockquote>%userprofile%\AppData\Local\Microsoft\Windows\Burn\Temporary Burn Folder</blockquote>and, there, to delete all contents from the Temporary Burn Folder (but not the folder itself). That solved half the problem:  the "Files Ready" group was gone, but I still had "Files Currently on the Disc."  I ran <a href="https://web.archive.org/web/20190513231615/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=Vs6&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Files+Currently+on+the+Disc%22+%22Windows+7%22+%22Windows+Explorer%22&amp;aq=f&amp;aqi=&amp;aql=&amp;oq=">another search</a> and found <a href="https://web.archive.org/web/20190513231615/http://www.techrepublic.com/forum/questions/101-322764">a webpage</a> leading to <a href="https://web.archive.org/web/20190513231615/http://www.howtogeek.com/howto/windows-vista/disable-windows-vistas-built-in-cddvd-burning-features/">a How-To Geek page</a> that said this was a result of having Windows 7 built-in (as distinct from e.g., Nero third-party) DVD burning enabled.  To disable the built-in burning, I downloaded their registry hack for Vista and verified in regedit that it added the desired value to the Win7 registry.  I checked in Windows Explorer.  The Files Currently on the Disc message was still there.  I rebooted.  On reboot, I got an error:<br/>
<blockquote>explorer.exe<br/>
The parameter is incorrect</blockquote>I wasn't sure if this resulted from the registry edit.  The Files Currently on Disc message was no longer there when I selected the DVD drive (with a disc in the drive) in Windows Explorer.  The original problem seemed to be fixed.  Glary Registry Repair did not identify the registry tweak as a problem.  I went ahead and added it to my all-purpose <a href="https://web.archive.org/web/20190513231615/http://raywoodcockslatest.blogspot.com/2011/01/windows-7-installation-win7regeditreg.html">Win7RegEdit.reg registry tweak file</a> that I would run when installing Windows 7.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

---
layout: post
title: "Windows 7:  "Access Denied" on the Command Line When Using FIND"
date: 2012-03-09
---

<div class="post-body">
<p>I tried to run a FIND command in the CMD (sometimes called the DOS) box in Windows 7.  I got an error message:<br/>
<blockquote class="tr_bq">Access Denied - D:\FOLDER\SUB FOLDER</blockquote>This was bizarre.  I had been using the command line in this Win7 installation for months.  Well, something had apparently changed.  I got this message regardless of whether I used my pre-installed "<a href="https://web.archive.org/web/20150720010651/http://raywoodcockslatest.blogspot.com/2012/01/windows-7-batch-printing-html-mht-files.html" target="_blank">Open Command Window Here</a>" right-click option in Windows Explorer or the <a href="https://web.archive.org/web/20150720010651/http://raywoodcockslatest.blogspot.com/2011/12/windows-7-tweaked-installation-latest.html" target="_blank">Administrator Command Box</a> option I had created in the Start menu.<br/>
<br/>
<a href="https://web.archive.org/web/20150720010651/https://www.google.com/search?q=%22Windows+7%22+command+%22Access+Denied%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> led me through various <a href="https://web.archive.org/web/20150720010651/http://www.addictivetips.com/windows-tips/windows-7-access-denied-permission-ownership/" target="_blank">possible solutions</a>.  I tried especially to tweak the permissions for the entire partition and for the individual folder via right-click &gt; Properties &gt; Security tab &gt; Advanced &gt; Owner tab &gt; Edit &gt; select Administrators and check "Replace owner on subcontainers and objects," and to play with other tabs and settings in that vicinity.<br/>
<br/>
<a href="https://web.archive.org/web/20150720010651/http://think-like-a-computer.com/2011/05/11/windows-access-denied-folder-administrator/" target="_blank">One option</a> I hadn't seen previously was to open the Local Group Policy Editor (Start &gt; Run &gt; gpedit.msc) and go into <a href="https://web.archive.org/web/20150720010651/http://technet.microsoft.com/en-us/library/cc736413%28v=ws.10%29.aspx" target="_blank">Computer Configuration</a> &gt; Windows Settings &gt; Security Settings &gt; Local Policies &gt; Security Options &gt; right-click on "User Account Control:  Behavior of the elevation prompt for administrators in Admin Approval Mode" &gt; Properties &gt; Elevate Without Prompting.  But I already had that selected.<br/>
<br/>
That writeup raised the question, though:  had I not completely <a href="https://web.archive.org/web/20150720010651/https://www.google.com/search?q=%22Windows+7%22+%22disable+UAC%22+OR+%22disable+User+Account+Control%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">disabled User Account Control</a> (UAC)?  <a href="https://web.archive.org/web/20150720010651/http://www.mydigitallife.info/how-to-disable-and-turn-off-uac-in-windows-7/" target="_blank">As advised</a>, I went into Start &gt; Run &gt; Regedit and navigated to HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\System.  There, I right-clicked on EnableLUA and verified that the value was zero.  Nonetheless, I exported the tweak, extracted the relevant lines from the REG file, and added them to my <a href="https://web.archive.org/web/20150720010651/http://raywoodcockslatest.blogspot.com/2011/11/win7regeditreg-updated.html" target="_blank">Win7RegEdit.reg</a> file for future installations, just to be sure.<br/>
<br/>
When I was in Permissions (via Windows Explorer folder right-click &gt; Properties &gt; Security tab &gt; Edit), I noticed that the permissions checkboxes were checked but greyed out.  I couldn't change them.  Was I somehow not in the right account?  <a href="https://web.archive.org/web/20150720010651/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=A65&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Windows+7%22+permissions+grey+OR+gray+security&amp;oq=%22Windows+7%22+permissions+grey+OR+gray+security&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=312214l313136l0l313970l9l7l0l0l0l0l290l1380l1.3.3l7l0&amp;gs_l=serp.3...312214l313136l0l313970l9l7l0l0l0l0l290l1380l1j3j3l7l0" target="_blank">A search</a> led to <a href="https://web.archive.org/web/20150720010651/http://windows7forums.com/windows-7-support/72366-windows-7-security-settings-permissions-issues.html" target="_blank">a proffered batch</a> file (<a href="https://web.archive.org/web/20150720010651/http://windows7forums.com/windows-7-support/72366-windows-7-security-settings-permissions-issues.html" target="_blank">Permissions.zip</a>) that read as follows:<br/>
<blockquote>@echo off<br/>
title File/Folder Permissions <br/>
echo.<br/>
echo.             BY KAOS - Windows 7 Forums<br/>
echo.<br/>
echo.<br/>
set /p a=Enter Path Of File/Folder:<br/>
echo.<br/>
set /p b=User Name:<br/>
echo Type "deny" = remove access OR type "grant" = allow full access<br/>
set /p c=Permission Type:<br/>
echo.<br/>
echo.<br/>
echo.<br/>
if %c%==deny goto lock<br/>
if %c%==grant goto unlock<br/>
if %a%==menu goto start2<br/>
if %b%==menu goto start2<br/>
if %c%==menu goto start2<br/>
:lock<br/>
cacls %a% /e /d %b%<br/>
cls<br/>
exit<br/>
:unlock<br/>
cacls %a% /e /g %b%:f<br/>
cls</blockquote>The gist of this batch file seemed to be that I could try <a href="https://web.archive.org/web/20150720010651/http://technet.microsoft.com/en-us/library/bb490872.aspx" target="_blank">a CACLS command</a> of this form:  cacls [folder path] /e /g [username]:f, where /e meant "edit," /g specified the user, and :f gave full control.  So, in my case, what username would I use?  Control Panel &gt; User Accounts said that I had <a href="https://web.archive.org/web/20150720010651/http://raywoodcockslatest.blogspot.com/2011/12/windows-7-tweaked-installation-latest.html" target="_blank">set up my system</a> so that the only options were Ray (Administrator) and Guest (turned off).  Maybe this was the problem:  I had been thinking in terms of the Administrator account rather than the Ray account.  So, OK, I tried typing this on the command line, to grant full control to the whole drive:<br/>
<blockquote>cacls D:\ /e /g Ray:f</blockquote>In response to that command, I got a short message:  "processed dir: D:\.  Did that mean champagne?  I retried the command that had given me the "Access Denied" error.  No, still denied.  Alright, how about same command, different user:  Administrator.  Same output.  Still denied.  Baffling!<br/>
<br/>
I ran across <a href="https://web.archive.org/web/20150720010651/http://discussions.virtualdr.com/showthread.php?t=137879" target="_blank">a post</a> that said something about turning off simple file sharing and permissions, and then permissions.  It raised a question:  was there a way to reset permissions to the default, and start over?  For the drive (i.e., right-clicking on D: in Windows Explorer), I went into Share with &gt; Advanced sharing &gt; Sharing tab &gt; Advanced Sharing.  I unclicked Share This Folder &gt; Apply.  I got a note indicating that I had some files currently opened, and they would be closed.  I clicked Yes &gt; OK &gt; Close.  This, in itself, didn't have any effect on another try of the FIND command; still denied.  <br/>
<br/>
I had recently gotten an indication that the Recycle Bin on drive D was corrupted.  I had said go ahead and empty it.  That message had recurred.  I had also been getting bothersome messages when I tried to move or delete folders, telling me that these folders were shared and confirming that I really wanted to do what I had said I wanted to do.  It seemed that these problems might be related.  But how, and what could I do about it?<br/>
<br/>
I found <a href="https://web.archive.org/web/20150720010651/http://www.techrepublic.com/article/techrepublic-tutorial-establish-the-correct-file-sharing-permissions-in-windows-xp/1056018" target="_blank">a Windows XP article</a> from 2002 that said, "If you don't have a thorough understanding of the various permissions and their relationships, it can be nearly impossible to sort out a permission problem and find a solution."  So I could see how Windows 7 was a direct descendant from Windows XP:  both could make it impossible to get any work done.  The article said that there was a difference between sharing permissions and NTFS permissions, and that the more restrictive one wins.  So if I wanted to grant full control to everyone for everything, I had to do that in two different right-click &gt; Properties tabs:  the Sharing tab and also the Security tab.  But it really looked like I had done that, over and over again.<br/>
<br/>
Ah, but now I saw a new problem.  In the Security tab, I saw that I had a little red circle with an X in it, next to the Administrator group.  There was no right-click option to explain it.  I guessed that the problem was that I had entered the wrong CACLS command, regarding Administrator rather than Administrators (plural).  So that was interesting.  I clicked on Edit, selected Administrator, and clicked Remove.  Then I re-ran that CACLS command with a reference to Administrators, this time, instead of Administrator.  But still no joy on my FIND command:  Access denied.<br/>
<br/>
So anyway, as I was saying, it did seem that I had given full control to almost everyone listed in the Security tab.  I mean, literally, Everyone:  I had an entry for them, and they had full control, and so did SYSTEM, Ray, and Administrators.  But not Authenticated Users, and not plain old Users.  Who the hell were all these people, anyway, and why did we all need to have so many kinds of access to my computer so that I could get work done?  (Sigh.)  Wiser minds knew; I did not.  Anyway, I went ahead and gave full control to my whole world to everyone and his brother, Users and all.  And still the godforsaken command did not run.<br/>
<br/>
And, by the way, at this point I searched in vain for those greyed-out permissions boxes I had seen earlier.  Evidently I had altered something significant, in all this screwing around.  Not so significant as to actually let me get any work done, but significant certainly in the sense that I could no longer detect greyness when I searched therefor.  Not in the Security, nor back in the Sharing tab.  Speaking of which, I now saw that my reestablished share of drive D now had permissions only for Everyone.  Did Everyone include me and all the other Administrators and Users and Authenticated Users of my home system (I was living alone), or did I need to add the whole gang back to my computer?  Not sure.<br/>
<br/>
It occurred to me that I did have a solution.  It was called System Restore.  But, alas, the mere fact of telling Windows to keep system restores, accompanied by weekly checking to make sure that the task was really running as scheduled, did not necessarily mean that I would actually have recourse to any system restore points, other than the one created that very morning.  Apparently Windows was not content with the 10GB of disk space I had set aside for this purpose.  Fortuitously, I did have an Acronis drive image from a week or so earlier, and so, without further ado, I wiped the drive and restored that.  Did there exist any further difficulty?  Yes, there did.  My Acronis backup was too recent.  Apparently this problem had lurked for days and/or was not only, or primarily, a matter of drive C (stored in Acronis) as distinct from drive D (not backed up in Acronis).<br/>
<br/>
I tried a different command that, I knew, I had run within recent days:  DIR.  It ran.  Now, why would DIR run and FIND not run?  FIND took a look inside files; were my permissions of some type not reaching into the files?  I right-clicked on the files in question.  They didn't have sharing or security options collectively; I had to click them one at a time to get a Security tab.  It said everyone had full control.  The Advanced &gt; Owner tab option said the owner of at least one file was Administrators.  Anyway, the CACLS command was supposed to take care of user accouint issues.<br/>
<br/>
I tried the same FIND command on another computer of virtually identical configuration.  It, too, provided a FIND error.  <a href="https://web.archive.org/web/20150720010651/https://www.google.com/search?q=FIND+command+%22access+denied%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> led to <a href="https://web.archive.org/web/20150720010651/http://serverfault.com/questions/146180/why-does-find-on-windows-7-give-an-access-denied-error" target="_blank">a brilliant insight</a>:  my command was wrong.  I was trying to use FIND on a directory, when it only works on files.  I had to make one change:  I had to add a star (asterisk) to the end of my search.  The FIND command worked without error when I did it this way:<br/>
<blockquote>find /i /c "X-Message-Delivery:" "D:\Folder\Sub Folder\*"</blockquote>Solution:  operator error.  Case closed.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
I wish I could hug you through the internet. I was having this exact problem and now you've fixed it.

**Anonymous**:
thank you!!

**Pauline**:
thank you!

**Anonymous**:
Thanks for the legwork! Appreciate it.

**Jan Kacina**:
Thanks a lot!

**Anonymous**:
Holy Crap... Thank you, Thank you, Thank you...

**Anonymous**:
Operator error indeed.  Kill me now - man, I'm stupid.


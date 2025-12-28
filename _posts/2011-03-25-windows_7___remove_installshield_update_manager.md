---
layout: post
title: "Windows 7:  Remove InstallShield Update Manager"
date: 2011-03-25
---

<div class="post-body">
<p>The InstallShield Update Manager (ISUM) had somehow installed itself on my system.  It would sometimes appear in my system tray, and would also pop up messages telling me that I needed to install updates.  I wanted it gone.<br/>
<br/>
I ran <a href="https://web.archive.org/web/20151102075723/http://www.google.com/search?q=%22installshield+update+manager%22+remove&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;as_qdr=all&amp;num=50&amp;cad=h">a search</a> and found <a href="https://web.archive.org/web/20151102075723/http://kb.flexerasoftware.com/selfservice/microsites/search.do?cmd=displayKC&amp;docType=kc&amp;externalId=Q111106&amp;sliceId=1&amp;docTypeID=DT_HOWTO_1_1&amp;dialogID=91533023&amp;stateId=0%200%2091525880">a Flexera Software webpage</a> that offered <a href="https://web.archive.org/web/20151102075723/http://support.installshield.com/kb/files/Q112918/SoftwareManagerUninstall.exe">a link</a> to a SoftwareManagerUninstall.exe program.  I ran that uninstaller and was greeted with a question:  "Are you sure you want to remove the FLEXnet Connect Software Manager?  Odd question; I hadn't installed any such thing.  Logically, though, it couldn't hurt, so I said sure, do it.  A moment later, it said the software manager had been removed from my system.  I was glad for that.  But the ISUM icon was still in my system tray, and when I double-clicked on it, it informed me that it was currently updating two important programs, namely, ON-OFF Charge B10.0427.1, which I had never heard of, and the InstallSheild Update Manager itself.  Marvelous.<br/>
<br/>
The idea seemed to be that there were different versions of the ISUM, depending on which program installed it on my system, which would explain why various sites pointing me toward specific registry entries didn't work for me -- and I couldn't just delete all references to InstallShield, because all kinds of programs used that as their installer.  I went into Control Panel &gt; Programs and Features to verify that, as I recalled, the InstallShield Update Manager was not listed there.  With the aid of <a href="https://web.archive.org/web/20151102075723/http://gadgetopia.com/post/3837">a thread</a>, I found that C:\Program Files\Common Files\InstallShield\UpdateService\ISUSPM.exe was the operative program -- running the Update Manager, I mean -- but somebody said that deleting that wouldn't solve the problem; it would just be reinstalled by the related registry entries at some point.  There was the option to set it not to check for updates, but somebody in that thread said it would then pop up to remind me that I had set it to not remind me.<br/>
<br/>
I ran <a href="https://web.archive.org/web/20151102075723/http://forums.v3.co.uk/showthread.php?t=215005">a better search</a> and got a suggestion to use <a href="https://web.archive.org/web/20151102075723/http://technet.microsoft.com/en-us/sysinternals/bb963902">Autoruns</a> instead of Start &gt; Run &gt; msconfig to identify ISUM as a starting program and untick it.  But before trying the Autoruns/msconfig route, I did a Ctrl-F in Start &gt; Run &gt; regedit for ISUSPM.exe.  This gave me the idea to delete the C:\Program Files\Common Files\InstallShield\UpdateService folder and then run <a href="https://web.archive.org/web/20151102075723/http://www.glarysoft.com/">Glary Registry Repair</a> to wipe out references to it.  Thanks to previous tweaks (see links above), I was already running as administrator with about as much freedom as I could persuade Win7 to give me, so I figured the only thing left to do, before I could delete that folder, would be to use my right-click <a href="https://web.archive.org/web/20151102075723/http://lockhunter.com/">Lockhunter</a> option to free it up in Windows Explorer.  That didn't work, though, so I tried deleting the contents of C:\Program Files\Common Files\InstallShield\UpdateService individually.  Everything went except issch.exe.  For that, I got an error:<br/>
<blockquote>File In Use<br/>
The action can't be completed because the file is open in InstallShield Update Service Scheduler.</blockquote>So I went into Task Manager (Ctrl-Alt-Del) &gt; Processes tab, highlighted issch.exe, and clicked End Process.  That took care of that.  (When I tried this on another machine, I also had to use Task Manager to shut down agent.exe, ISUSPM.exe, and one or two other processes.)  Then I closed Task Manager.  Now I could get rid of the folder.  I ran Glary.  I was watching one of the references to ISUSPM.exe in regedit, and it did not change when Glary was done, so I rebooted, ran Glary again, and did another search in regedit for ISUSPM.exe.  That reference was still there; so, maybe, were others.  I wasn't sure what to do about that, so I left it alone for a while.<br/>
<br/>
Nothing further emerged, so I left things as they were.  The InstallShield Update Manager seemed to be gone.  There was still an InstallShield Program Updates icon in Control Panel, though.  I got rid of that by going to C:\Windows\System32.  There, I clicked on the Type heading (in Windows Explorer) to sort by that field, scrolled down to the .cpl (Control panel item) files, and deleted ISUSPM.cpl.  The icon was still in Control Panel, but I thought maybe it would go away after a reboot.  That may have been correct.  When I checked a week later, it was gone.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Dhee**:
I hope it works I jus did it on vista

**jb**:
I've been trying to get rid of this thing for years!!!! Thanks you for a most thorough and very successful process outline. It worked (and I'm using Vista)

**Anonymous**:
Well written!! I discovered it running a performance check with Mr. Fix It and it was on the first list to iniate stop loading at start menu on my Win 7. But no perhaps it is HP. I will start with checking off no load on start and go from there. (I am more sure that it was HP installed prior to purchase.)THANK YOU.

**Anonymous**:
Revo Uninstaller hunter mode- start ISUSPM.EXE, wait for the GUI to appear. Start Revo, select hunter mode, position the hunter symbol over the ISUSPM.EXE GUI and click.Allow Revo to scan. It will list a lot of relevant registry entries, allow you to delete them, and then delete the files (except agent.exe as it's running, deleted on reboot). Else you can kill it in task manager and then delete it and a .dll file remaining.

**Anonymous**:
Worked like a champ.  BTW, the control panel icon for Installshieled will disappear (after deleting the icon entry in C:\windows\system32) just by refreshing the control panel list... no need to reboot.

**Anonymous**:
Thanks for this info! I had mine installed by purchasing an LG 27EA83 monitor. That had a utility app called "ScreenSplit" which didn't work. So i uninstalled it. That's when I noticed I have that annoying background app running. So thank you LG for that junk!

**Anonymous**:
Thanks! Just did this on Win 7

**WarningU2**:
Thank you for this


---
layout: post
title: "Error 1324: Path Contains an Invalid Character"
date: 2007-08-25
---

<div class="post-body">
<p>I was trying to uninstall the hp LaserJet 1010 Series, and was also trying to uninstall Dragon Naturally Speaking.  Both were cluttering my very slow Inspiron 2200 laptop (much slower in Windows XP than in Ubuntu, that is).  In both cases, I got a message like this:  "Error 1324. The path Inspiron Backup contains an invalid character."  The uninstallation did not appear to finish; that is, the items in question remained listed in Add or Remove Programs (found in WinXP's  Control Panel).

I searched for "Inspiron Backup" (with and without a space in the middle) using Regedit (which you can run by using Start &gt; Run).  It did not find anything.  I also searched using Lavasoft Reghance, which had strangely <a href="https://web.archive.org/web/20141022080610/http://www.lavasoftsupport.com/lofiversion/index.php/t1667.html">vanished without a trace</a> from the <a href="https://web.archive.org/web/20141022080610/http://www.lavasoftusa.com/index.php">Lavasoft website</a> but appeared to be available as <a href="https://web.archive.org/web/20141022080610/http://www.majorgeeks.com/RegHance_d468.html">shareware from MajorGeeks</a>.  (There were alternative possible tools at <a href="https://web.archive.org/web/20141022080610/http://www.snapfiles.com/Freeware/system/fwregtools.html">SnapFiles</a> and at <a href="https://web.archive.org/web/20141022080610/http://www.softpedia.com/get/Tweak/Registry-Tweak/Registrar-Lite.shtml">Softpedia</a>.)  Reghance didn't find that string either.

<a href="https://web.archive.org/web/20141022080610/http://www.experts-exchange.com/Applications/Q_21394052.html">Another user</a> had found the answer to his/her problem in the registry at this location:

MyComputer\HKEY_CURRENT_USER\Software\Microsoft\
Windows\CurrentVersion\Explorer\UserShellFolders

In that person's situation the problem had been with a reference to a folder called D:\My Pictures, and the solution was simply to delete the key containing that reference.  In my case, what I saw in that location in the registry was a key named Personal and a reference to H:\Inspiron Backup\Inspiron Drive E\Current. 

I had no such drive or folder.  I was surprised that my registry cleaning software had not detected and offered to fix this problem.  I was not sure whether to delete or fix this reference.  I *could* fix it; I did recognize the reference to a folder called "Current," which was now located on another drive.  I decided fixing would be the more conservative alternative.  So I right-clicked to modify that key, changed the reference, and used Regedit's File &gt; Export option to save a REG file.  I edited that REG file using Notepad, so that its contents pertained only to what I had changed.

In doing so, I noticed that the New folder under this registry key also contained other references to H:\Inspiron Backup, as well as a mistaken location for the Temporary Internet Files cache.  Thus, my revised REG file looked like this:

Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Windows\
CurrentVersion\Explorer\User Shell Folders]
"Personal"="E:\\Current"

[HKEY_CURRENT_USER\Software\Microsoft\Windows\
CurrentVersion\Explorer\User Shell Folders\New]
"My Video"="E:\\Current"
"Cache"="F:\Miscellany\Temporary Internet Files"
"My Pictures"="E:\\Current"
"My Music"="E:\\Current"

After running that REG file, I rebooted and tried again on the uninstallation.  This time, when trying to uninstall Dragon NaturallySpeaking, I got "Error 1721. There is a problem with this Windows Installer package.  A program required for this install to complete could not be run."  Then, as before, "Fatal error during installation."  I tried with the hp LaserJet 1010 Series.  That one ran to completion, and the hp LaserJet 1010 Series item vanished from Add or Remove Programs.  So I suspected I could probably finish the job by reinstalling Dragon NaturallySpeaking and then re-uninstalling.  I ran a repair installation from the program CD and also reinstalled the Dragon NaturallySpeaking 8.0 Service Pack 1E that I had apparently downloaded and installed previously.  After rebooting, I uninstalled it without further difficulty.

It occurred to me that another way of finding references to the Inspiron Backup folder -- the one cited in Error 1324, above -- would be to export the whole registry, rename it from being a REG file to being a TXT file, and search it in Notepad.  I did that and found at least a half-dozen other references.  It wasn't necessary to go back into the registry to change them all, one by one.  Instead, for each of these other references, I kept the header (i.e., the line, shown above, that refers to some HKEY_CURRENT_USER or similar location); I corrected the registry key so that, as in the above example, it pointed to the correct folder (making sure that all folder names in the registry key references (unlike the HKEY line) were preceded with double (not single) slashes, and making new folders in appropriate locations in some instances); I added these additional portions to the REG file shown above; and I ran the REG file -- which, of course, I kept, in case I ever had to do this again following e.g., a System Restore.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

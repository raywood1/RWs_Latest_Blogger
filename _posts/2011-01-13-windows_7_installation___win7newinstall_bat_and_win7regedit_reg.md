---
layout: post
title: "Windows 7 Installation:  Win7NewInstall.bat and Win7RegEdit.reg"
date: 2011-01-13
---

<div class="post-body">
<p>In the process of installing and adjusting Windows 7 Ultimate, I developed a batch file (Win7NewInstall.bat) to run certain commands.  I also developed a registry (.reg) file (which I called Win7RegEdit.reg) to make a number of tweaks automatically.  I developed these to be run in that order -- the batch file first, and then the registry edit file.<br/>
<br/>
I found that some parts of the .reg file did not perform as desired.  Running the .reg file produced an error:<br/>
<br/>
<blockquote>Registry Editor<br/>
<br/>
Cannot import [filename]:  Not all data was successfully written to the registry.  Some keys are open by the system or other processes.</blockquote>I went through the registry edits that I had incorporated into the file, at that point, and identified individual items that were not installing, even with other programs closed.  <a href="https://web.archive.org/web/20190513231610/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;q=%22Not+all+data+was+successfully+written+to+the+registry%22+%22Windows+7%22+.reg+edit&amp;aq=f&amp;aqi=&amp;aql=f&amp;oq=">My search</a> for responses to this error led to some webpages that made me think I might be better off making the needed changes via a batch file.  Unfortunately, batch files sometimes produced the similar "ERROR: Access is denied."  <a href="https://web.archive.org/web/20190513231610/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;q=%22Windows+7%22+intitle:%22access+is+denied%22+batch+registry&amp;aq=f&amp;aqi=&amp;aql=f&amp;oq=">A search</a> for answers to that led, in turn, to an understanding that I would need to take owneship of registry keys to make those changes; but <a href="https://web.archive.org/web/20190513231610/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;q=%22Windows+7%22+%22take+ownership+of+registry%22&amp;aq=f&amp;aqi=&amp;aql=f&amp;oq=">a search</a> on that subject led to <a href="https://web.archive.org/web/20190513231610/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;q=%22Windows+7%22+-NT+-Vista+-XP+batch+registry+edit+permissions&amp;aq=f&amp;aqi=&amp;aql=f&amp;oq=">another search</a> whose upshot was that there was not a good automated way to take ownership of such keys, or at least not one that I would know how to use.<br/>
<br/>
I started to convert the .reg file to .batch file lines.  I found guidance for that translation in tutorials from <a href="https://web.archive.org/web/20190513231610/http://www.sevenforums.com/tutorials/84189-convert-reg-files-bat-files.html">Dwarf</a> and from <a href="https://web.archive.org/web/20190513231610/http://www.petri.co.il/reg_command_in_windows_xp.htm">Daniel Petri</a>, and also in the online help files (in a Win7 cmd window, type "REG /?").  This step, by itself, did not eliminate the error shown above.  Running a prohibited batch command in a DOS box (a/k/a cmd window, produced by Start &gt; cmd) would yield Running the batch file in Windows 7 Safe Mode would sometimes if not always yield the same error.<br/>
<br/>
I decided the most efficient solution was to automate the changes that I could automate (using either batch commands or the .reg file); failing that, to use <a href="https://web.archive.org/web/20190513231610/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;q=%22Ultimate+Windows+Tweaker%22&amp;aq=f&amp;aqi=g10&amp;aql=f&amp;oq=">Ultimate Windows Tweaker</a>; and if that too failed, then go into the registry and make the changes manually.  I then found I was able to automate parts of the manual process, so I built those parts into the sequence.  In other words, the way I worked it out, I would run the batch file, then run the reg file, then run Ultimate Windows Tweaker, then make changes manually (e.g., in Control Panel).  These steps are described more fully in my post about the whole Win7 installation process, from about this same time, entitled "Windows 7 Installation:  Second Try."<br/>
<br/>
I assembled these materials over a period of weeks, with numerous changes. This post does not necessarily represent the final state of these materials. It is more of a record of how they had developed at this point. It could be a very bad idea for someone else to simply adopt and run these files as-is. I could not say what effects that might have. Where I happened to think of it, I added some explanatory and cautionary comments within these files. For posterity, the contents of the Win7NewInstall.bat file were as follows:<br/>
<blockquote>@echo off<br/>
<br/>
:: ***** Win7NewInstall.bat *****<br/>
<br/>
:: ************* NOTES *************<br/>
<br/>
:: These commands customize a new Windows 7 installation.<br/>
:: I used some of these on my system. They are offered for reference.<br/>
:: These commands can ruin your system. Use at your own risk.<br/>
<br/>
:: These were converted from .reg file lines, guided by the DOS help files at REG /?<br/>
:: I tried to minimize other running programs before running these commands.<br/>
:: Consult original source webpages for comments, changes, updates, etc.<br/>
:: I ran these as Administrator and had to reboot for some to take effect.<br/>
<br/>
:: Set permissions manually as needed<br/>
:: This step requires OORegEditor, or something like it, in a designated directory.<br/>
cls<br/>
echo.<br/>
echo Copy and paste each of these into a program like OORegEditor (Ctrl-G).<br/>
echo The locations may already be saved as Favorites in that program.<br/>
echo.<br/>
echo There, right-click and set permissions for each of these keys.<br/>
echo.<br/>
echo HKEY_CLASSES_ROOT\CLSID\{323CA680-C24D-4099-B94D-446DD2D7249E}\ShellFolder<br/>
echo.<br/>
pause<br/>
cls<br/>
echo.<br/>
echo The remaining tweaks will now install.<br/>
echo.<br/>
pause<br/>
cls<br/>
<br/>
:: Disable User Account Control<br/>
<br/>
wait "" "C:\Windows\System32\cmd.exe" /k %windir%\System32\reg.exe ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 0 /f<br/>
:: Optional: Enable User Account Control<br/>
:: C:\Windows\System32\cmd.exe /k %windir%\System32\reg.exe ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 1 /f<br/>
:: Other UAC Options<br/>
:: http://www.howtogeek.com/howto/windows-vista/4-ways-to-make-uac-less-annoying-on-windows-vista/<br/>
:: http://www.howtogeek.com/howto/3340/how-to-manage-uac-notifications-in-windows-7/<br/>
<br/>
:: Create God Mode folder in Start Menu<br/>
<br/>
md "D:\Installation\Start Menu\Programs\Tools\Tweakers\God Mode.{ED7BA470-8E54-465E-825C-99712043E01C}"<br/>
<br/>
:: Turn off Windows Defender - it is included in Microsoft Security Essentials<br/>
<br/>
takeown /f "c:\Program Files\Windows Defender" /r /d y<br/>
icacls "c:\Program Files\Windows Defender" /grant Administrator:F /t<br/>
ren "c:\Program Files\Windows Defender\MSASCui.exe" "c:\Program Files\Windows Defender\wasMSASCui.exe"<br/>
<br/>
:: Map Network Drives<br/>
<br/>
:: Not presently using network drives.<br/>
:: Command form: net use z: /persistent:yes \\servername\foldername password<br/>
:: More info at http://raywoodcockslatest.blogspot.com/2010/07/vmware-workstation-ubuntu-host-windows.html<br/>
<br/>
:: Run the registry tweaks file<br/>
<br/>
start "" "D:\Installation\Windows 7 Drive C\03 Other Installation &amp; Tweaking Programs\99 Win7RegTweaks.reg"<br/>
<br/>
exit</blockquote>As shown in those final lines, Win7NewInstall.bat would then run Win7RegTweaks.reg.  The contents of Win7RegTweaks.reg at this point were as follows:<br/>
<blockquote>Windows Registry Editor Version 5.00<br/>
<br/>
; ************* NOTES *************<br/>
<br/>
; These are registry edits. They can ruin your system. Use at your own risk.<br/>
;<br/>
; There are undo options for many of these at the sources (above).<br/>
; Items that are commented out were not needed on this system.<br/>
; Run this with no other programs running (even Windows Explorer).<br/>
; Probably have to run as Administrator in some cases.<br/>
; Consult the original source webpage for comments, changes, updates, etc.<br/>
; May have to reboot for some of these to take effect.<br/>
<br/>
; ************* SOURCES *************<br/>
<br/>
; http://www.howtogeek.com/howto/37920/the-50-best-registry-hacks-that-make-windows-better/<br/>
; http://www.sevenforums.com/tutorials/257-windows-7-tutorial-index.html<br/>
; and other assorted sources.<br/>
<br/>
; ************* WINDOWS EXPLORER *************<br/>
<br/>
; ***** Disable Libraries *****<br/>
<br/>
[-HKEY_CLASSES_ROOT\CLSID\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Classes\CLSID\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}]<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel]<br/>
“{031E4825-7B94-4dc3-B131-E946B44C8DD5}”=-<br/>
; Restore default<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel]<br/>
; "{031E4825-7B94-4dc3-B131-E946B44C8DD5}"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
; @="UsersLibraries"<br/>
; "Removal Message"="@shell32.dll,-9047"<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}]<br/>
; "Name"="MusicLibrary"<br/>
; "Category"=dword:00000004<br/>
; "ParsingName"="::{031E4825-7B94-4dc3-B131-E946B44C8DD5}\\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}"<br/>
; "Stream"=dword:00000001<br/>
; "StreamResource"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,32,00,00,00<br/>
; "StreamResourceType"="LIBRARY"<br/>
; "RelativePath"="Music.library-ms"<br/>
; "ParentFolder"="{1B3EA5DC-B587-4786-B4EF-BD1DC332AEAE}"<br/>
; "Icon"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,74,\<br/>
; 00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,69,00,\<br/>
; 6d,00,61,00,67,00,65,00,72,00,65,00,73,00,2e,00,64,00,6c,00,6c,00,2c,00,2d,\<br/>
; 00,31,00,30,00,30,00,34,00,00,00<br/>
; "InfoTip"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,31,00,32,00,36,00,38,00,39,00,00,00<br/>
; "LocalizedName"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,\<br/>
; 6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,\<br/>
; 00,5c,00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,\<br/>
; 2c,00,2d,00,33,00,34,00,35,00,38,00,34,00,00,00<br/>
; "PreCreate"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}\PropertyBag]<br/>
; "FoldersDependentOn"="{4BD8D571-6D19-48D3-BE97-422220080E43};{3214FAB5-9757-4298-BB61-92A9DEAA44FF}"<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}]<br/>
; "Name"="VideosLibrary"<br/>
; "Category"=dword:00000004<br/>
; "ParsingName"="::{031E4825-7B94-4dc3-B131-E946B44C8DD5}\\{491E922F-5643-4af4-A7EB-4E7A138D8174}"<br/>
; "Stream"=dword:00000001<br/>
; "StreamResource"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,34,00,00,00<br/>
; "StreamResourceType"="LIBRARY"<br/>
; "RelativePath"="Videos.library-ms"<br/>
; "ParentFolder"="{1B3EA5DC-B587-4786-B4EF-BD1DC332AEAE}"<br/>
; "Icon"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,74,\<br/>
; 00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,69,00,\<br/>
; 6d,00,61,00,67,00,65,00,72,00,65,00,73,00,2e,00,64,00,6c,00,6c,00,2c,00,2d,\<br/>
; 00,31,00,30,00,30,00,35,00,00,00<br/>
; "InfoTip"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,31,00,32,00,36,00,39,00,30,00,00,00<br/>
; "LocalizedName"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,\<br/>
; 6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,\<br/>
; 00,5c,00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,\<br/>
; 2c,00,2d,00,33,00,34,00,36,00,32,00,30,00,00,00<br/>
; "PreCreate"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}\PropertyBag]<br/>
; "FoldersDependentOn"="{18989B1D-99B5-455B-841C-AB7C74E4DDFC};{2400183A-6185-49FB-A2D8-4A392A602BA3}"<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}]<br/>
; "Name"="DocumentsLibrary"<br/>
; "Category"=dword:00000004<br/>
; "ParsingName"="::{031E4825-7B94-4dc3-B131-E946B44C8DD5}\\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}"<br/>
; "Stream"=dword:00000001<br/>
; "StreamResource"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,31,00,00,00<br/>
; "StreamResourceType"="LIBRARY"<br/>
; "RelativePath"="Documents.library-ms"<br/>
; "ParentFolder"="{1B3EA5DC-B587-4786-B4EF-BD1DC332AEAE}"<br/>
; "Icon"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,74,\<br/>
; 00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,69,00,\<br/>
; 6d,00,61,00,67,00,65,00,72,00,65,00,73,00,2e,00,64,00,6c,00,6c,00,2c,00,2d,\<br/>
; 00,31,00,30,00,30,00,32,00,00,00<br/>
; "LocalizedName"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,\<br/>
; 6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,\<br/>
; 00,5c,00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,\<br/>
; 2c,00,2d,00,33,00,34,00,35,00,37,00,35,00,00,00<br/>
; "PreCreate"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}\PropertyBag]<br/>
; "FoldersDependentOn"="{FDD39AD0-238F-46AF-ADB4-6C85480369C7};{ED4824AF-DCE4-45A8-81E2-FC7965083634}"<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}]<br/>
; "Name"="UsersLibrariesFolder"<br/>
; "Category"=dword:00000001<br/>
; "ParsingName"="::{031E4825-7B94-4dc3-B131-E946B44C8DD5}"<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}\PropertyBag]<br/>
; "NoCustomize"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}]<br/>
; "Name"="PicturesLibrary"<br/>
; "Category"=dword:00000004<br/>
; "ParsingName"="::{031E4825-7B94-4dc3-B131-E946B44C8DD5}\\{A990AE9F-A03B-4e80-94BC-9912D7504104}"<br/>
; "Stream"=dword:00000001<br/>
; "StreamResource"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,33,00,00,00<br/>
; "StreamResourceType"="LIBRARY"<br/>
; "RelativePath"="Pictures.library-ms"<br/>
; "ParentFolder"="{1B3EA5DC-B587-4786-B4EF-BD1DC332AEAE}"<br/>
; "Icon"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,74,\<br/>
; 00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,69,00,\<br/>
; 6d,00,61,00,67,00,65,00,72,00,65,00,73,00,2e,00,64,00,6c,00,6c,00,2c,00,2d,\<br/>
; 00,31,00,30,00,30,00,33,00,00,00<br/>
; "InfoTip"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,\<br/>
; 6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,\<br/>
; 00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,2c,00,\<br/>
; 2d,00,31,00,32,00,36,00,38,00,38,00,00,00<br/>
; "LocalizedName"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,\<br/>
; 6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,\<br/>
; 00,5c,00,73,00,68,00,65,00,6c,00,6c,00,33,00,32,00,2e,00,64,00,6c,00,6c,00,\<br/>
; 2c,00,2d,00,33,00,34,00,35,00,39,00,35,00,00,00<br/>
; "PreCreate"=dword:00000001<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}\PropertyBag]<br/>
; "FoldersDependentOn"="{33E28130-4E1E-4676-835A-98395C3BC3BB};{B6EBFB86-6907-413C-9AF7-4FC2ABF07CC5}"<br/>
<br/>
; Hide Favorites<br/>
; Requires manual change of permissions<br/>
[HKEY_CLASSES_ROOT\CLSID\{323CA680-C24D-4099-B94D-446DD2D7249E}\ShellFolder]<br/>
"Attributes"=dword:a9400100<br/>
; Restore default<br/>
; "Attributes"=dword:a0900100<br/>
<br/>
; Set Documents folder template as default<br/>
; source: http://www.sevenforums.com/tutorials/11356-folder-view-apply-all-folders.html<br/>
[HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags\AllFolders\Shell]<br/>
"FolderType"="Documents"<br/>
; Alternative: use General type instead<br/>
; "FolderType"="NotSpecified"<br/>
; Restore default<br/>
; [HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags\AllFolders\Shell]<br/>
; "FolderType"=-<br/>
; [-HKEY_CURRENT_USER\Software\Microsoft\Windows\Shell\BagMRU]<br/>
; [-HKEY_CURRENT_USER\Software\Microsoft\Windows\Shell\Bags]<br/>
; [-HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\BagMRU]<br/>
; [-HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags]<br/>
<br/>
; ***** Context Menu *****<br/>
<br/>
; Add context menu option to open files with Notepad<br/>
[HKEY_CLASSES_ROOT\*\shell\Notepad]<br/>
@="Open with Notepad"<br/>
[HKEY_CLASSES_ROOT\*\shell\Notepad\command]<br/>
@="notepad.exe \"%1\""<br/>
; Remove option<br/>
; [-HKEY_CLASSES_ROOT\*\shell\Notepad]<br/>
<br/>
; Add context menu option to take ownership of files and folders<br/>
[HKEY_CLASSES_ROOT\*\shell\runas]<br/>
@="Take Ownership"<br/>
"NoWorkingDirectory"=""<br/>
[HKEY_CLASSES_ROOT\*\shell\runas\command]<br/>
@="cmd.exe /c takeown /f \"%1\" &amp;&amp; icacls \"%1\" /grant administrators:F"<br/>
"IsolatedCommand"="cmd.exe /c takeown /f \"%1\" &amp;&amp; icacls \"%1\" /grant administrators:F"<br/>
[HKEY_CLASSES_ROOT\Directory\shell\runas]<br/>
@="Take Ownership"<br/>
"NoWorkingDirectory"=""<br/>
[HKEY_CLASSES_ROOT\Directory\shell\runas\command]<br/>
@="cmd.exe /c takeown /f \"%1\" /r /d y &amp;&amp; icacls \"%1\" /grant administrators:F /t"<br/>
"IsolatedCommand"="cmd.exe /c takeown /f \"%1\" /r /d y &amp;&amp; icacls \"%1\" /grant administrators:F /t"<br/>
; Restore default<br/>
; [-HKEY_CLASSES_ROOT\*\shell\runas]<br/>
; [-HKEY_CLASSES_ROOT\Directory\shell\runas]<br/>
<br/>
; Add context menu items Copy To Folder and Move To Folder<br/>
; [HKEY_CLASSES_ROOT\AllFilesystemObjects\shellex\ContextMenuHandlers]<br/>
; [HKEY_CLASSES_ROOT\AllFilesystemObjects\shellex\ContextMenuHandlers\Copy To]<br/>
; @="{C2FBB630-2971-11D1-A18C-00C04FD75D13}"<br/>
[HKEY_CLASSES_ROOT\AllFilesystemObjects\shellex\ContextMenuHandlers\Move To]<br/>
@="{C2FBB631-2971-11D1-A18C-00C04FD75D13}"<br/>
<br/>
; Add context menu item to copy text files to clipboard<br/>
[HKEY_CLASSES_ROOT\txtfile\shell\copytoclip]<br/>
@="Copy to Clipboard"<br/>
"Extended"=""<br/>
[HKEY_CLASSES_ROOT\txtfile\shell\copytoclip\command]<br/>
@="cmd /c clip &lt; \"%1\""<br/>
; Restore default<br/>
; [-HKEY_CLASSES_ROOT\txtfile\shell\copytoclip]<br/>
<br/>
; Add context menu encryption option<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"EncryptionContextMenu"=dword:00000001<br/>
<br/>
; ***** Other Functioning *****<br/>
<br/>
; Disable annoying web service dialog for opening files<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoInternetOpenWith"=dword:00000001<br/>
[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoInternetOpenWith"=dword:00000001<br/>
; Restore default<br/>
; [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
; "NoInternetOpenWith"=-<br/>
; [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
; "NoInternetOpenWith"=-<br/>
<br/>
; ***** Unused *****<br/>
<br/>
; Double-pane Windows Explorer for network drives<br/>
; [HKEY_CLASSES_ROOT\Folder\shell\open\ddeexec]<br/>
; @="[ExploreFolder(\"%l\", %I, %S)]"<br/>
<br/>
; Disable context menu item Send To<br/>
; [HKEY_CLASSES_ROOT\AllFilesystemObjects\shellex\ContextMenuHandlers\Send To]<br/>
; @=""<br/>
; Restore default<br/>
; @="{7BA4C740-9E81-11CF-99D3-00AA004AE837}"<br/>
<br/>
; Disable Caps Lock key<br/>
; [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]<br/>
; "Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,00,00,3a,00,00,00,00,00<br/>
; Alternative: change Caps Lock to Ctrl<br/>
; "Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,1d,00,3a,00,00,00,00,00 <br/>
; Alternative: change Caps Lock to Shift<br/>
; "Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,2a,00,3a,00,00,00,00,00<br/>
; Alternative: change Caps Lock to ScrollLock<br/>
; "Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,00,00,3a,00,3A,00,46,00,00,00,00,00<br/>
; Eliminate keyboard remap<br/>
; "Scancode Map"=-<br/>
<br/>
; Disable balloon tips<br/>
; [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
; "EnableBalloonTips"=dword:00000000<br/>
; Restore default<br/>
; "EnableBalloonTips"=-<br/>
<br/>
; Set Alt-Tab to show thumbnails despite Classic desktop theme<br/>
; Doesn't work<br/>
; [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer]<br/>
; "AltTabSettings"=-<br/>
; Alternate: set Alt-Tab to Classic<br/>
; [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer]<br/>
; "AltTabSettings"=dword:00000001<br/>
<br/>
; ************* START MENU, TASKBAR, AND THUMBNAILS ************* <br/>
<br/>
; Make Aero Peek happen instantly<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"DesktopLivePreviewHoverTime"=dword:00000000<br/>
; Restore default<br/>
; "DesktopLivePreviewHoverTime"=dword:000001f4<br/>
<br/>
; Make Aero taskbar thumbnails show contents immediately when hovering<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"ExtendedUIHoverTime"=dword:00000001<br/>
<br/>
; Increase Start Menu display speed -- default is 400<br/>
[HKEY_CURRENT_USER\Control Panel\Desktop]<br/>
"MenuShowDelay"="200"<br/>
<br/>
; ************* FILE LOCATIONS ************* <br/>
<br/>
; Point to D for Start Menu and Programs<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders]<br/>
"Administrative Tools"="D:\\Installation\\Start Menu"<br/>
"Programs"="D:\\Installation\\Start Menu\\Programs"<br/>
"Startup"="D:\\Installation\\Start Menu\\Programs\\Startup"<br/>
"Start Menu"="D:\\Installation\\Start Menu"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders]<br/>
"Programs"="D:\\Installation\\Start Menu\\Programs"<br/>
"Startup"="D:\\Installation\\Start Menu\\Programs\\Startup"<br/>
"Start Menu"="D:\\Installation\\Start Menu"<br/>
<br/>
; Point to Current folder for Music, Video, Pictures, etc.<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders]<br/>
"My Music"="D:\\Current"<br/>
"My Pictures"="D:\\Current"<br/>
"My Video"="D:\\Current"<br/>
"Personal"="D:\\Current"<br/>
"{374DE290-123F-4565-9164-39C4925E467B}"="D:\\Current"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders]<br/>
"My Music"="D:\\Current"<br/>
"My Pictures"="D:\\Current"<br/>
"My Video"="D:\\Current"<br/>
"Personal"="D:\\Current"<br/>
"{374DE290-123F-4565-9164-39C4925E467B}"="D:\\Current"<br/>
<br/>
; Point to X:\Cache for cookies, cache, etc.<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders]<br/>
"Cache"="X:\\Cache\\Temporary Internet Files"<br/>
"Cookies"="X:\\Cache\\Cookies"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders]<br/>
"Cache"="X:\\Cache\\Temporary Internet Files"<br/>
"Cookies"="X:\\Cache\\Cookies"<br/>
<br/>
; ************* FILE OPENING ************* <br/>
<br/>
; Files with no extension open in Notepad<br/>
[HKEY_CLASSES_ROOT\*\shell]<br/>
[HKEY_CLASSES_ROOT\*\shell\open]<br/>
@="Open With Notepad"<br/>
[HKEY_CLASSES_ROOT\*\shell\open\command]<br/>
@="notepad.exe %1"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.]<br/>
"Application"="Notepad"<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Directory\shell\Notepad]<br/>
@="Notepad"<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Directory\shell\Notepad\command]<br/>
@="C:\\Windows\\notepad"<br/>
<br/>
; Disable Windows from asking "Do you want to open this file?"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Download] <br/>
"CheckExeSignatures"="no" <br/>
"RunInvalidSignatures"=dword:00000001 <br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Attachments] <br/>
"SaveZoneInformation"=dword:00000001 <br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Associations] <br/>
"LowRiskFileTypes"=".zip;.rar;.nfo;.txt;.exe;.bat;.com;.cmd;.reg;.msi;.htm;.html;.gif;.bmp;.jpg;.avi;.mpg;.mpeg;.mov;.mp3;.m3u;.wav;"<br/>
<br/>
; ************* INTERNET EXPLORER ************* <br/>
<br/>
; Specify IE download directory<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer]<br/>
"Download Directory"="D:\\Current"<br/>
<br/>
; Force IE to launch shortcuts in a new window<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Main]<br/>
"AllowWindowReuse"=dword:00000000<br/>
<br/>
; ************* LOGIN, LOGOUT, SHUTDOWN *************<br/>
<br/>
; Prevent Windows from rebooting after updates<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU]<br/>
"NoAutoRebootWithLoggedOnUsers"=dword:00000001<br/>
; Restore default<br/>
; "NoAutoRebootWithLoggedOnUsers"=-<br/>
<br/>
; Save settings on exit<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoSaveSettings"=dword:00000000<br/>
<br/>
; Disable automatic restart after crash so you can see error messages<br/>
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl]<br/>
"AutoReboot "=dword:00000000<br/>
<br/>
; Don't clear paging file at shutdown<br/>
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management]<br/>
"ClearPageFileAtShutdown"=dword:00000000<br/>
<br/>
; Hide user account on login screen<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\SpecialAccounts]<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\SpecialAccounts\UserList]<br/>
"Administrator"=dword:00000000<br/>
; Restore default<br/>
; [-HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\SpecialAccounts\UserList]<br/>
; [-HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\SpecialAccounts]<br/>
<br/>
; ************* OTHER TWEAKS *************<br/>
<br/>
; Remove "Shortcut" from title of shortcuts <br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer]<br/>
"link"=hex:00,00,00,00<br/>
; Restore default<br/>
; "link"=hex:1e,00,00,00<br/>
<br/>
; Removable devices Auto-Play off<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoDriveTypeAutoRun"=dword:00000095<br/>
; Alternate: "NoDriveTypeAutoRun"=dword:000000FF<br/>
; May not be needed in Win7: "NoSaveSettings"=dword:00000000<br/>
<br/>
; Disable creation of Thumbs.db<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"DisableThumbnailCache"=dword:00000001<br/>
<br/>
; Disable beep on error<br/>
[HKEY_CURRENT_USER\Control Panel\Sound]<br/>
"Beep"="No"<br/>
<br/>
; Increase Internet download connections to 10<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings]<br/>
"MaxConnectionsPerServer"=dword:0000000a<br/>
"MaxConnectionsPer1_0Server"=dword:0000000a<br/>
<br/>
; Set Control Panel to classic view<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"ForceClassicControlPanel"=dword:00000001</blockquote>After a week of using the system, these edits seemed generally stable.  It appeared that a few might be ineffectual.  I was using Ultimate Windows Tweaker to try again on making those changes.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**linda liu**:
such a good post , if you can tell me what to do when iforgot windows 7 password, i will very thankful.


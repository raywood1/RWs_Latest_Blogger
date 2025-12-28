---
layout: post
title: "Win7RegEdit.reg Updated"
date: 2011-11-30
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20151029190959/http://raywoodcockslatest.blogspot.com/2011/01/windows-7-installation-win7regeditreg.html" target="_blank">previously developed</a> a .reg file that would automate a number of registry edits in Windows 7.  This post presents a slimmed-down version of that .reg file.  The tweaks in this .reg file were part of a Win7 installation that also used Ultimate Windows Tweaker and other tools, as described in another post in this blog.  The purpose of the present post is just to display the contents of Win7RegEdit.reg.<br/>
<br/>
The following text will probably display better if copied and pasted into Notepad.  It may be necessary to correct some line breaks inserted by the blog website.  I wouldn't recommend using this information if you aren't sure what you're doing and haven't backed up your system.<br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Windows Registry Editor Version 5.00</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Run Ultimate Windows Tweaker first.  This adds options not available there.<br/>
; More info &amp; restore options in 32-bit version of this file.</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* WINDOWS EXPLORER *************</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ***** Disable Libraries *****<br/>
[-HKEY_CLASSES_ROOT\CLSID\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Classes\CLSID\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{031E4825-7B94-4dc3-B131-E946B44C8DD5}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}]<br/>
[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}]<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel]<br/>
“{031E4825-7B94-4dc3-B131-E946B44C8DD5}”=-</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Set Documents folder template as default<br/>
[HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags\AllFolders\Shell]<br/>
"FolderType"="Documents"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Add context menu option to open files with Notepad<br/>
[HKEY_CLASSES_ROOT\*\shell\Notepad]<br/>
@="Open with Notepad"<br/>
[HKEY_CLASSES_ROOT\*\shell\Notepad\command]<br/>
@="notepad.exe \"%1\""</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable Windows from asking "Do you want to open this file?"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Download] <br/>
"CheckExeSignatures"="no" <br/>
"RunInvalidSignatures"=dword:00000001 <br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Attachments] <br/>
"SaveZoneInformation"=dword:00000001 <br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Associations] <br/>
"LowRiskFileTypes"=".zip;.rar;.nfo;.txt;.exe;.bat;.com;.cmd;.reg;.msi;.htm;.html;.gif;.bmp;.jpg;.avi;.mpg;.mpeg;.mov;.mp3;.m3u;.wav;"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable annoying web service dialog for opening files<br/>
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoInternetOpenWith"=dword:00000001<br/>
[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoInternetOpenWith"=dword:00000001</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable Windows 7 built-in CD burning<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoCDBurning"=dword:00000001</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* START MENU, TASKBAR, AND THUMBNAILS ************* </span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Make Aero Peek happen instantly<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"DesktopLivePreviewHoverTime"=dword:00000000</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Make Aero taskbar thumbnails show contents immediately when hovering<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"ExtendedUIHoverTime"=dword:00000001</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Increase Start Menu display speed -- default is 400<br/>
[HKEY_CURRENT_USER\Control Panel\Desktop]<br/>
"MenuShowDelay"="200"</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* FILE LOCATIONS ************* </span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Point to W for customized Start Menu and Programs<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders]<br/>
"Administrative Tools"="W:\\Start Menu"<br/>
"Programs"="W:\\Start Menu\\Programs"<br/>
"Startup"="W:\\Start Menu\\Programs\\Startup"<br/>
"Start Menu"="W:\\Start Menu"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders]<br/>
"Programs"="W:\\Start Menu\\Programs"<br/>
"Startup"="W:\\Start Menu\\Programs\\Startup"<br/>
"Start Menu"="W:\\Start Menu"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Point to Current folder for Music, Video, Pictures, etc.<br/>
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
"{374DE290-123F-4565-9164-39C4925E467B}"="D:\\Current"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Point to X:\Cache for cookies, cache, etc.<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders]<br/>
"Cache"="X:\\Cache\\Temporary Internet Files"<br/>
"Cookies"="X:\\Cache\\Cookies"<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders]<br/>
"Cache"="X:\\Cache\\Temporary Internet Files"<br/>
"Cookies"="X:\\Cache\\Cookies"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Customize default places bar in Win7's common file dialog box<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\comdlg32]<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\comdlg32\Placesbar]<br/>
"Place0"="MyDocuments"<br/>
"Place1"="Recent"<br/>
"Place2"="D:\\Career"<br/>
"Place3"="D:\\Personal Projects"<br/>
"Place4"="W:\\Start Menu\\Programs"</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* INTERNET EXPLORER ************* </span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Specify IE download directory<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer]<br/>
"Download Directory"="D:\\Current"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Force IE to launch shortcuts in a new window<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Main]<br/>
"AllowWindowReuse"=dword:00000000</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* LOGIN, LOGOUT, SHUTDOWN *************</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Save settings on exit<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]<br/>
"NoSaveSettings"=dword:00000000</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable automatic restart after crash so you can see error messages<br/>
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl]<br/>
"AutoReboot "=dword:00000000</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; ************* OTHER TWEAKS *************</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Remove "Shortcut" from title of shortcuts<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer]<br/>
"link"=hex:00,00,00,00</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable creation of Thumbs.db<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]<br/>
"DisableThumbnailCache"=dword:00000001</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Disable beep on error<br/>
[HKEY_CURRENT_USER\Control Panel\Sound]<br/>
"Beep"="No"</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Increase Internet download connections to 10<br/>
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings]<br/>
"MaxConnectionsPerServer"=dword:0000000a<br/>
"MaxConnectionsPer1_0Server"=dword:0000000a</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Google Earth cache settings<br/>
[HKEY_CURRENT_USER\Software\Google\Google Earth Plus]<br/>
:: Move cache to drive X<br/>
:: Originally "CachePath"="C:\\Users\\Ray\\AppData\\LocalLow\\Google\\GoogleEarth"<br/>
"CachePath"="X:\\Cache\\Google Earth"<br/>
:: Set disk cache to 2GB and memory cache to 1GB<br/>
[HKEY_CURRENT_USER\Software\Google\Google Earth Plus\Cache]<br/>
"DiskCacheSize"=dword:000007d0<br/>
"MemoryCacheSize"=dword:000003e8</span></p>
<div style="clear: both;"></div>
</div>

---
### Comments

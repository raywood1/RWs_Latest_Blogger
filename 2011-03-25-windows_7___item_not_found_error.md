---
layout: post
title: "Windows 7:  Item Not Found Error"
date: 2011-03-25
---

<div class="post-body">
<p>Suddenly, when I was moving folders, I started getting a stupid message that the folder that I was moving was no longer where it used to be.  The message was specifically as follows:<br/>
<blockquote>Item Not Found<br/>
Could not find this item<br/>
This is no longer located in [source folder].  Verify the item's location and try again.</blockquote>Trying again would finish the move.  I wanted to stop getting this message.  I ran <a href="https://web.archive.org/web/20151125205919/http://www.google.com/search?q=%22Item+Not+Found%22+%22could+not+find+this+item%22+%22Windows+7%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;as_qdr=all&amp;num=50&amp;cad=h">a search</a> and came up with <a href="https://web.archive.org/web/20151125205919/http://answers.microsoft.com/en-us/windows/forum/windows_7-files/renaming-folders-causes-item-not-found-error-in/e2cf38c7-9e77-4256-89de-6308df53d5f9">a thread</a> suggesting that the problem was with a Windows 7 update, KB980408.  That thread led me to <a href="https://web.archive.org/web/20151125205919/http://www.overclock.net/windows/721973-msupdate-kb980408-warning-all-win7-x64-2.html#post9211430">a .reg file</a>, which I downloaded and ran:<br/>
<blockquote><span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>Windows Registry Editor Version 5.00</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'></span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{2112AB0A-C86A-4ffe-A368-0DE96E47012E}\PropertyBag]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{491E922F-5643-4af4-A7EB-4E7A138D8174}\PropertyBag]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7b0db17d-9cd2-4a93-9733-46cc89022e7c}\PropertyBag]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A302545D-DEFF-464b-ABE8-61C8648D939B}\PropertyBag]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}]</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: xx-small;'>[-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{A990AE9F-A03B-4e80-94BC-9912D7504104}\PropertyBag]</span></blockquote>That seemed to take care of it.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Awesome, thanks :)


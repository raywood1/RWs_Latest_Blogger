---
layout: post
title: "Microsoft Word:  'Attempting to open a file created in earlier version'"
date: 2012-03-17
---

<div class="post-body">
<p>I was working in Microsoft Word 2003.  I tried to open a .doc file.  It may have been originally written in WordStar, XyWrite, WordPerfect for DOS, or some other word processing program.  Word gave me an error message:<br/>
<blockquote class="tr_bq">You are attempting to open a file that was created in an earlier version  of Microsoft Office.  This file type is blocked from opening in this  version by your registry policy setting.</blockquote>Of course, this was not what I wanted to hear.  I did <a href="https://web.archive.org/web/20120701030824/https://www.google.com/search?q=%22earlier+version+of+Microsoft+Office%22+%22policy+setting%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">a search</a> and found <a href="https://web.archive.org/web/20120701030824/http://support.microsoft.com/kb/922849" target="_blank">a Microsoft webpage</a> that, for my purposes, led to <a href="https://web.archive.org/web/20120701030824/http://support.microsoft.com/kb/938810" target="_blank">another webpage</a> that led me to four REG file downloads whose contents I combined in a single REG file that I named MicrosoftOfficeUnblock.reg, whose contents were as follows:<br/>
<blockquote><span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Windows Registry Editor Version 5.00</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Unblock Word</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Word\Security\FileOpenBlock]<br/>
"FilesBeforeVersion"=dword:00000000</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Unblock Excel</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileOpenBlock]<br/>
"LotusandQuattroFiles"=dword:00000000<br/>
"LegacyBinaryFiles"=dword:00000000<br/>
"LegacyDatabaseAndDatasourceFiles"=dword:00000000</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileSaveBlock]<br/>
"LotusandQuattroFiles"=dword:00000000<br/>
"LegacyBinaryFiles"=dword:00000000<br/>
"LegacyDatabaseAndDatasourceFiles"=dword:00000000</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Unblock PowerPoint</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\PowerPoint\Security</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>\FileOpenBlock]<br/>
"FilesBeforePowerPoint97"=dword:00000000</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\PowerPoint\Security</span><br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>\FileSaveBlock]<br/>
"FilesBeforePowerPoint97"=dword:00000000</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>; Unblock Corel Draw</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>[HKEY_LOCAL_MACHINE\Software\Microsoft\Shared Tools\Graphics Filters\Import\CDR]<br/>
"Enabled"=dword:00000001</span></blockquote>I ran that REG file and also added its contents to my Win7RegEdit.reg file, along with a reminder to run that file both early and, again, late in the process of installing Windows 7.  The REG fix appeared to work without a need for a reboot; I was immediately able to open files in Word that were blocked just a few minutes earlier.</p>
<div style="clear: both;"></div>
</div>

---
### Comments


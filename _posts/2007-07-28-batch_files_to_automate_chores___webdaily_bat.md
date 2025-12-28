---
layout: post
title: "Batch Files to Automate Chores:  WEBDAILY.BAT"
date: 2007-07-28
---

<div class="post-body">
<p>You can use command-line files without knowing much about command lines.  Here's an example of a program that I run by clicking on an icon.  It's called WEBDAILY.BAT.  I edit it in Notepad.  In abbreviated form (i.e., just providing a few examples), its contents, as viewed in Notepad, are:

*********************************

::  WEBDAILY.BAT
::  Opens each website or file I want to visit daily.

@echo off

:: start firefox.exe http://www.cnn.com
start iexplore.exe http://www.thehungersite.com

:: start excel.exe "E:\Spreadsheets\Running Times and Distances.xls"

start winword.exe "E:\Projects\Pain in the Ass Term Paper.doc"

start acrobat.exe "E:\Big PDF File.pdf"

start %SystemRoot%\system32\ntbackup.exe
start %SystemRoot%\Explorer.exe "F:\Music CDs in Process\CDs"

:: start C:\Windows\notepad.exe "E:\Current\Where I Was.txt"

cls
echo When everything else has loaded, you can proceed to load Cool Edit.
pause
start "Startup Commands Batch File" "C:\Program Files\Audio\Cool Edit\cool2000.exe"

exit

*********************************

OK, let's diagnose that.  As you may have guessed, the two colons (::) at the start of a line make that line a non-command, i.e., a comment.  The contents of that line will not actually run, when you run the program; they will just sit there.  So you can see that I have "commented out" the line that used to run Excel and open the spreadsheet where I record my daily running times.  I did that because I hurt my calf and was not running daily, so I didn't really want that spreadsheet opening up all the time.

I've given examples of how you might run some of the more common programs in Windows XP.  Examples here include Word, Excel, Adobe Acrobat, and the Firefox and Internet Explorer (iexplore) web browsers.  Whatever it is, if you use it once daily, you can set this up and just click once to open all the stuff you want to work with every day.

You can copy this file and modify it to be WEBWEEKLY.BAT or WEBMONTHLY.BAT or whatever, for those webpages or files that you want to open only once a week or on some other schedule.

The last section, involving Cool Edit 2000, begins with CLS, which means Clear Screen.  I was finding that Cool Edit was not loading properly in this automated way.  It seemed to need everything else to be loaded and calmed down first, before it would run.  So I added the clear screen, followed by a pause, to show me just this command, so that I would remember to let stuff settle before letting the program proceed.  I don't remember exactly why I have that particular syntax about "Startup Commands Batch File," but it works.

To wrap up this little project, save the WEBDAILY.BAT file somewhere and create a shortcut to it.  Put the shortcut on your desktop or wherever is convenient, and you're done.  You can right-click the shortcut to edit the batch file, which is convenient.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

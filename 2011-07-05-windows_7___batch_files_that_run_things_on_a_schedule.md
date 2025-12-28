---
layout: post
title: "Windows 7:  Batch Files That Run Things on a Schedule"
date: 2011-07-05
---

<div class="post-body">
<p>I was using Windows 7.  I had a bunch of things that I did every day, other things that I did every week, and so forth -- semimonthly, monthly, quarterly, yearly.  I found that these items could be run from within batch files, and that I could run those batch files using Task Scheduler.  This post summarizes some of those arrangements.<br/>
<br/>
The first step was to create a batch file.  Here are the contents of a sample DAILY.BAT file:<br/>
<blockquote><span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>echo Ready to open Explorer sessions and projects.<br/>
echo.<br/>
echo.<br/>
echo First, it's time to exercise!<br/>
echo.<br/>
echo Then move to the last open tab in Firefox.<br/>
echo.<br/>
pause<br/>
cls<br/>
<br/>
:: Regular daily stuff<br/>
<br/>
start Excel "D:\Spreadsheets\Exercise Results.xls"<br/>
start sfc /verifyonly<br/>
del "X:\Cache\Junk Temp Folder\*.tmp"<br/>
<br/>
:: Open Firefox webpages<br/>
<br/>
start firefox "http://www.thehungersite.com"<br/>
start firefox "http://www.npr.org/series/4703895/song-of-the-day"<br/>
<br/>
:: Open folders<br/>
<br/>
start explorer.exe /e,"D:\Folder1\Subfolder1"<br/>
start explorer.exe /e,"D:\Folder2\Subfolder2"<br/>
<br/>
:: Not using now<br/>
<br/>
:: start "" "C:\Program Files\Microsoft Office\OFFICE11\Winword.exe"<br/>
:: start "" "W:\Start Menu\Programs\PortableWinampLite\winamp.exe"</span></blockquote><br/>
Using Notepad, I put materials like these into a text file called DAILY.BAT.  The BAT extension would notify Windows that this should run like a program.  The first commands shown here would clear the screen in a CMD window (CLS), show statements (using various forms of ECHO), run the System File Checker (SFS), delete the TMP files from a certain folder, and start various other programs.<br/>
<br/>
All kinds of programs could be started this way.  The information about where to go to start them was usually available in the Properties of shortcuts to them found in the Start Menu.  Some examples here included tabs that open in Firefox (having set Firefox to open new links in new tabs), new sessions of Windows Explorer (opened with a focus on a particular folder), and Microsoft Word and Excel.  The command pointing to Word, and also the one pointing to Winamp, are commented out here (i.e., there are double colons in front of them), because I decided I didn't need them now, but I didn't want to forget how I had set them up, in case I did start to use them again).<br/>
<br/>
Note the two different ways of starting Word and Excel shown here.  Both ways would work for either program; they just show two different approaches.  The reference to Word (i.e., winword.exe) included a full statement of its path, contained in quotation marks, and without specifying a particular file to open.  (The double quotation marks at the start of that Word command solved the problem that some programs would not start unless they were preceded with a dummy variable.)  But the reference to Excel just said "Excel."  That Excel command worked because I put a shortcut to Excel, called simply "Excel," in C:\Windows.  I kept a folder with a half-dozen of these kinds of shortcuts, for different programs that I would invoke frequently, and I would copy them to C:\Windows whenever I reinstalled Windows 7.<br/>
<br/>
I was able to set up batch files like this DAILY.BAT example for any timeframe.  I could have had one called EVENING.BAT, or 10AM.BAT, or MONTHLY.BAT.  I would keep them in a folder on my Start Menu, so that I could run them manually or easily find them for a quick right-click &gt; Edit.<br/>
<br/>
The next step would then be to make them run on a schedule.  This called for running Task Scheduler.  Since I had a Run option on my Start Menu, I would just go to Start &gt; Run &gt; taskschd.msc.  An alternative would be to search for Task Scheduler.  There, I would go to Actions &gt; Create Basic Task and go through the steps of the setup wizard.  When that was done, if I right-clicked on that task and looked at its tabs, I would verify these settings:<br/>
<ul><li>General tab:  Run with highest privileges; Configure for Windows 7.</li>
<li>Triggers:  Enabled.</li>
<li>Actions:  Start a program:  DAILY.BAT.  Start in:  insert the path to the place in the Start Menu, or wherever DAILY.BAT is stored.</li>
</ul>Other settings might also have to be configured for the particular purpose.  I tended to favor settings that would let the program run whenever the computer was next turned on, so that I wouldn't have to leave the machine on all the time to be sure of letting everything run right when Task Scheduler said it should.<br/>
<br/>
The general idea is that, with a scheduled batch file, I could change the things that would happen at 10 AM, or whenever the batch file was scheduled to run, by just editing the batch file in Notepad.  Anything that I would do every day, or on the fifth day of every month, would run automatically.  I might have to run it a couple of times to work out the bugs, but then it would just do its thing with no further involvement by me.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

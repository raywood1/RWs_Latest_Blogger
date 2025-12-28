---
layout: post
title: "Robocopy Commands for File and Folder Synchronization"
date: 2012-02-25
---

<div class="post-body">
<p>I wanted to know if Robocopy could replace <a href="https://web.archive.org/web/20151210035401/http://raywoodcockslatest.blogspot.com/2012/03/synchronizing-two-computers-goodsync.html" target="_blank">synchronization programs</a> like GoodSync and Allway Sync.  I decided to take a look at its options.  This post describes what I found.<br/>
<br/>
<a href="https://web.archive.org/web/20151210035401/http://theether.net/download/Microsoft/Utilities/robocopy.pdf" target="_blank">The manual for Robocopy</a> itself seemed to confirm my prior sense that Robocopy was a unidirectional copying utility.  That is, you could command it to copy from A to B, or from B to A, but not bidirectionally between A and B, never mind multidirectionally.  In particular, manual page 16, discussing Robocopy's /XO option, said this:<br/>
<blockquote class="tr_bq">The most appropriate use for /XO is to synchronize two directory trees so that they can be updated simultaneously in separate areas. To ensure that the latest files are present in both directory trees, copy with /XO first in one direction and then in the other.</blockquote>So apparently synchronization with Robocopy would require reciprocal commands:  one to copy newer files from A to B, and another, otherwise identical, command to copy from B to A.  <a href="https://web.archive.org/web/20151210035401/https://en.wikipedia.org/wiki/Robocopy#Features" target="_blank">Wikipedia</a> noted that Robocopy would not copy open files, but that seemed to be true of GoodSync as well.  I didn't expect it to be a problem for my purposes.<br/>
<br/>
(The information from the manual seemed pretty similar to what I got from a command-line "robocopy /?" command.  <a href="https://web.archive.org/web/20151210035401/http://technet.microsoft.com/en-us/library/cc733145%28WS.10%29.aspx" target="_blank">A Windows Server webpage</a> provided yet another list of Robocopy commands.  I had noticed, though, that Wikipedia said Robocopy was not entirely consistent between platforms.  It seemed I had better verify that my solutions would work on Windows 7 specifically.)<br/>
<br/>
I wasn't yet sure what kind of analysis /XO or other Robocopy commands would perform.  I assumed, but was not yet positive, that they would take account of time as well as date, down to the minute if not the second.  This thought prompted me to look into something that would improve the present gap of about 20 seconds between the clocks on the two computers -- something more fun than just resetting the clock manually, that is.  It seemed I would want one or two minutes' tolerance in timestamp comparisons in any case; but in <a href="https://web.archive.org/web/20151210035401/http://raywoodcockslatest.blogspot.com/2012/02/windows-7-setting-and-maintaining.html" target="_blank">a separate post</a>, I took a closer look at possible solutions to get the two machines closer to chronological synchronization.  (Later I saw that the manual (p. 17) said, "File-time granularity is 100 nanoseconds on NTFS, and two seconds on FAT.")<br/>
<br/>
The next step seemed to be to peruse the Robocopy command-line options, to see which ones might work for my synchronization project.  The manual (pp. 7-11) provided a concise command-line reference.   (<a href="https://web.archive.org/web/20151210035401/http://technet.microsoft.com/en-us/library/cc733145%28WS.10%29.aspx" target="_blank">Apparently</a> lowercase versions of the commands worked; I use uppercase here for visibility.)  The options that seemed most relevant were as follows, leaving out those that would be included by default:<br/>
<blockquote>/S   copy subdirectories, excluding empty ones<br/>
<br/>
/ZB   resume a copying task from a point of previous failure (presumably instead of starting over), but switch to backup mode if restartable mode fails (as when using an unreliable network); but <a href="https://web.archive.org/web/20151210035401/https://en.wikipedia.org/wiki/Robocopy#Common_usage_scenarios" target="_blank">Wikipedia</a> said that /Z would slow copying significantly<br/>
<br/>
/MOT:X and /MON:Y   monitor the source directory and run Robocopy again when X number of files have changed and Y minutes have elapsed<br/>
<br/>
/XD   exclude specified directories<br/>
<br/>
/XO   don't overwrite destination files with source files having the same name and an older timestamp<br/>
<br/>
/R   specify the number of retries<br/>
<br/>
/W   specify wait time between retries<br/>
<br/>
/REG   save /R and /W in registry as default settings<br/>
<br/>
/L   list files<br/>
<br/>
/V   produce verbose output<br/>
<br/>
/TS   display source file timestamps in output log<br/>
<br/>
/FP   display full pathnames in output log<br/>
<br/>
/NC   suppress output of Robocopy file class information<br/>
<br/>
<span id="goog_1099412079"></span><a href="https://web.archive.org/web/20151210035401/http://www.blogger.com/"></a><span id="goog_1099412080"></span><br/>
/NS   suppress output of file and directory sizes<br/>
<br/>
/NJH and /NJS   turn off logging of job header and summary<br/>
<br/>
/ETA   show estimated time of completion<br/>
<br/>
/LOG:filename or /LOG+:filename   redirect output to named file, overwriting or (+) appending if it already exists<br/>
<br/>
/TEE   display output as well as writing LOG<br/>
<br/>
/JOB:jobfile   read parameters from jobfile; optionally /IF to include files with specified names or paths; optionally /SD:path and /DD:path   to specify source and destination directories; optionally /QUIT to view job file contents without any actual copying<br/>
<br/>
/SAVE:jobfile   write current parameter settings to jobfile</blockquote>This was an intimidating set of potentially relevant options.  There were many things that could go wrong with so many choices.  I decided to look for examples and more information.  As the manual said (p. 22), these options could result in long, unwieldy commands, and it did appear that the JOB options would help with that.  I ran <a href="https://web.archive.org/web/20151210035401/https://encrypted.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Windows+7%22+%22job+options%22+Robocopy+sync+OR+synchronize+folders&amp;oq=%22Windows+7%22+%22job+options%22+Robocopy+sync+OR+synchronize+folders&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=10630l20770l0l22024l21l16l1l0l0l6l467l4328l2-12.1.2l15l0" target="_blank">a search</a> with that in mind.  It led most immediately to some general-reference sites (e.g., <a href="https://web.archive.org/web/20151210035401/http://ss64.com/nt/robocopy.html" target="_blank">SS64</a>, <a href="https://web.archive.org/web/20151210035401/http://www.powercram.com/2009/11/robocopy-syntax-command-line-switches.html" target="_blank">PowerCram</a>, <a href="https://web.archive.org/web/20151210035401/http://fixmyitsystem.com/2011/04/using-robocopy-for-enhance-file.html" target="_blank">FixMyITSystem</a>).  I tried again.  <a href="https://web.archive.org/web/20151210035401/https://encrypted.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Windows+7%22+Robocopy+intitle%3Ajob+%22job+options%22+sync+OR+synchronize+folders&amp;oq=%22Windows+7%22+Robocopy+intitle%3Ajob+%22job+options%22+sync+OR+synchronize+folders&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=382773l388655l0l389930l14l12l0l0l0l2l442l2741l1.5.2.2.2l12l0" target="_blank">That search</a> led almost nowhere.  Likewise another, seemingly <a href="https://web.archive.org/web/20151210035401/https://encrypted.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Robocopy+intitle%3Ajob+%22sync+folders%22+OR+%22synchronize+folders%22&amp;oq=Robocopy+intitle%3Ajob+%22sync+folders%22+OR+%22synchronize+folders%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=5240l10586l0l11238l12l8l0l0l0l1l567l1696l1.4.2.5-1l8l0" target="_blank">broader search</a>.<br/>
<br/>
Eventually, I found <a href="https://web.archive.org/web/20151210035401/http://www.ehow.com/how_7234428_sync-folders-xcopy.html" target="_blank">an eHow website</a> that said I could use XCopy to synchronize computers.  Was I trying to use the wrong tool?  It didn't seem so.  I saw indications that Robocopy had <a href="https://web.archive.org/web/20151210035401/http://www.ehow.com/info_8461260_differences-between-robocopy-xcopy.html" target="_blank">more options</a> and <a href="https://web.archive.org/web/20151210035401/http://stackoverflow.com/questions/9215661/parallel-copy-using-xcopy" target="_blank">better performance</a>, and that use of XCopy was <a href="https://web.archive.org/web/20151210035401/https://en.wikipedia.org/wiki/XCOPY#Deprecation" target="_blank">deprecated</a>.  But why was I not seeing tons of obvious references to the use of Robocopy JOB options for synchronization?  (Another possibility with lots of options:  <a href="https://web.archive.org/web/20151210035401/http://www.xxcopy.com/xxcopy30.htm" target="_blank">XXCOPY</a>.  But the least expensive version <a href="https://web.archive.org/web/20151210035401/http://www.xxcopy.com/xcpyofaq.htm" target="_blank">for networked computers</a> cost $100, and its reception at <a href="https://web.archive.org/web/20151210035401/http://download.cnet.com/XXCOPY/3000-2248_4-10648429.html?tag=contentMain;contentBody;1d" target="_blank">CNET</a> was underwhelming.)<br/>
<br/>
I tried <a href="https://web.archive.org/web/20151210035401/https://encrypted.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Robocopy+%22job+options%22+intitle%3Ajob+OR+intitle%3Ajobs&amp;oq=Robocopy+%22job+options%22+intitle%3Ajob+OR+intitle%3Ajobs&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=21451l25416l0l25659l28l25l0l0l0l0l254l2798l12.9.4l25l0" target="_blank">another search</a>, focusing only on Robocopy job options.  Posts at <a href="https://web.archive.org/web/20151210035401/http://serverfault.com/questions/55733/the-job-and-monitoring-options-of-robocopy" target="_blank">Serverfault</a> and <a href="https://web.archive.org/web/20151210035401/http://www.skonet.com/Articles_Archive/Robocopy_Job_Template.aspx" target="_blank">Skonet</a> seemed to suggest that I could work up my desired Robocopy command on the command line itself, and then add the /SAVE option to save it to a file, and that my job options would go into a separate file with an .RCJ extension.  I wasn't sure exactly how all that would work in practice, but at least there seemed to be a starting point.<br/>
<br/>
It appeared that the slash (/) character was the signal, in the job options file and probably also for Robocopy generally, indicating that one option had ended and a new one was starting.  So, for instance, if I gave the /XD command, I could then proceed to list a boatload of directories to exclude, without worrying too much about format -- putting them on the same line, putting each on a different line, or whatever.  Everything I wrote after /XD would be treated as another directory to exclude, until I came to another / command (e.g., /S) or else reached the end of the job options file.<br/>
<br/>
One thing that was not clear to me, from the foregoing options:  what if I had deleted a file on computer B, intending that synchronization should delete it on computer A as well?  GoodSync knew how to interpret such situations.  I suspected that Robocopy, run in a reciprocal setup starting with robocopy A &gt; B, would just restore the file from computer A to computer B.  That, as I found in tinkering, was what Beyond Compare might do.  In other words, there was a real difference between a backup program and a synchronization program.  The former would just make sure that the target contained what was on the source; the latter would keep track of what had been removed from each side, and would decide whether the removal occurred later than the most recent update of those files on the other side.  I could control such things manually, more easily in Beyond Compare than in robocopy, but for an automated solution I would need a program that would keep track of dates and times of deletions as well as of file changes.  I posted <a href="https://web.archive.org/web/20151210035401/http://forum.sysinternals.com/topic27728_post134253.html#134253" target="_blank">a question</a> on this, just to make sure I was understanding Robocopy correctly.  The response confirmed it, and suggested using regular synchronization programs.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Thank you.

**Anonymous**:
Robocopy is a great tool though we ran into an issue when we wanted to copy open files from users computers like PST file which are locked by outlook.  We found gscopypro which works exactly like robocopy but can copy open and locked files. It is like 30 dollars or so and if you need a lot of licenses, you can talk to the software vendor and they can work a deal easily to get a volume license.Give it a try.. the link ishttp://www.gurusquad.com/GSCOPYPRO

**Anonymous**:
We were looking for a tool to keep folders in sync.. based on the comment here we tried gscopypro from gurusquad and it was a great recommendation. It copies open files nicely.Thank you


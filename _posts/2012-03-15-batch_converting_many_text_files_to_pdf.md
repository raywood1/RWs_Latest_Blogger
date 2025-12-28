---
layout: post
title: "Batch Converting Many Text Files to PDF"
date: 2012-03-15
---

<div class="post-body">
<p>I had a bunch of .TXT files that I wanted to convert to PDF.  I had solved this problem previously, but it looked like I hadn't written it out clearly, so that's the purpose of this post.  This explanation includes solutions to several other sub-problems.  All together, the things presented here were useful for solving a variety of problems.<br/>
<br/>
First, I made a list of the files to convert.  My preferred way of doing this was to use DIR.  First, I would open a command window.  My preferred way of doing *that* was to use the "<a href="https://web.archive.org/web/20120701030819/http://raywoodcockslatest.blogspot.com/2011/05/asus-eee-pc-windows-7-tweaks.html" target="_blank">Open command window here</a>" context menu (i.e., right-click in Windows Explorer) option.  An alternative was to use Start &gt; Run &gt; cmd, but then I would have to navigate to the desired folder using commands like CD.<br/>
<br/>
The DIR command I usually used, to make a list of files, was DIR /s /a-d /b &gt; filelist.txt.  (Information on DIR and other DOS-style commands was available in the command window by typing the command followed by /?.  For example, DIR /? told me that that the /s option would tell DIR to search subdirectories.  A variation on the DIR command:  DIR *.txt /s /a-d /b.  The addition of *.txt, in that example, would tell DIR that I wanted a list of only the *.txt files in the folder in question (and its subfolders).  If I wanted to search a whole drive, I'd make it DIR D:\*.txt /s /a-d /b &gt; filelist.txt.  If I wanted to search multiple drives, I'd use &gt;&gt; rather than &gt; in the command for the second drive, so that the results would add to rather than overwrite the filelist.txt created by the preceding command.<br/>
<br/>
Using DIR that way could gather files from all over the drive.  Sometimes it was better to gather the files into one folder first, and then run my DIR command just on that folder.  An easy way of finding certain kinds of files was to use the <a href="https://web.archive.org/web/20120701030819/http://www.voidtools.com/" target="_blank">Everything</a> file finding utility, and then just cut and paste all those files from Everything to the desired folder.  For instance, a search in Everything for this:<br/>
<blockquote class="tr_bq">"see you tomorrow" *.txt</blockquote>would find all text files whose names contained that phrase.  Cutting and pasting that specialized list into a separate folder would quickly give me a manageable set of files on which I could focus my DIR command.  (There were other directory listing or printing programs that would also do this work; I just found them more convoluted than the simple DIR command.)<br/>
<br/>
Once I had dirlist.txt, I copied its contents into Excel (or I could have used Excel to open dirlist.txt) and used <a href="https://web.archive.org/web/20120701030819/http://raywoodcockslatest.blogspot.com/2012/02/batch-merging-many-scattered-jpgs-into_14.html" target="_blank">various formulas</a> to create the commands that would convert my text files into PDF.  The form of the command was like this:<br/>
<blockquote class="tr_bq">notepad /p textfile.txt</blockquote>I wasn't sure in the case of Notepad specifically, but I was able to run some programs (e.g., Word) from the command line by just typing one word (instead of e.g., "notepad.exe," or a longer statement of the path to the folder where e.g., winword.exe was located) because I had put the necessary <a href="https://web.archive.org/web/20120701030819/http://raywoodcockslatest.blogspot.com/2011/07/windows-7-batch-files-that-run-things.html" target="_blank">shortcuts in C:\Windows</a>.<br/>
<br/>
Those Notepad commands would send the text files to my default printer.  My default printer was <a href="https://web.archive.org/web/20120701030819/http://raywoodcockslatest.blogspot.com/2012/01/windows-7-batch-printing-html-mht-files.html" target="_blank">Bullzip</a>.  When I installed it, it gave me a separate shortcut leading to its options.  For this purpose, I set its options so that it did not open the document after creation (General tab), specified an output folder (General tab), and indicated that no dialogs or questions should be asked (Dialogs tab).<br/>
<br/>
I copied the desired commands from Excel to a Notepad text file and saved it with a .bat extension.  The rest of the file name didn't matter, but the .bat extension was important to make it an executable program.  In other words, if I double-clicked on PrintThoseFiles.bat (or if I selected PrintThoseFiles.bat and hit Enter) in Windows Explorer, the batch file would run and those commands would execute.  (I could also run the batch file from the command line, just by typing its name and hitting Enter -- which meant that I could have a batch file <a href="https://web.archive.org/web/20120701030819/http://raywoodcockslatest.blogspot.com/2011/07/windows-7-batch-files-that-run-things.html" target="_blank">running other batch files</a>.)<br/>
<br/>
So that pretty much did it for me.  I ran the batch file, running lots of Notepad commands, and it produced lots of good-looking PDFs.<br/>
<br/>
Please feel free to post questions or comments.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I didn't have a problem in this case, but for some purposes it can be helpful to slow down batch file execution.  Options for the START command include/WAITand various priority settings (e.g., /LOW) can help in such situations.

**raywood**:
A later postdiscusses the conversion of many DOC or other file formats to PDF.


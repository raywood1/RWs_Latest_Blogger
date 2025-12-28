---
layout: post
title: "Using Screenshots to Examine Many Files Quickly"
date: 2012-03-10
---

<div class="post-body">
<p>I had a couple of projects that called for a way to examine a large number of files.  It seemed that screenshots could help in those projects.  This post describes the techniques I used.<br/>
<br/>
<strong>EML Analysis</strong><br/>
<br/>
In one project, I was working with various email files that I had exported from Thunderbird.  These files had an EML extension.  Typically, if I viewed an EML file in Notepad, I would see various codes and other information that wouldn't be visible if I viewed it in an email program like Thunderbird.<br/>
<br/>
I was interested in seeing the header codes in these EML files.  Those codes appeared at the tops of the files.  I felt that I could probably see what I needed to see in the first screenful of a Notepad session, opened maximized.<br/>
<br/>
In other words, the concept was that I would open the EML file in Notepad; I would take a screenshot; I would save the screenshot; and then I would close the file and repeat the process with the next EML file on my list.  Then I would combine all those screenshots into one file, and flip through it or perhaps use other tools to analyze it further.  I wouldn't have to sit there, maintaining constant attention while the process continued in real time; I could just review the outcome afterwards.  (For some purposes, an alternative would have been to combine or select from the text, without a graphical view.)<br/>
<br/>
The first step was to build the list of EML files that I wanted to examine.  I moved them all into a single folder and <a href="https://web.archive.org/web/20190208143009/http://raywoodcockslatest.blogspot.com/2012/02/batch-merging-many-scattered-jpgs-into_14.html" target="_blank">used DIR and Excel</a> to give me the list and to convert it into a series of batch commands.  There was one such command for each such EML file.  Before running those commands, I had to open Notepad once, turn on its Format &gt; Word Wrap option, and then close it.  The format of the command was as follows:<br/>
<blockquote class="tr_bq">start /max notepad "D:\Folder Name\Email Name.eml"</blockquote>That command was sufficient to open the EML file.  Next, I needed to pause the system for a moment, so that the file would have time to come onscreen.  Among <a href="https://web.archive.org/web/20190208143009/http://stackoverflow.com/questions/1672338/how-to-sleep-for-5-seconds-in-windowss-command-prompt-or-dos" target="_blank">numerous suggestions</a>, I favored a command involving PING ("ping 1.1.1.1 -n 1 -w 1500 &gt; nul") because of its fine-tunable setting (in the example just given, 1500 milliseconds).  Unfortunately, that command's output component (" &gt; nul") would have prevented me from adding more commands on the same line.  So I had to go with "TIMEOUT /T 1" for a one-second delay.<br/>
<br/>
Next, I needed a command to take a snapshot.  It <a href="https://web.archive.org/web/20190208143009/https://www.google.com/search?q=%22command+line%22+screenshot&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">looked like</a> there were multiple options here.  I had already installed <a href="https://web.archive.org/web/20190208143009/http://www.nirsoft.net/utils/nircmd.html" target="_blank">NirCmd</a> and had found it useful for other things, so I used this command:<br/>
<blockquote>start NirCmd savescreenshot "D:\Folder Name\Screenshots\Email Name.png"</blockquote>NirCmd came with an option to copy its executable (nircmd.exe) to C:\Windows, so that this command could run without any need to specify the location of NirCmd, to put a copy of it in the current working folder, or to modify the computer's Path.  NirCmd wasn't saving to subfolders properly, so in the end I had to modify that part of the command.<br/>
<br/>
Finally, I needed a command to close Notepad.  <a href="https://web.archive.org/web/20190208143009/http://commandwindows.com/taskkill.htm" target="_blank">The advice</a> that worked for me was:<br/>
<blockquote class="tr_bq">taskkill /f /im notepad.exe</blockquote>Note that this would close all currently open Notepad sessions.  These three steps (i.e., open the EML in Notepad, take a picture with NirCmd, close Notepad) would give me a screenshot of the first screenful's worth of the file's contents.  Collectively, those screenshots would give me a visual impression of the various kinds of codes appearing at the start of my EML files.<br/>
<br/>
<a href="https://web.archive.org/web/20190208143009/http://commandwindows.com/command1.htm" target="_blank">I used &amp;&amp;</a> to combine multiple commands on the same line, as a single (long) batch command.  If that had failed, I could have added index columns next to the spreadsheet columns in which I built those two commands, with alternating even and odd numbers in those columns:  1 for the first Notepad command, 2 for the first NirCmd command, 3 for the second Notpad command, and so forth.  These index numbers would allow the various commands to be sorted into proper sequence in a single column, for copying and pasting into a batch file.<br/>
<br/>
In short, for each EML file, I combined four commands with &amp;&amp;, into a single long command like this:<br/>
<blockquote class="tr_bq">start /max notepad "D:\Folder Name\Email Name.eml" &amp;&amp; timeout /t 1 &amp;&amp; start NirCmd savescreenshot "Email Name.png" &amp;&amp; taskkill /f /im notepad.exe</blockquote>This gave me some PNGs.  Now there was the question of what to do with them.  One option was to simply stitch them together in a slideshow (using e.g., IrfanView) or a single PDF (using e.g., Acrobat).  I did <a href="https://web.archive.org/web/20190208143009/http://raywoodcockslatest.blogspot.com/2012/03/optical-character-recognition-freeware.html" target="_blank">a brief investigation</a> of OCR software for that purpose.  Ultimately, I just used IrfanView, without even creating a slideshow, to arrow down through those PNGs, one at a time, at whatever pace I chose.  So I could look at whether each page came through OK.<br/>
<br/>
<strong>PDF Analysis</strong><br/>
<br/>
In another project, I had a bunch of PDFs that I had created in a conversion process.  I wanted to check if the PDFs came through OK.  It would have been very slow to open them, one at a time, and page through them.  Combining them all into a single large PDF, which I could also page through, would have produced a huge file.  Also, if I was working with large PDFs or many PDFs (or both), I might have to look at huge numbers of pages.  Boredom or haste could lead me to flip past an important one-page document, while checking hundreds or thousands of less important pages.<br/>
<br/>
Based on various factors (including the number of PDFs, their importance, and the time available), I decided to examine just the first page of each PDF.  I might not be able to tell if the whole document printed properly, but at least I could eliminate those instances where printing failed completely.<br/>
<br/>
For this purpose, the process described in the previous section offered one possibility.  I could probably work up a set of commands to open a PDF, take a screenshot, and then close it, and then flip through the resulting screenshots.<br/>
<br/>
I did not actually pursue that approach in this case, however.  Instead, I wanted to see if I could convert the PDF documents to JPG and then flip through just the first page from each such document.  If I had a hundred documents to check, I would have a hundred pages to look at -- not a thousand.  <a href="https://web.archive.org/web/20190208143009/http://raywoodcockslatest.blogspot.com/2012/03/troubleshooting-some-options-for.html" target="_blank">A separate post</a> discusses that investigation.  The tool I chose was  <a href="https://web.archive.org/web/20190208143009/http://www.boxoft.com/pdf-to-jpg/" target="_blank">Boxoft PDF to JPG Converter</a>.  Another way to proceed might have been to split the PDFs first, using something like <a href="https://web.archive.org/web/20190208143009/http://www.pdfsam.org/" target="_blank">PDFsam</a>, and then combine the PDFs of each resulting first page into a larger PDF that I could flip through.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

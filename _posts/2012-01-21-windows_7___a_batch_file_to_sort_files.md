---
layout: post
title: "Windows 7:  A Batch File to Sort Files"
date: 2012-01-21
---

<div class="post-body">
<p>Since the mid-1980s, I had been using batch files to automate various tasks.  While a person could do some fancy things with batch files, mine tended to be very basic.  The simple commands that I had learned in DOS had mostly remained useful in Windows 3.1, 95, 98, XP, and 7.<br/>
<br/>
Batch files could be run in multiple ways.  If the file was already set up and if there was no desire to watch it perform, it would run by just double-clicking on it or selecting it and hitting Enter in Windows Explorer.  A batch file could also be run by being called from within another batch file or other program.  It was also possible to run a batch file by opening a command window, moving to the folder where the batch file was saved, and typing its name.<br/>
<br/>
Those and other aspects of batch files are described in <a href="https://web.archive.org/web/20160218055051/https://www.google.com/search?q=site%3Ahttp%3A%2F%2Fraywoodcockslatest.blogspot.com+%22batch+file%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">previous posts.</a>  It occurred to me, at this point, that those posts had not yet mentioned a certain kind of batch file that might save some people a lot of time.  This batch file would sort files into subfolders according to their names.<br/>
<br/>
Consider, for instance, the situation in which I would have a thousand files with names like these:<br/>
<blockquote>Letter to Jones cbgb.doc<br/>
Letter to Jones cbgb.pdf<br/>
Letter to Jones cbgb A.pdf<br/>
Letter Dec.23 to Jones.txt<br/>
1988-12-23 Letter to Jones.doc<br/>
1993-06-23 Letter to Jones.doc</blockquote>A real mess.  How could I possibly find which of these, if any, were duplicates?  And then, once I got past that, how could I sort them into appropriate folders?<br/>
<br/>
I had been <a href="https://web.archive.org/web/20160218055051/http://raywoodcockslatest.blogspot.com/2011/05/data-nightmare-reconciling-two-hard.html" target="_blank">struggling</a> with the first of those two questions for some time.  I had some partial solutions.  For instance, note that the first two items in this list have the same names but different extensions.  I could convert one to the other format -- printing the .doc file to PDF, or using Acrobat or some other program to save the PDF in .doc format -- and then I could open both of them and eyeball them for differences.  Or, in a different scenario, if I knew they were different, but they were scattered all over my hard drive, I could do a search that would ignore extensions or that would focus on file dates, using a program like <a href="https://web.archive.org/web/20160218055051/http://www.bigbangenterprises.de/en/doublekillerpro/comp.htm" target="_blank">DoubleKiller Pro</a>, and decide which if any I could safely delete.  Similarly, between the second and third items in the list, I could do a DoubleKiller search for near or exact duplicates, or a search that would focus on most but not all of the filename.<br/>
<br/>
Once I had reduced the number of possible duplicates, I would want to rename files so that they would all follow a certain pattern.  The last two in the list show the pattern that I would want to use for renaming the others.  In a more complicated form that might be useful for some purposes, the pattern could be year-month-day-hour-minute-item-title-version.extension, like this:<br/>
<blockquote>1988-12-23 11.23 01 First Item Produced at 11-23 AM A.txt</blockquote>That format would have two advantages:  it would automatically sort and display files in chronological order, in Windows Explorer and other programs, and it would make it easier for my batch file to sort files into subfolders by year, month, and so forth.  To get files into that format, as more fully explained <a href="https://web.archive.org/web/20160218055051/http://raywoodcockslatest.blogspot.com/2011/04/using-spreadsheet-to-rename-thousands.html" target="_blank">elsewhere</a>, I would use tools like Excel and commands like DIR -- perhaps with the aid of something like <a href="https://web.archive.org/web/20160218055051/https://www.google.com/search?q=%22Bulk+Rename+Utility%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">Bulk Rename Utility</a>, whose initially discouraging interface had proved easier to use than I would have expected.<br/>
<br/>
Once I got the files into the proper format, it would be time to work up my sorting batch file.  I would do that in a program like Notepad -- not Microsoft Word or some other word processor, since they would tend to use characters that would not be understood by the command processor.  Smart quotation marks are an example of that.<br/>
<br/>
The concept in this example is that I would have top-level folders for decades, subfolders for years, and sub-subfolders for months, like this:<br/>
<blockquote>1990s<br/>
--1991<br/>
--1992<br/>
----1992-01<br/>
----1992-02</blockquote>and so forth.  It would be fairly easy to write a batch file, perhaps with the aid of Excel, that could automate the process of creating those folders (or any sequential set of empty folders), if necessary.  The commands that I would use in that batch file would also tend to be the commands that I would use in the sorting batch file.  They would include examples like these:<br/>
<blockquote><strong>D:</strong>     move to drive D<br/>
<br/>
<strong>cd \</strong>   change directories to the root folder in the current drive<br/>
<br/>
<strong>cd ..</strong>  change to the parent folder<br/>
<br/>
<strong>cd Subfolder</strong>    change to Subfolder (this command works only if Subfolder is directly below the current folder, which can be verified by typing DIR)<br/>
<br/>
<strong>md Subfolder</strong>     make directory called Subfolder immediately below the current folder<br/>
<br/>
<strong>move document.txt D:</strong>    move document.txt to the currently active folder on drive D<br/>
<br/>
<strong>*.txt     </strong>refers to all files whose names end with a .txt extension<br/>
<br/>
<strong>199?.doc</strong>     refers to all files whose names start with 199, followed by one other character, with a .doc extension (e.g., 1991.doc, 199A.doc</blockquote>More information was available for commands by typing the command name followed by /? (example:  move /?) at the command prompt.  They could be used in combination.  For instance, "move *.txt D:\Folder\Subfolder" would move all files with a .txt extension from the current directory to the Subfolder child of Folder on drive D.<br/>
<br/>
The sorting batch file could then be structured like this:<br/>
<blockquote>:: BATCH FILE TO SORT FILES<br/>
<br/>
D:<br/>
<br/>
:: ********** MOVE TO DECADE GROUPS **********<br/>
<br/>
cd "\WORKSPACE"<br/>
move /-y 199?-*.* 1990s<br/>
move /-y 200?-*.* 2000s<br/>
move /-y 201?-*.* 2010s<br/>
(etc.)<br/>
<br/>
:: ********** MOVE TO INDIVIDUAL YEARS **********<br/>
<br/>
cd "\ARCHIVES BY YEAR\1990s"<br/>
move /-y 1990-*.* 1990<br/>
move /-y 1991-*.* 1991<br/>
move /-y 1992-*.* 1992<br/>
(etc.)<br/>
<br/>
:: ********** MOVE TO MONTH FOLDERS **********<br/>
<br/>
cd "\ARCHIVES BY YEAR\1990s\1990"<br/>
move /-y 1990-00-*.* 1990-00<br/>
move /-y 1990-01-*.* 1990-01<br/>
move /-y 1990-02-*.* 1990-02<br/>
(etc.)</blockquote>Its first line is a comment.  That is, it begins with a double colon (::) and, as such, would be ignored by the command processor.  It is just there for the reader's information.  The next line moves us to drive D.  Then another comment, indicating that now we are going to move all of the files to decade folders (with names like "1990s" and "2000s"), according to the first three characters of their filename.  The following commands do that, after a "cd" command that moves us to the Workspace folder where the files to be sorted are located.  (The quotation marks around "Workspace" are unnecessary, but would be necessary if that folder's name had a space in it.)  <br/>
<br/>
Then the batch file contains another section, structured the same, that moves files to subfolders based on their year.  For instance, "move /-y 1990-*.* 1990" means "move (but ask me to confirm before overwriting) all files with names that begin with 1990-, followed by any other characters, and with any extensions, to the folder named 1990."  So the files that would have been sorted into the 1990s folder are now going to be subsorted into the 1990, 1991, 1992 ... folders.  Finally, the months folders:  all of the files that wound up in the 1991 folder are now going to be sorted into the folders for months 0, 1, 2 ...  (I would allow a 0 folder for those files that could be traced to sometime in the year, but not to a specific month.)<br/>
<br/>
And that's basically it.  A lot of information in a brief presentation, but hopefully it provides some ideas for how a batch file could be used to automate the sorting of any number of files, on any number of occasions.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
P.S.  Be careful.  Batch files are really powerful.  It goes without saying that you should have a complete system backup before starting.  I would also recommend keeping a copy of that backup for weeks (months, if possible) so that you can allow plenty of time to pass before you become completely committed to what your batch file tinkering has wrought.  It can take a long time to discover that things were moved or deleted in ways that you did not expect.


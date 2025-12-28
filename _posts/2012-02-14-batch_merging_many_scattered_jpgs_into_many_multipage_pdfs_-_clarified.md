---
layout: post
title: "Batch Merging Many Scattered JPGs into Many Multipage PDFs - Clarified"
date: 2012-02-14
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20141124092347/http://raywoodcockslatest.blogspot.com/2012/01/batch-merging-many-scattered-jpgs-into.html" target="_blank">recently streamlined</a> a spreadsheet-oriented technique for working up file names and batch commands to merge multiple JPGs into single- or multi-page PDFs.  I had yet another task calling for that process.  This post presents the same steps as in that previous writeup, but in clearer and more organized terms.  The various steps are described in different terms in <a href="https://web.archive.org/web/20141124092347/http://raywoodcockslatest.blogspot.com/2012/01/batch-merging-many-scattered-jpgs-into.html" target="_blank">the previous post</a> and in its much more <a href="https://web.archive.org/web/20141124092347/http://raywoodcockslatest.blogspot.com/2012/01/batch-merging-many-scattered-jpgs-into.html" target="_blank">convoluted predecessor</a>.  Note that the simplification of steps here yields a longer explanation.<br/>
<br/>
<strong>Generate the Input PDF Filenames</strong><br/>
<br/>
In this discussion, the project had already been brought to the point where there was a spreadsheet containing the names of JPGs to be converted to PDF.  (A list of such files could come from a command like DIR D:\*.jpg /s /a-d /b &gt; JPGLIST.TXT.)  In that spreadsheet, row 1 was reserved for column names (e.g., "Original Filename," "Path").  The name of the first file to be converted appeared in cell A2 (e.g., "Test File.jpg"), and the others appeared below it in column A.<br/>
<br/>
Column B was used to calculate the endpoint of the path (e.g., "D:\Folder 1\Test File.jpg").  This calculation required or at least benefited from the use of a REVERSE function.  The REVERSE function was created by inserting the following text into a module:<br/>
<blockquote>Function Reverse(Text As String) As String<br/>
Dim i As Integer<br/>
Dim StrNew As String<br/>
Dim StrOld As String<br/>
StrOld = Trim(Text)<br/>
For i = 1 To Len(StrOld)<br/>
StrNew = Mid(StrOld, i, 1) &amp; StrNew<br/>
Next i<br/>
Reverse = StrNew<br/>
End Function</blockquote>To create the module, I closed all Excel files other than the one being worked on.  I went into Tools &gt; Macro &gt; Visual Basic Editor &gt; Insert &gt; Module.  I pasted the text there.  I went to to File &gt; Close and Return to Microsoft Excel.  The formulas in the next several cells were then as follows:<br/>
<blockquote>B2:  =LEN(A2)-FIND("\",REVERSE(A2))+1<br/>
C2:  =LEFT(A2,B2)<br/>
D2:  =MID(A2,B2+1,LEN(A2))</blockquote>I was reconstructing some of these steps after the fact; hopefully I was not misstating anything or leaving anything out of this description.  I focused on the formulas for row 2 because, when I was done filling out row 2, it would be easy to copy all of its formulas at once to fill the spreadsheet, so that the same formulas would be applied to the filenames in rows 3, 4, 5 et seq.<br/>
<br/>
The next step was to identify which files I wanted to convert.  I was able to use the spreadsheet to help in this process.  For example, I had files with names like these:<br/>
<blockquote>Test File page 01.jpg<br/>
Test File page 02.jpg</blockquote>I could determine that these belonged together by using a column that showed these filenames without the ending X characters.  That column would use a command like =RIGHT(D2,$E$1), where I would put a number in E1.  The number I used in this example was 12, because I would have to eliminate 12 characters from the right end of "Test File page 01.jpg" to get the name that I wanted to give to the new PDF, which would be simply "Test File."  I manually entered 12 in cell E2.  I filtered the rows so that the ones with numbers in column E would not show, so as to reduce clutter.  I repeated this process until each row had a number in column E, indicating how many characters I had to trim from the right end of the filename to get a common stem.  Then cell F2 contained =LEFT(D2,LEN(D2)-E2), to produce the stem filename.  So, for example, if there were two pages that had to go into Test File.pdf, then (assuming I had sorted my spreadsheet correctly), the contents of cells F2 et seq. would look like this:<br/>
<blockquote>F2:  Test File<br/>
F3:  Test File<br/>
F4:  Another File</blockquote>and so forth, continuing down the list, so that each JPG would be assigned to a stem filename.  I discovered at this point that I had brought over a bunch of JPGs that did not belong in a multipage PDF, or at least I could not be sure of it.  I put these back where they came from, and thus had a smaller set of files to work on.<br/>
<br/>
Now I could sort the spreadsheet to insure that the JPGs I wanted to merge into a specific PDF would be next to each other.  Once I had the files sorted into the desired order, I used column G as an Index column, numbering each row in that order.  This column would be useful to restore the desired order if I resorted the spreadsheet for some reason, and it would also provide the key ingredient in the unique filename that I was about to calculate.  (To generate an index number, I used either a +1 formula, incrementing the number in the preceding row by 1, followed by an Edit &gt; Copy, Edit &gt; Paste Special &gt; Values sequence to convert those formulas to fixed numbers that would not be affected by resorting the spreadsheet; or, easier, I entered 1 in the first row, 2 in the second row, and then highlighted the cells to be filled and used Edit &gt; Insert &gt; Series to add the sequential numbers.)  Then I used columns G through I to calculate a simple, unique filename and produce a renaming command:<br/>
<blockquote>G2:  unique Index number<br/>
H2:  ="Input_"&amp;REPT("0",4-LEN(G2))&amp;G2&amp;".pdf"<br/>
I2:  ="ren "&amp;CHAR(34)&amp;A2&amp;CHAR(34)&amp;" "&amp;H2</blockquote>Cell H2 would produce the file name of "Input_0001.pdf."  (More or fewer digits could be appropriate, depending on the number of files involved.)  This name worked for me because a search of my files verified that my computer contained no other files whose names began with Input_.  Otherwise, a different name might have been advisable.  Cell I2 would produce a command that would rename Test File page 01.jpg to be Input_0001.pdf.  (Of course, this wasn't a conversion.  IrfanView would be doing that.  This was just a translation of file names, to make subsequent steps easier.)<br/>
<br/>
Then, as usual, I copied these commands from row 2 down to fill the remaining rows of the spreadsheet.  Next, I copied all of the commands from column I into Notepad, saved that file with a .bat extension (e.g., "Renamer.bat"), and ran it in Windows Explorer.  That renamed all of the JPGs that I hoped to merge into multipage PDFs.  (Obviously, I had a backup.)<br/>
<br/>
Now I would use column J for commands to move all those JPGs to a single folder.  (I did the renaming before the moving in case I had two separate sets of incoming JPGs with the same name, such as D:\Folder A\Test File page 01.jpg and E:\Folder R\Test File page 01.jpg.)  In my actual example, the files were all moved to V:\Workspace, so my command in cell J2 looked like this:<br/>
<blockquote>J2:  ="move /-y "&amp;CHAR(34)&amp;C2&amp;H2&amp;CHAR(34)&amp;" V:\Workspace"</blockquote>I combined the commands in column J into another batch file, Mover.bat, and used it to move all those renamed JPGs to V:\Workspace.  Now that they were together, I could use IrfanView's File &gt; Batch Conversion/Rename option to convert all those JPGs to single-page PDFs.  I output those PDFs to V:\Workspace and then removed the JPGs from V:\Workspace to V:\Workspace\Original JPGs, where they would probably not be needed further.<br/>
<br/>
<strong>Generate the File Value Lines</strong><br/>
<br/>
So now I had files starting with Input_0001.pdf in V:\Workspace.  The project now was to merge those single-page input PDFs into multipage output PDFs.  In column K, I entered a number indicating where each input PDF should go.  As I could see from column F (above), the files that used to be called Test File page 01.jpg and Test File page 02.jpg, which had now been converted to uniquely named single-page PDFs, were both going to end up in Output_0001.pdf, so both of those had the number 1 in column K.   I needed to pad out that number so that the resulting filename would sort correctly.  So the next formulas were as follows:<br/>
<blockquote>K2:  =LEFT(H2,11)&amp;"pdf"<br/>
L2:   =REPT("0",4-LEN(K2))&amp;K2</blockquote>But I wasn't ready, yet, to generate the ultimate Output PDF files.  I needed to make sure that PDFsam (below) would have all the instructions needed to insert multiple single-page PDFs into one Output PDF.  Those instructions would come from lines of XML code, one line per input PDF.  The lines of XML code would be combined into a smaller number of FileValueLines files.  In my example, the instruction lines for the erstwhile Test File page 01.jpg and Test File page 02.jpg files (now called Input_0001.pdf and Input_0002.pdf) would both go into a single FileValueLines file.  A FileValueLines file could contain any number of lines of XML code; it just depended on how many single-page PDFs were going to be combined into it.  What I needed, then, was the command that would shovel those XML code lines into the appropriate FileValueLines files.  The next formulas in my spreadsheet looked like this:<br/>
<blockquote>M2:  ="FileValueLines_"&amp;L2<br/>
N2:  ="echo ^&lt;file value="&amp;CHAR(34)&amp;"V:\Workspace\PDF\"&amp;H2&amp;CHAR(34)&amp;" /^&gt; &gt;&gt; "&amp;M2</blockquote>and cell N2 produced this command:<br/>
<blockquote>echo ^&lt;file value="V:\Workspace\PDF\Input_0002.pdf" /^&gt; &gt;&gt; FileValueLines_0001</blockquote>Note that this command assumed that the PDFs created by IrfanView were in a folder called V:\Workspace\PDF.  I filled the lower rows of the spreadsheet with these formulas and copied the commands in column N into a new Notepad file called _ValueMaker.bat.  I ran _ValueMaker.bat in V:\Workspace.  It produced 545 FileValueLines files in V:\Workspace, as expected.  (I added an underscore before the file's name so that it would appear near the top of the potentially cluttered list of files in V:\Workspace.)<br/>
<br/>
This was a point of transition.  Until now, I had been working with a total of 3,894 spreadsheet rows, one for each of the 3,894 JPGs that I wanted to combine into multipage PDFs.  Each of those 3,894 JPGs (converted into single-page PDFs called Input_0001.pdf et seq.) was represented in exactly one File Value line.  Those 3,894 File Value lines were now contained within a total of 545 FileValueLine_ files.  In other words, we were transitioning from a focus on 3,894 individual JPGs to a focus on 545 multipage PDFs.<br/>
<br/>
<strong>Building the XML Files</strong><br/>
<br/>
The 545 FileValueLines files (FileValueLines_0001 and so forth) needed more lines before they would function.  To add those lines, I needed a new spreadsheet.  I started this one with a list of the FileValueLines files I had just created.  (A command like "dir FileValueLines* /b /a-d &gt; _FVLlist.txt" would produce that list.)  In other words, column A contained the list of the new FileValueLines files.  Next, I calculated the name of the resulting XML file, and then wrote the formula that would create those XML files:<br/>
<blockquote>B2:  =RIGHT(A2,4)<br/>
C2:  ="XMLfile_"&amp;B2&amp;".xml"<br/>
D2:  ="copy /b _Header.txt+"&amp;A2&amp;"+_Tailer.txt "&amp;C2</blockquote>That formula in D2 produced the command that I would need to create the complete XML files:  "copy /b _Header.txt+FileValueLines_0001+_Tailer.txt XMLfile_0001.xml."  This command called for me to create just one _Header.txt and one _Tailer.txt file that would be added to the start and end of each of my XML files.  The _Header.txt file read as follows:<br/>
<blockquote>&lt;?xml version="1.0" encoding="UTF-8"?&gt;<br/>
&lt;filelist&gt;</blockquote>I saved those two lines in a new _Header.txt file.  It was important to make sure the file ended on a blank line.  In other words, if I moved my cursor down to the end of _Header.txt, it needed to be on the line below &lt;filelist&gt;, not at the end of the line containing &lt;filelist&gt;.  The same was true for _Tailer.txt, which contained this line:<br/>
<blockquote>&lt;/filelist&gt;</blockquote>Once _Header.txt and _Tailer.txt existed, I could run the commands contained in column D.  I copied those 545 commands into a new batch file called _Builder.bat and ran it.  That gave me 545 XML files, starting with XMLfile_0001.xml.  Again, V:\Workspace was filling up, so I moved the no longer needed FileValueLines files to their own archival subfolder.<br/>
<br/>
<strong>Generating the PDFsam Commands</strong><br/>
<br/>
At this point, I would use a batch file to generate batch files.  This would call for the same kind of process as above:  a header text file (but no tailer) containing lines that would be standard in all of these batch files, combined with another text file containing unique commands.  In this new _HeaderB.txt file, I placed these lines:<br/>
<blockquote>@echo off<br/>
<br/>
set JAVA=%JAVA_HOME%\BIN\JAVA<br/>
<br/>
set JAVA_OPTS=-Xmx256m  -Dlog4j.configuration=console-log4j.xml<br/>
<br/>
set CONSOLE_JAR="C:\Program Files  (x86)\pdfsam\lib\pdfsam-console-2.3.1e.jar"<br/>
<br/>
@echo on</blockquote>Apparently these first lines set up a few essential Java variables.  (In case of difficulty here, as elsewhere, see <a href="https://web.archive.org/web/20141124092347/http://raywoodcockslatest.blogspot.com/2012/01/batch-merging-many-scattered-jpgs-into.html" target="_blank">the preceding post</a>.)  The second part of the batch file -- the unique command -- would tell PDFsam (below) what to do.  The command looked like this:<br/>
<blockquote>E2:  ="echo %%JAVA%% %%JAVA_OPTS%% -jar %%CONSOLE_JAR%% -l V:\Workspace\"&amp;C2&amp;" -o V:\Workspace\Merged\Output_"&amp;B2&amp;".pdf concat &gt;&gt; Command_"&amp;B2&amp;".txt"</blockquote>Basically, this would produce a command that said, "Write a command that will create Output_*.pdf, and put that command in a file called Command_*.txt."  In other words, that spreadsheet formula in cell E2 produced a command that looked like this:<br/>
<blockquote>echo %%JAVA%% %%JAVA_OPTS%% -jar %%CONSOLE_JAR%% -l V:\Workspace\XMLfile_0001.xml -o V:\Workspace\Merged\Output_0001.pdf concat &gt;&gt; Command_0001.txt</blockquote>Spreadsheet column E gave me 545 variations on that command.  I copied them all and ran them in a new batch file called _Texter.bat.  The resulting 545 Command_*.txt files would have to share V:\Workspace with my preexisting XMLfile_*.xml files; both would be needed shortly.<br/>
<br/>
Now it was time to combine _HeaderB.txt and Command_*.txt into a batch file that would run PDFsam and produce an multipage Output PDF.  This was easy enough:<br/>
<blockquote>F2:  ="copy /b _HeaderB.txt+"&amp;RIGHT(E2,16)&amp;" Ready_"&amp;B2&amp;".bat"</blockquote>The 545 versions of that command, run via _Commander.bat, created 545 Ready_*.bat files, each containing the header information from _HeaderB.txt plus the single command line from Command_*.txt.  Now I was done with the Command_*.txt files, and could archive them.<br/>
<br/>
<strong>Final Run:  Creating the Merged Output PDFs</strong><br/>
<br/>
If I double-clicked on one of those Ready batch files, it would run and produce a final merged Output.pdf.  But I wanted to run them all at once.  So, back to the spreadsheet:<br/>
<blockquote>G2:  ="call "&amp;RIGHT(F2,14)&amp;" &gt;&gt; _Errorlog.txt"</blockquote>That produced "call Ready_0001.bat &gt;&gt; _Errorlog.txt."  I copied the 545 CALL commands from column G into a file called _Runner.bat and -- you guessed it -- I ran it.  It took a few minutes, but it produced 542 merged PDFs.  Not 545.  I searched _Errorlog.txt for occurrences of "Error."  Sure enough, three occurrences.  In each case, the error was the same:  "Input_0838.pdf (and Input_0947.pdf, and Input_1090.pdf) not found as file or resource."  Apparenly PDFsam had not gone ahead to create the Output PDFs anyway, without the offending Input file.  I checked and, indeed, those three files were not included among my input.  I was not sure what happened to them.  They appeared to have disappeared during this process.  I made a note to retrieve them from backup.<br/>
<br/>
Otherwise, though, the process seemed to have succeeded.  Spot checks indicated that I had working multipage PDFs.  Now it was time to rename them to be something other than Output_0001.pdf etc.  I went back to my first spreadsheet, saved it, and went to work on a temporary copy of it.  Specifically, I converted all of its formulas to numerical values.  (In Excel 2003, this involved going to the top left corner, selecting the whole spreadsheet, and using the Edit &gt; Copy, Edit &gt; Paste Special Values combination.)  With that done, I was free to delete and rearrange columns as needed, without having cells recalculate in undesirable ways.  I kept only columns C (showing the original source folder), F (showing the name I had chosen for the combined output PDF), and L (showing the output file number).  I rearranged those columns in reverse order, so that the output file number column could function as a rather redundant index.  I went to the second spreadsheet and, working likewise on a copy of that, deleted all columns except column B, containing the output file number.  In an adjacent column, I used VLOOKUP to look up the filenames, from the other spreadsheet, to which these Output_0001.pdf etc. files should be renamed.<br/>
<br/>
Through such steps, I renamed these files.  Yet something went wrong.  Due to distraction and time delay during the last stages of this process, somehow the renaming did not bring me back to a coherent set of files.  Spot checks indicated that the ones that did rename were renamed correctly.  That is, if a file wound up being renamed as Letter to Joe, it did seem to be exactly that.  But I was left with 60 files -- more than 10% of the total -- that did not rename at all.  There may have been a way to fix them through the spreadsheet, but I had run out of time for the project.  Under the circumstances, I defaulted to putting those files aside into a separate folder, pending a future manual renaming effort.<br/>
<br/>
The process described in this post did seem to work.  But its numerous steps continued to hold the threat of something going wrong, somewhere along the line, and being difficult to retrace.  This did not seem to be nearly the last word on batch merging scattered JPGs into multipage PDFs.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
As it turns out, the problem with those 60 files was that I made the mistake of renaming before moving, instead of afterwards.  There were duplicate filenames, so the batch file didn't rename until I moved some of the renamed files out of that folder.

**raywood**:
It looked likeKaren's Directory Printerwould provide an alternative to DIR for some purposes.

**raywood**:
As described near the bottom ofanother post, I later found pdftk much easier to use than PDFsam.

**raywood**:
A later postpulls together some of these remarks in a more summary fashion.


---
layout: post
title: "Batch Merging (Combining, Concatenating) PDFs from the Command Line"
date: 2011-04-18
---

<div class="post-body">
<p>I was using Windows 7.  I had a bunch of JPGs that were images of successive pages in a document.  In other words, when the document was scanned, each page was saved to its own separate file.  They were named Page01.jpg, Page02.jpg, Page03.jpg, and so forth.  I had converted these JPGs to PDF, thinking that would help me toward my goal.  The goal was to combine them all -- whether as JPGs or PDFs -- into one PDF file containing the entire document.  I had a large number of documents like this, each consisting of several pages, all together in one directory.  It was too big a job to do manually.  But could I automate it?  This post describes my efforts to that end.<br/>
What I was looking for was, somehow, a program or script that could recognize the differences among these files in a directory, and combine only the ones that should be combined:<br/>
<blockquote>Doc1Page1<br/>
Doc1Page2<br/>
Doc2Page1<br/>
Doc3Page1<br/>
Doc3Page2</blockquote>so that I would wind up with this:<br/>
<blockquote>Doc1 (pages 1 &amp; 2)<br/>
Doc 2 (page 1)<br/>
Doc 3 (pages 1 &amp; 2)</blockquote><a href="https://web.archive.org/web/20150516030027/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=TlV&amp;as_qdr=all&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=batch+%22combine+pdfs%22+OR+%22combine+pdf%22+%22command+line%22+freeware+-%22advanced+pdf+merger%22+-%22pdf+combine%22&amp;tbs=search%3Fas_&amp;lr=&amp;as_filetype=&amp;aq=f&amp;aqi=&amp;aql=&amp;oq=">A search</a> led to <a href="https://web.archive.org/web/20150516030027/http://itextpdf.com/itext.php">iText</a>, which looked sleek and got some good recommendations but unfortunately (a) did not appear to be available in a Windows/DOS version and (b) was not for end users.  In other words, I had no idea what to do with it.  A <a href="https://web.archive.org/web/20150516030027/http://www.techsupportalert.com/content/best-free-pdf-tools.htm#Quick_Selection_Guide">Gizmo's Freeware</a> article did not seem to identify programs that could do this.  The article led me to <a href="https://web.archive.org/web/20150516030027/http://www.pdfill.com/pdf_tools_free.html">PDFill PDF Editor</a> as its first choice for an all-around freeware PDF solution.  There, I went to the <a href="https://web.archive.org/web/20150516030027/http://www.pdfill.com/pdftool_merge.html">Merge PDF Files</a> tool.  Its <a href="https://web.archive.org/web/20150516030027/http://www.pdfill.com/pdf_batch_command.html">batch command option,</a> available only in its $20 paid version, looked like it would come close to doing what I wanted.  The example they gave looked like this:<br/>
<blockquote>"C:\Program Files\PlotSoft\PDFill\PDFill.exe" MERGE Input1.pdf Input2.pdf Input3.pdf Output.pdf</blockquote>With many files or long filenames, that approach would run into limits on how long a command could be.  I suspected I could vary their command with standard DOS input options, which I vaguely recalled would look like this:<br/>
<blockquote>"C:\Program Files\PlotSoft\PDFill\PDFill.exe" MERGE &lt; inputfilelist.txt</blockquote>So then the challenge would be to automate the process of identifying filenames that would belong together in the same inputfilelist.txt file:  Doc1Page1.pdf and Doc1Page2.pdf would be in Doc1inputfilelist.txt, whereas Doc3Page1.pdf and Doc3Page2.pdf would be in Doc3inputfilelist.txt.  Then all I'd have to do would be to construct a batch file with lines like this:<br/>
<blockquote>"C:\Program Files\PlotSoft\PDFill\PDFill.exe" MERGE &lt; Doc1inputfilelist.txt<br/>
"C:\Program Files\PlotSoft\PDFill\PDFill.exe" MERGE &lt; Doc3inputfilelist.txt</blockquote>I wasn't sure if PDFill would allow me to select a name for each resulting output file, or how that would work.  With a large number of files, that manual process could be very time-consuming.  I could also look into other possibilities, like going back to the JPGs from which I had created these PDFs and merging them into multipage TIF files that I could then convert into multipage PDFs.<br/>
<br/>
These were the steps I would have to pursue as this project continued.  But I had to shelve it for now, to deal with other things.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**shapeless - lacklogic**:
Ray, did you ever find a good solution to your "Batch PDF Merge" idea?  ..via a CSV, text file, or command line method?Thanks!

**raywood**:
Sorry, I didn't receive or overlooked the notification of this comment.  But no, I haven't solved that problem yet, sad to say.

**raywood**:
Now I do havea more recent postattacking this kind of problem.

**raywood**:
Another subsequent postcontains a further update.


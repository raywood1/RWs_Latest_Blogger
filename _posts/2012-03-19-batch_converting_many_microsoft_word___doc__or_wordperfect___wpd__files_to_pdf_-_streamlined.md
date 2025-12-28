---
layout: post
title: "Batch Converting Many Microsoft Word (.doc) or WordPerfect (.wpd) Files to PDF - Streamlined"
date: 2012-03-19
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20120701030814/http://raywoodcockslatest.blogspot.com/2012/03/batch-converting-many-microsoft-word.html" target="_blank">previously</a> figured out a semi-automated command-line solution to the question of how to convert many Microsoft Word docs to PDF.  This process involved automatically opening, printing, and closing the files, one at a time, in Word.  Now I had another set of documents to convert.  So the first purpose of this post was to boil down what I wrote up in that previous post.<br/>
<br/>
The second purpose was to see if the same approach would work for WordPerfect (.wpd) docs.  The logic was that Word could handle WPDs, and that it would automatically convert them upon opening.  So it seemed that I should be able to run an almost identical command to convert a document, regardless of whether it was a WPD or a DOC (or, presumably, an RTF, or a DOCX, etc.).<br/>
<br/>
The command I used was long, but not super-complicated.  This was the one-line command I used to convert all of the DOC files in a folder:<br/>
<blockquote>FOR /F "usebackq delims=" %%g IN (`dir /b "*.doc"`) DO "C:\Program Files (x86)\Microsoft Office\Office11\winword.exe" "%%g" /q /n /mFilePrintDefault /mFileExit &amp;&amp; TASKKILL /f /im winword.exe</blockquote>Its success depended on several factors.  Some, such as cleaning out the %Temp% folder, are detailed in the previous post.  I structured the command with the aid of <a href="https://web.archive.org/web/20120701030814/http://stackoverflow.com/questions/9744520/batch-combining-two-pieces-of-text-on-one-line-in-a-loop" target="_blank">early answers</a> to a question I posted.<br/>
<br/>
It is worth noting that the command could be used to specify various kinds of files.  This example referred to *.doc (that is, to all .doc) files in the folder in which it the command was run.  (It goes without saying that it would be wise to have a backup before fooling with this or any command.)  Also, I set my PDF printer (<a href="https://web.archive.org/web/20120701030814/http://www.bullzip.com/products/pdf/info.php" target="_blank">Bullzip</a> &gt; Options &gt; General and Dialogs tabs) to operate without asking me any questions.  Note, further, that the precise location of winword.exe would vary, from one system to another.  Of course, saving the command as the entire contents of an executable batch file was just a matter of putting it into a text file with a .bat extension, and then saving and running that .bat file.<br/>
<br/>
I tried modifying the command to refer to .wpd rather than .doc, and ran it in a folder full of WPDs.  It worked.  Then, as detailed <a href="https://web.archive.org/web/20120701030814/http://raywoodcockslatest.blogspot.com/2012/03/troubleshooting-some-options-for.html" target="_blank">elsewhere</a>, I did a file count to verify that I had the right number of resulting PDFs, and ran <a href="https://web.archive.org/web/20120701030814/http://www.boxoft.com/pdf-to-jpg/" target="_blank">Boxoft PDF to JPG Converter</a> to do a quick test, highlighting files that didn't look right.  This process worked with WPDs.<br/>
<br/>
I wasn't sure how much further the command could be extended.  A test with PPTs (using PowerPoint rather than Word) failed.  In response to my <a href="https://web.archive.org/web/20120701030814/http://stackoverflow.com/questions/9763895/batch-file-to-convert-doc-files-to-pdf" target="_blank">follow-up question</a> regarding the possibility of specifying the filetype on the command line (by typing e.g., CONVERTER.BAT DOC), it was suggested that I simply experiment to see if I could get the variable ("DOC," in that example) to work.  I didn't have any more files to work on at the moment, so that investigation would have to wait until later.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
Another postdescribes how I also used this approach for mass-converting WordStar (.ws) files to PDF.

**raywood**:
Note that the command shown above was designed for use in a batch file, not directly on the command line.  The other post just referenced, regarding WordStar, clarifies this.


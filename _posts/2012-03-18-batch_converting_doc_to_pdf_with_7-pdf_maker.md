---
layout: post
title: "Batch Converting DOC to PDF with 7-PDF Maker"
date: 2012-03-18
---

<div class="post-body">
<p>I had some Microsoft Word .doc files.  I wanted to convert them to PDF.  I wanted to be able to do this from the command line, so as to reach into different folders and process large numbers of them at once.<br/>
<br/>
I went into Softpedia and did <a href="https://web.archive.org/web/20151205114351/http://www.softpedia.com/dyn-search.php?search_term=pdf+doc+convert&amp;Submit=Search&amp;license_filter=1&amp;results_per_page=30&amp;lastupd_filter=0&amp;sort_field=3" target="_blank">a search</a>.  It came up with numerous free programs for this purpose.  I chose <a href="https://web.archive.org/web/20151205114351/http://www.softpedia.com/get/Office-tools/PDF/7-PDF-Maker.shtml" target="_blank">7-PDF Maker</a>.  It had a pretty good rating, as Softpedia programs go (4.0 stars; 16,001 downloads), and it did offer a command-line option.  I also downloaded <a href="https://web.archive.org/web/20151205114351/http://www.7-pdf.de/fileadmin/manuals/maker/english.pdf" target="_blank">its manual</a>.  (It had a real manual!)<br/>
<br/>
Once 7-PDF Maker was installed, I searched for its command-line executable, 7p.exe.  I put a copy of it into D:\Workspace (i.e., the folder where I was working).  That way, my commands that referred to 7p.exe would know where to find it.  There were other ways, but this was simplest, and 7p.exe was not a filename that would get confused with the ones I wanted to convert.<br/>
<br/>
I opened a command window in D:\Workspace and typed "7p /?" to see what the command line options were.  Basically, it seemed, I could save the DOC as a PDF with a command as simple as "7p D:\Workspace\File.doc."  The /? instructions seemed to be saying that I had to specify an absolute path for the source file (i.e., not just "File.doc" without the drive and folder information).  I was not sure whether that was necessary with a copy of 7p.exe in the working folder.  There was also an option to save the resulting PDF to a different folder (e.g., "7p File.doc D:\Workspace\Output").  In addition, I could use wildcards.  7p.exe D:\Folder\*.doc would convert all doc files in Folder to PDF.  The same command with *.* would convert all supported files to PDF.  There were many supported filetypes (manual p. 18), including Word, WordPerfect, OpenOffice, Excel, PowerPoint, and various image formats (e.g., BMP, TIF, JPG, PNG).<br/>
<br/>
There were also options for overwriting and recursion (i.e., working down through subdirectories).  In both cases, the default was false (i.e., don't recurse, don't overwrite).  The default was all I needed, so I did not investigate the exact syntax.  But it appeared that one instance of the word "true" on the command line would be construed as an instruction to recurse.<br/>
<br/>
I gave it a test run with x.doc.  The command I used was simply "7p x.doc."  That gave me an error, so I tried "7p D:\Workspace\x.doc."  That gave me a different error:  "Variante referenziert kein Automatisierungsobjekt."  <a href="https://web.archive.org/web/20151205114351/http://translate.google.com/#de|en|%22Variante%20referenziert%20kein%20Automatisierungsobjekt%22" target="_blank">One translation</a> was, "Variant does not reference an automation object."  Did this mean that x.doc was not a convertible DOC file?  Or that I should have been running this in the 7-PDF installation folder on drive C?  I tried the latter with an absolute path (i.e., not just "7p x.doc").  Same "Variante referenziert" error.<br/>
<br/>
I tried opening x.doc in Word.  Oh.  Now I understood.  It was called a DOC file, but it was actually just a text file with a DOC extension.  But the manual said that text files were supported.  Maybe the .doc extension was confusing 7p?  I changed it to x.txt and tried the original approach of running the command in D:\Workspace rather than in the installation folder on drive C.  Specifically, I tried just "7p x.txt."  It said, "URL seems to be an unsupported one."  Maybe it was the wrong kind of text file.  Whatever; I used a text to PDF converter for them instead.<br/>
<br/>
I did not proceed further with 7-PDF because, at this point, I found <a href="https://web.archive.org/web/20151205114351/http://raywoodcockslatest.blogspot.com/2012/03/batch-converting-many-microsoft-word.html" target="_blank">an alternative</a> I liked better.  Not to say that 7-PDF was a bad program; it just was not working really well for me at this point.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

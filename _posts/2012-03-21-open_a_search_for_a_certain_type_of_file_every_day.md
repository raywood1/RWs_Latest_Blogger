---
layout: post
title: "Open a Search for a Certain Type of File Every Day"
date: 2012-03-21
---

<div class="post-body">
<p>I was in the process of converting scattered Microsoft Word .doc files to PDF.  I had <a href="https://web.archive.org/web/20151130170444/http://raywoodcockslatest.blogspot.com/2012/03/batch-converting-many-microsoft-word.html" target="_blank">found a way</a> to automate the conversion of large numbers of such files, provided I was willing to put them all into a single folder; but that left me with some that would have to be handled on a more piecemeal basis, one folder at a time.<br/>
<br/>
To aid in this process, I wanted my computer to give me a list of where my remaining .doc files were located, so that I could choose the ones that were ripe for conversion.  I had found <a href="https://web.archive.org/web/20151130170444/http://raywoodcockslatest.blogspot.com/2011/05/windows-7-file-finder-review-of.html" target="_blank">Everything</a> to be a very useful file finder.  On a one-time basis, I could find my Word docs by just typing *.doc on the Everything search line.  But now I wanted a command-line solution that would run Everything and do that search automatically.<br/>
<br/>
I had not previously tried using Everything with command-line options, but now I found those options in <a href="https://web.archive.org/web/20151130170444/http://support.voidtools.com/everything/Command_line_options" target="_blank">the Everything wiki</a>.  For this purpose, I found that this command would do the trick:<br/>
<blockquote>Everything -filename *.doc<br/>
</blockquote>That command worked because I had put a copy of Everything.exe (originally named Everything-1.2.1.371.exe) into C:\Windows.  Now, if I wanted that command to run on a regular basis (say, once a day, or once a week), I could add it to a regularly <a href="https://web.archive.org/web/20151130170444/http://raywoodcockslatest.blogspot.com/2011/07/windows-7-batch-files-that-run-things.html" target="_blank">scheduled batch file</a>.  Not that I would have to; I could also just run it from the command line as needed, or save it in a batch file that I would run by double-clicking on it (or on a shortcut to it).</p>
<div style="clear: both;"></div>
</div>

---
### Comments

---
layout: post
title: "Batch Converting Many WordStar (.ws) Files to PDF"
date: 2012-06-10
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20151121004733/http://raywoodcockslatest.blogspot.com/2012/03/batch-converting-many-microsoft-word_19.html" target="_blank">previously</a> worked out a command that would convert all of the Microsoft Word (.doc) or WordPerfect (.wpd) files in a folder to PDF.  Now I wanted to try that on a batch of old WordStar (.ws) files.  This post discusses that task.<br/>
<br/>
As described in the previous post, I set my PDF printer (Bullzip) to print without opening the resulting files and without interruptions, except that I think I did let it notify me of error messages.  I didn't want to have to approve each conversion manually.  Also, I had named the WordStar documents to have a .ws extension, even though that extension was not necessary back in WordStar's heyday.<br/>
<br/>
I had also configured my copy of Word 2003 to recognize and open .ws documents.  I was not entirely sure how I had managed this.  My records suggested two possibilities.  One was to run a .reg file containing the following lines, so as to modify the registry in some hopefully appropriate way:<br/>
<blockquote><span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Windows Registry Editor Version 5.00<br/>
<span style='font-family: "Courier New", Courier, monospace;'><br/>
<span style="font-size: x-small;">[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Text Converters\Export\WordStar]<br/>
"Extensions"="ws"<br/>
"Name"="WordStar 3.3 - 7"<br/>
"Path"="C:\\Program Files\\Common Files\\Microsoft Shared\\TextConv\\Wrdstr32.cnv"<br/>
<span style='font-family: "Courier New", Courier, monospace;'><br/>
<span style="font-size: x-small;">[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Text Converters\Import\WordStar]<br/>
"Extensions"="ws"<br/>
"Name"="WordStar 3.3 - 7"<br/>
"Path"="C:\\Program Files\\Common Files\\Microsoft Shared\\TextConv\\Wrdstr32.cnv"</span></span></span></span></span></blockquote>The other possibility was that I had apparently found a program that required me to add certain files to the Windows 7 Program Files folder, including particularly one called Wrdstr32.cnv.  <a href="https://web.archive.org/web/20151121004733/https://www.google.com/search?q=Wrdstr32.cnv&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> suggested that anyone hoping to download such files from a virus-free source had best be using something like <a href="https://web.archive.org/web/20151121004733/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;safe=off&amp;client=firefox-a&amp;hs=xpu&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=WOT+%22Web+of+Trust%22&amp;oq=WOT+%22Web+of+Trust%22&amp;aq=f&amp;aqi=g3g-K6g-sK1&amp;aql=&amp;gs_l=serp.3..0l3j0i30l6j0i10i30.1085.2606.0.2853.15.10.0.0.0.0.283.1383.2j5j2.9.0...0.0.ODV05_awJRE" target="_blank">WOT</a>.  It had been a while since I had set up my system, and in any case I had not tested these options individually to determine whether they were useful or necessary.  For all I knew, Word was capable of reading .ws files without any of this.  The point is that, at least on my system, Word was now capable of doing so.<br/>
<br/>
With all that in place, I was set to run a command that would hopefully process a lot of WordStar files without much intervention from me.  I started Notepad, created a blank file called Converter.bat, and put this line in it:<br/>
<blockquote><span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>FOR /F "usebackq delims=" %%g IN (`dir /b "*.ws"`) DO "C:\Program Files (x86)\Microsoft Office\Office11\winword.exe" "%%g" /q /n /mFilePrintDefault /mFileExit &amp;&amp; TASKKILL /f /im winword.exe</span></blockquote>I saved Converter.bat and put it in the folder containing the .ws files.  I probably could have used Excel to mass-produce commands that would have done the conversion in-place, for .ws files scattered among multiple folders, but <a href="https://web.archive.org/web/20151121004733/http://raywoodcockslatest.blogspot.com/2012/06/batch-verifying-or-validating-scattered.html" target="_blank">my approach</a> to that sort of situation tended to involve bringing the files to be converted together into one folder anyway, and then putting their converted replacements back where the original files had come from.<br/>
<br/>
I ran Converter.bat in the .ws folder.  It ran successfully; I had PDFs in my Bullzip output folder for each WS document in the input folder.  Mission accomplished.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
An earlier posttreats the similar problem of converting many text files to PDF using a different approach.

**Anonymous**:
there is a site that automatically sets the paths to install the appropriate files to the areas requiredwordstar zipSincerely,Clem(e)clementereyes at yahoo dot com


---
layout: post
title: "How to Print a Long Webpage or Image File"
date: 2008-01-02
---

<div class="post-body">
<p>I took this question to <a href="https://web.archive.org/web/20160109094401/http://www.adobeforums.com/webx?14@@.3c05a25c/0">the Adobe Acrobat Windows forum</a>.  It drew a couple of responses, but no real answer.

Here was the problem.  Acrobat gives you the option of printing a webpage to PDF.  Usually, it works just fine:  you print the webpage, Acrobat breaks it up into a bunch of 8.5 x 11 sheets (if it's a long webpage), and you have a PDF document containing a reasonably good representation of the webpage.

Sometimes, unfortunately, it does not work that way.  Instead of printing the entire webpage to PDF, Acrobat prints just the first and last pages, or maybe just the first page. I think the reason must have to do with the HTML coding of the webpage.  Whatever:  point is, you can't PDF the webpage. 

This happens for some long image files too.  For instance, I thought of using <a href="https://web.archive.org/web/20160109094401/https://addons.mozilla.org/en-US/firefox/addon/1146">the ScreenGrab extension</a> in Firefox to save the irritating long webpage to JPG or PNG format, and then using an image editor (e.g., the highly recommended freeware <a href="https://web.archive.org/web/20160109094401/http://irfanview.com/">IrfanView</a>) to print the PNG to PDF.  But this didn't work either:  I still got the same outcome.  Likewise if I first saved the webpage to different forms of HTML files on my local drive.

Eventually, though, I came to a simple solution.  Instead of trying to print to 8.5 x 11-inch paper, save the long webpage to a PNG, and then set Acrobat to print to a sheet that is 92 x 92 inches.  There are many webpages that are still too long for that, but it's not a bad size.  If you need to convert that outcome to 8.5 x 11, then maybe you can print the 92" PDF to an 8.5 x 11 PDF size.

In my experiments so far, this approach gives me fonts that look pretty much normal, viewed at a page width display setting.  They are good enough to OCR in Acrobat.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
To print without leaving the web page. In Firefox, download AAdvark, a page editor. Size and print the first page, then use AAdvark to delete the first part of the web page, then print the second and any subsequent pages. Aadvark is also useful to get rid of all the blurb around the text that you want.

**raywood**:
Sometimes I can print an otherwise difficult webpage by selecting just the text I want to print and hitting Print > Selection.

**raywood**:
A Firefox add-on calledScreen Capture Elitehas recently been working very well for this purpose in FF 8.0.1.

**bug**:
Use Safari instead. You can print multiple pages and it does not mess up the scaling.


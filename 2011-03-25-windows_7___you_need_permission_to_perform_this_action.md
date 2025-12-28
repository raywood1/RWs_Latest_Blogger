---
layout: post
title: "Windows 7:  You Need Permission to Perform This Action"
date: 2011-03-25
---

<div class="post-body">
<p>I was trying to move a file from one folder to another.  This was a frequently used folder.  I had done this operation a thousand times before.  Suddenly I got this error message:<br/>
<blockquote>Destination Folder Access Denied<br/>
You need permission to perform this action</blockquote><a href="https://web.archive.org/web/20120822012759/http://www.google.com/search?q=%22Windows+7%22+%22You+need+permission+to+perform+this+action%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;as_qdr=all&amp;num=50&amp;cad=h">A search</a> led to <a href="https://web.archive.org/web/20120822012759/http://answers.microsoft.com/en-us/windows/forum/windows_7-security/you-need-permission-to-perform-this-action-you/ed61078c-168f-476a-91cc-85f1398c0c53">the suggestion</a> that, in Windows Explorer, I should right-click on the folder and go to Properties &gt; Security tab &gt; Advanced &gt; Owner tab &gt; Edit &gt; select Administrator (since that was who I wanted to own the folder, though that was *already* who owned it) &gt; Apply &gt; OK.  That didn't work.  Some remarks indicated that this could be a digital rights management issue, in the case of a music file, but this was just a PDF.  It was, however, a PDF created by <a href="https://web.archive.org/web/20120822012759/http://www.google.com/search?q=%22Sumatra+PDF%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;as_qdr=all&amp;num=50&amp;cad=h">Sumatra PDF</a>, in an attempt to remove security from the PDF so that I could run OCR on it.  It seemed I should have used Foxit instead.  Anyway, I went back into Properties &gt; Security tab &gt; Advanced &gt; Everyone &gt; Change Permissions &gt; Everyone (check both boxes) &gt; Apply &gt; OK.  That didn't do it either.  I moved everything out of the folder, deleted it, put its former contents into a new folder, and was able to work normally.  No explanation.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

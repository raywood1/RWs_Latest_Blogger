---
layout: post
title: "Excel 2003:  Count the Number of Times a Letter Appears in a Cell"
date: 2010-05-24
---

<div class="post-body">
<p>I had tracked down the solution to this problem once before, and then couldn’t remember it or find it when I needed it again, so here it is.  It’s borrowed from <a href="https://web.archive.org/web/20190906053708/http://www.pcreview.co.uk/forums/thread-3698470.php">another source</a>, but I don’t mind, as long as it meets the need.<br/>
<br/>
The question is, how do you count the number of times a letter occurs within a cell, in Microsoft Excel 2003?  I was searching for this:<br/>
<br/>
<a href="//web.archive.org/web/20190906053708/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;safe=off&amp;client=firefox-a&amp;hs=vaI&amp;rlz=1R1GGGL_en___US333&amp;q=count+occurrences+%22of+a+letter+in+a+cell%22+%22excel+2003%22&amp;btnG=Search">count occurrences "of a letter in a cell" "excel 2003"</a><br/>
<br/>
when what I should have been searching for was this:<br/>
<br/>
<a href="//web.archive.org/web/20190906053708/https://www.google.com/search?q=%22excel+2003%22+%22Count+the+times+a+specific+character+appears+in+a+cell%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;client=firefox-a&amp;rlz=1R1GGGL_en___US333">“Count the times a specific character appears in a cell”</a><br/>
<br/>
but probably not this:<br/>
<br/>
<a href="//web.archive.org/web/20190906053708/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;safe=off&amp;client=firefox-a&amp;hs=aUd&amp;rlz=1R1GGGL_en___US333&amp;q=%22excel+2003%22+%22Count+the+number+of+times+a+character+appears+in+a+cell%22&amp;btnG=Search">"excel 2003" "Count the number of times a character appears in a cell"</a><br/>
<br/>
Anyway, the solution is to use either of these:<br/>
<br/>
=LEN(A1)-LEN(SUBSTITUTE(A1,"/",""))<br/>
=-LEN(SUBSTITUTE(A1,"/",""))+LEN(A1)<br/>
<br/>
The former is simpler, and it works.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**M Sayed**:
Excellent stuff !!


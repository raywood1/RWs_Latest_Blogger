---
layout: post
title: "Finding the Last Occurrence of a Character in an Excel String:  A User-Defined Function"
date: 2011-04-22
---

<div class="post-body">
<p>I was looking for the last occurrence of a hyphen in a string of text data in a cell in Excel 2003.  I wasn't sure how many hyphens there would be, so I couldn't just do repeated searches for a hyphen from the beginning.  I vaguely recalled that there was a way to do this, but I wasn't sure what it was.  This post describes the process of answering that question.<br/>
<br/>
This, I felt, was probably going to be close to the technique for counting the number of times a letter occurred in a cell.  I <a href="https://web.archive.org/web/20150215032216/http://raywoodcockslatest.blogspot.com/2010/05/excel-2003-count-number-of-times-letter.html">had searched</a> for the answer to that one previously.  The answer here did involve the use of the SUBSTITUTE command too.  In that other case, the solution was to count the difference in length of the string before and after substituting nothing (i.e., "") for the occurrence of the character in question.<br/>
<br/>
As pointed out by <a href="https://web.archive.org/web/20150215032216/http://www.mrexcel.com/archive/General/30895.html">Aladin Akyurek</a>, that would work here too, if you did the substitution, calculated the length difference, and then searched for the last occurrence, now that you knew how many times the character appeared in the string.   His solution appeared in a single formula, which I disfavored because it was easy to make mistakes in long formulas, hard to understand them, and hard to figure out where the mistake was.  But he did use SUBSTITUTE well, whereas I never used it, so I had something to learn there.<br/>
<br/>
What I found more interesting, though, was his alternate suggestion, involving something else that I never did:  define a function and save it for future use.  I surely should have invested the time to learn Visual Basic, when it replaced the old-style BASIC that I had used for minor programming in the 1980s and somewhat thereafter, but then I guess VB changed again in the 2000s and threw a lot of its users off the trail.  Anyway, his function was one that I could actually understand, from the old BASIC days.  The steps to make it work were:<br/>
<ul><li>Close all Excel files other than the one you're working on.</li>
<li>Go into Tools &gt; Macro &gt; Visual Basic Editor &gt; Insert &gt; Module.</li>
<li>Copy and paste this into the window:</li>
</ul><blockquote><blockquote>Function Reverse(Text As String) As String<br/>
Dim i As Integer<br/>
Dim StrNew As String<br/>
Dim StrOld As String<br/>
StrOld = Trim(Text)<br/>
For i = 1 To Len(StrOld)<br/>
StrNew = Mid(StrOld, i, 1) &amp; StrNew<br/>
Next i<br/>
Reverse = StrNew<br/>
End Function</blockquote></blockquote><ul><li>Go to File &gt; Close and return to Microsoft Excel.</li>
<li>Use the new REVERSE function by specifying the text to be reversed.  For my present purposes, a good use would be like this:  =FIND("-",REVERSE(A1)).</li>
</ul>I gave that a whirl.  It worked.  But some months later, after reinstalling Windows and Excel, it didn't work.  I was not sure what had changed.  I tried going into Tools &gt; Macro &gt; Security and changing the level to Medium; I played with <a href="https://web.archive.org/web/20150215032216/http://www.excelforum.com/excel-programming/688461-reverse-letter-sorting-in-a-cell.html" target="_blank">alternatives</a>; but I still got error messages.  As another approach, I installed <a href="https://web.archive.org/web/20150215032216/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=lso&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=morefunc+reverse&amp;oq=morefunc+reverse&amp;aq=f&amp;aqi=&amp;aql=1&amp;gs_sm=e&amp;gs_upl=7983l8959l0l9249l8l7l0l4l4l1l246l581l0.2.1l3l0" target="_blank">Morefunc</a> and then went into Tools &gt; Morefunc and did what it required in order to install it, and then tried Morefunc's <a href="https://web.archive.org/web/20150215032216/http://xcell05.free.fr/morefunc/english/" target="_blank">TEXTREVERSE</a> command.  That didn't work either.  The message I was getting was #NAME, which <a href="https://web.archive.org/web/20150215032216/http://www.ozgrid.com/Excel/formula-errors.htm" target="_blank">apparently meant</a> that Excel was not recognizing the function (i.e., TEXTREVERSE, or whatever it was called).  Something seemed to be interfering with the operation of the Visual Basic script.  I tried suspending my antivirus program, but that wasn't the solution.  Ultimately, the solution -- getting Morefunc's TEXTREVERSE to work -- seemed to involve a combination of killing and restarting Excel, embedding Morefunc into the worksheet until it finally said "Update successful," and typing my formula in all lowercase.  There was a new problem, though:  Morefunc's TEXTREVERSE function would crash Excel 2003 when dealing with cells containing more than 127 characters.  I tried again with the REVERSE code shown above.  Now that was working too, and no 127-character limit.  It worked on a cell containing more than 1,000 characters.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

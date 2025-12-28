---
layout: post
title: "Using Excel to Clean Unwanted Characters from Filenames or Other Text"
date: 2012-03-01
---

<div class="post-body">
<p>I was trying to organize some files.  This post contains some notes I made on ways of using Microsoft Excel to change a list of filenames.  The renaming project drew on file renaming techniques described <a href="https://web.archive.org/web/20151125205034/http://raywoodcockslatest.blogspot.com/2012/02/batch-merging-many-scattered-jpgs-into_14.html" target="_blank">elsewhere</a>.<br/>
<br/>
In various <a href="https://web.archive.org/web/20151125205034/http://raywoodcockslatest.blogspot.com/2012/03/excel-2003-attempt-to-sort-sentences-or.html">attempts</a> in this process, I came up against situations where inconsistent punctuation and other filename characteristics made the process unnecessarily complicated.  For instance, file names might refer to "Barack Obama," "Barack H. Obama," "President Obama," and so forth.  These would all be alphabetized differently.  Duplicates might be concealed, and files that belonged together topically might be overlooked.<br/>
<br/>
In part, that was an issue of choosing and using consistent <a href="https://web.archive.org/web/20151125205034/http://raywoodcockslatest.blogspot.com/2012/03/file-naming-conventions.html" target="_blank">file naming conventions</a>.  But at this point, given that the files were already named, there was an issue of how to deal with punctuation and other non-alphanumeric characters.  I wondered if there was a relatively straightforward way to get my arms around the varieties of character usage within a particular corpus.<br/>
<br/>
The first task seemed to be identifying what unwanted characters were in use.  Taking Microsoft Excel as my weapon <em>du jour</em>, I made a list of the filenames that I might want to change, using DIR on the Windows command line (see the comments following <a href="https://web.archive.org/web/20151125205034/http://raywoodcockslatest.blogspot.com/2012/02/windows-7-finding-dir-alternative.html" target="_blank">another recent post</a>).  I pasted that list of filenames into Excel.<br/>
<br/>
Next, I ran <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?q=identify+%22unique+characters%22+string+Excel&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a">a search</a> and found several ingenious approaches to related problems.  <a href="https://web.archive.org/web/20151125205034/http://www.chinese-forums.com/index.php?/topic/36680-how-to-have-a-list-of-unique-characters-in-a-document/">One</a> would use a wildcard search-and-replace in Microsoft Word:   search for ? (making sure to indicate that this would be a "Use wildcards" search) and replace with ^&amp;^p to put the same character (that is, any character) on a line by itself; then paste the whole text into Excel and do a unique filter to get all of the unique characters found in the text.  This did not seem likely to work for my purposes, unfortunately.  For one thing, Excel 2003 was limited to 65,536 rows, and there could easily be more characters than that in a text being analyzed.  I had also found that spreadsheets capable of handling more rows could be slow at it.<br/>
<br/>
There were other approaches that used <a href="https://web.archive.org/web/20151125205034/http://www.excelbanter.com/showpost.php?p=508736&amp;postcount=2">an array formula</a> or <a href="https://web.archive.org/web/20151125205034/http://www.mrexcel.com/forum/showpost.php?p=2193244&amp;postcount=8">a script</a>.  I was not as comfortable with those that I did not understand, because it would be difficult for me to work through their logic and make sure they were really doing what I wanted them to do.  An unnoticed mistake could have unfortunate effects when altering a large or important text, or when renaming thousands of files.<br/>
<br/>
Another possibility came to mind as I looked at <a href="https://web.archive.org/web/20151125205034/http://www.mrexcel.com/forum/showpost.php?p=2193162&amp;postcount=5">the suggestion</a> to use MoreFunc's <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=gf1&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Morefunc+Excel+%22regex.count%22&amp;oq=Morefunc+Excel+%22regex.count%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=7137l12041l0l12294l16l5l0l0l0l0l248l778l2.1.2l5l0&amp;gs_l=serp.3...7137l12041l0l12294l16l5l0l0l0l0l248l778l2j1j2l5l0">REGEX.COUNT</a> function (alternately, Excel's <a href="https://web.archive.org/web/20151125205034/http://www.mrexcel.com/forum/showpost.php?p=2193287&amp;postcount=9">SUBSTITUTE</a> or possibly <a href="https://web.archive.org/web/20151125205034/http://www.techonthenet.com/excel/formulas/match.php">MATCH</a>) to produce character-by-character counts.  I ran <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=hqM&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Excel+2003%22+SUBSTITUTE+function&amp;oq=%22Excel+2003%22+SUBSTITUTE+function&amp;aq=f&amp;aqi=g1&amp;aql=&amp;gs_sm=3&amp;gs_upl=10110l10654l0l10998l9l6l0l0l0l0l319l1158l0.2.2.1l5l0&amp;gs_l=serp.3..0.10110l10654l0l10998l9l6l0l0l0l0l319l1158l0j2j2j1l5l0">a search</a> and found some interesting variations in SUBSTITUTE, including <a href="https://web.archive.org/web/20151125205034/http://www.ozgrid.com/forum/showthread.php?t=39728&amp;p=199166#post199166">nested</a> and <a href="https://web.archive.org/web/20151125205034/http://www.ozgrid.com/forum/showthread.php?t=59547&amp;p=307598#post307598">case-insensitive</a> substitutions, along with the <a href="https://web.archive.org/web/20151125205034/http://exceluser.com/blog/797/excels-clean-function-is-more-powerful-than-you-think.html">CLEAN</a> function.  <a href="https://web.archive.org/web/20151125205034/http://www.ozgrid.com/forum/showthread.php?t=59547">One solution</a>, it seemed, would be to use 26 columns containing something like =SUBSTITUTE(UPPER(A1),"","") to replace all upper- and lower-case letters with nothing, another 10 columns to do the same for numbers, and then see what's left.<br/>
<br/>
With SUBSTITUTE, one possibility was to set up a map.  Put the rows of text being analyzed in one worksheet ("Sheet1").  Create a second worksheet ("Sheet2") within the same Excel file.  In Sheet2, make each row relate to the row of the same number in Sheet1.  So, for example, if there was a text string in cell A5 in Sheet1, there would be a row of characters across row 5 in Sheet2.  Each cell in that row would count the occurrences of a specific character.  For example, the 65th column would detect occurrences of the character whose Excel code happened to be 65 (that is, the letter "A," producible by =CHAR(65)).  The chief problem with this approach was that its calculations would take a year.  It would also max out Excel 2003's limit of 256 columns.  It would have the advantage of transparency:  I would be able to see much of what was happening in the data.<br/>
<br/>
I found <a href="https://web.archive.org/web/20151125205034/http://office.microsoft.com/en-us/excel-help/create-your-own-worksheet-functions-HA001054846.aspx">a user-defined function</a> (UDF) -- what I had been referring to as a script -- called <a href="https://web.archive.org/web/20151125205034/http://www.excelforum.com/excel-general/681475-formula-to-remove-unwanted-characters.html">SUBSTITUTELIST</a>.  This UDF would let me indicate a list of characters to simply remove.  In naming files, I would definitely not want to include many of the odd characters that were readily visible if, say, I opened a non-text file in Notepad.<br/>
<br/>
<img border="0" src="https://web.archive.org/web/20151125205034im_/http://4.bp.blogspot.com/-Q2-4JyrjfeU/T1IsKRjMtaI/AAAAAAAAAJk/eXVW4_YahWo/s200/Clipboard01.jpg"/><br/>
<br/>
The first step, with SUBSTITUTELIST, was to define it as a function that I could use in spreadsheet formulas.  To do that, using the steps described atop <a href="https://web.archive.org/web/20151125205034/http://raywoodcockslatest.blogspot.com/2012/02/excel-2003-print-or-export-formulas.html">another post</a>, I copied and pasted this text into an Excel module:<br/>
<blockquote>Function SubstituteList(rString As String, rList As Range) As String<br/>
Dim rCell As Range<br/>
For Each rCell In rList<br/>
rString = Replace(rString, rCell.Text, "")<br/>
Next rCell<br/>
SubstituteList = rString<br/>
End Function</blockquote>I didn't write that code, and was only partly clear on what it said.  It appeared, though, that its middle line was going to replace rString with nothing ("").  In other words, rString was being removed.  Now I had to tell it what characters to treat as rString.  In the spreadsheet listing the filenames I wanted to work on, I opened a new worksheet, called Sheet2, and put the numbers 1 through 255 in cells A2 to A256.  (Two easy ways to insert a series of numbers:  use =A1+1 in cell A2, and so forth; or enter the first two numbers (i.e., 1 and 2) manually, highlight the cells to be filled, and then use Edit &gt; Insert &gt; Series.  The Alt command option would probably still work in post-2003 versions of Excel:  Alt-E, I, S, Enter.)<br/>
<div class="separator" style="clear: both; text-align: center;"><a href="https://web.archive.org/web/20151125205034/http://2.bp.blogspot.com/-ADKSxogwAKQ/T29hT5dQjtI/AAAAAAAAAJw/ULYTp1c5P84/s1600/Clipboard01.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="151" src="https://web.archive.org/web/20151125205034im_/http://2.bp.blogspot.com/-ADKSxogwAKQ/T29hT5dQjtI/AAAAAAAAAJw/ULYTp1c5P84/s320/Clipboard01.jpg" width="320"/></a></div>Then, in Sheet2 cell B1, I typed =CHAR(A1), and copied it down to B255.  So now column B contained the actual characters I wanted to look at, whose CHAR equivalents were shown in column A.  Finally, column C contained the characters to be removed from consideration.  For example, in cell C128, I typed =B128.  That put a copy of CHAR(127) into column C.  SUBSTITUTELIST was going to remove anything in column C.  So that particular character would be removed from the cell in Sheet1 where I was going to be using SUBSTITUTELIST.  Depending on the situation, I might or might not want to remove all non-alphanumeric characters.  For instance, I thought that what I would really want to do with something like the euro character (<span style='font-family: "Times New Roman"; font-size: 12pt; mso-ansi-language: EN-US; mso-bidi-language: AR-SA; mso-fareast-font-family: "Times New Roman"; mso-fareast-language: EN-US;'>€), in a filename, would not be to eliminate it, but rather to replace it (e.g., <span style='font-family: "Times New Roman"; font-size: 12pt; mso-ansi-language: EN-US; mso-bidi-language: AR-SA; mso-fareast-font-family: "Times New Roman"; mso-fareast-language: EN-US;'>€35 becomes EUR 35).</span></span><br/>
<br/>
To use SUBSTITUTELIST, I put my text to be analyzed in column A of Sheet1.  In B1, I entered this:  =SUBSTITUTELIST(A1,Sheet2!$C$1:$C$255).  I copied that formula all the way down, next to each text string to be examined.  That gave me a collection of funky characters in Sheet1 column B.  Originally, I added TRIM to the SUBSTITUTELIST formula just cited, but then I realized that I actually wanted to see the pattern of spaces and other non-alphanumeric characters.<br/>
<br/>
SUBSTITUTELIST seemed to have potential for single-character eliminations, but it didn't seem capable of substitutions involving multiple-character strings (e.g., EUR in place of €).  It looked like a relatively simple change to SUBSTITUTELIST might do the job, but I had little ability for that sort of work at this point, so I <a href="https://web.archive.org/web/20151125205034/http://superuser.com/questions/404575/excel-or-batch-trying-to-automate-text-correction-many-changes-one-or-more-c" target="_blank">posted a question</a> on it.  One reply to that question suggested a UDF called CLEANUPTEXT.  The contents of that UDF (created in the same manner as SUBSTITUTELIST, above) were as follows:<br/>
<br/>
<code><span style="font-size: x-small;">Option Explicit<br/>
Sub cleanupText()<br/>
<br/>
Dim allTxt() As Variant, sublist() As Variant<br/>
Dim i As Long, j As Long, k As Long, tdots As Integer<br/>
<br/>
'Store data from sheets in arrays.<br/>
allTxt = Sheets(1).UsedRange.Value<br/>
sublist = Sheets(2).UsedRange.Offset(1, 0).Resize(Sheets(2).UsedRange.Rows.Count - 1, Sheets(2).UsedRange.Columns.Count).Value<br/>
<br/>
For i = 1 To UBound(allTxt, 1)<br/>
    For j = 1 To UBound(allTxt, 2)<br/>
        'Loop through replacement terms and make replacements to data in array.<br/>
        For k = 1 To UBound(sublist, 1)<br/>
            allTxt(i, j) = Replace(allTxt(i, j), sublist(k, 1), sublist(k, 2))<br/>
        Next k<br/>
        allTxt(i, j) = Trim(allTxt(i, j))<br/>
        </span><span style="color: #cc0000;"><span style="color: cyan; font-size: x-small;">'Remove series of trailing periods.<br/>
        If Right(allTxt(i, j), 1) = "." Then<br/>
            tdots = 1<br/>
        Else<br/>
            tdots = 0<br/>
        End If<br/>
        Do While tdots = 1<br/>
            allTxt(i, j) = Left(allTxt(i, j), Len(allTxt(i, j)) - 1)<br/>
            If Right(allTxt(i, j), 1) = "." Then<br/>
                tdots = 1<br/>
            Else<br/>
                tdots = 0<br/>
            End If<br/>
        Loop<br/>
        </span></span></code><code><span style="font-size: x-small;">allTxt(i, j) = Trim(allTxt(i, j))<br/>
    Next j<br/>
Next i<br/>
'Print cleaned up results in array onto sheet.<br/>
ActiveSheet.UsedRange.Value = allTxt<br/>
End Sub</span></code><br/>
<br/>
The instructions accompanying that UDF seemed to indicate that it required a separate worksheet, called Sheet2, containing the "before" terms in column A of Sheet2, and the "after" terms in column B of that sheet; and Sheet1 had to be the name of the tab containg the text being operated on.  In response to my question, the text shown in blue (above) was designed to remove trailing dots from the text being modified.  I did not actually try this UDF, but I hoped that I would not have to write similar lines of text for other kinds of unwanted text strings -- that, in other words, the column A / column B replacement approach would suffice.  If so, I might try to simplify this UDF by removing the lines in blue.<br/>
<br/>
On a separate note, I had noticed that some of the files in my list looked like their names were identical except for punctuation, so I added a column, in my spreadsheet that listed filenames, for this formula:  =LOWER(substitutelist(M2,Sheet2!$C$1:$C$255)).  M2 contained the existing filename, or part thereof, and Sheet2 column C was set to eliminate all non-alphanumeric characters, as shown above.  This step did succeed in highlighting some duplicate filenames and other issues.<br/>
<br/>
Another problem was that, in some cases, I would have to rename files before proceeding with something like SUBSTITUTELIST.  The specific problem was that some characters in filenames would defeat batch commands.  That is, I could have a command to change a filename, perhaps in response to an insight emerging from SUBSTITUTELIST; but the command might not run.  So I would have to change or delete those troublesome characters first.  (I often used Excel formulas to generate commands that I could run in a batch file to rename numerous files.  The basic idea here was that I would put the existing filename in cell A1 of an empty worksheet, and the desired filename in cell B1, and then I would enter this formula in cell C1:  ="ren "&amp;CHAR(34)&amp;A2&amp;CHAR(34)&amp;" "&amp;B2.  (If the new filename in B2 had spaces in it, then it too would have to be surrounded by CHAR(34) instances, as done in that formula for cell A1.)  The particular chacters at issue here were percent symbols and possibly exclamation marks.  The commands were right.  They would run if I typed them into the command line, or copied and pasted them there.  But they wouldn't work from within a batch file.  To address this concern, I just deleted the exclamation marks, and I replaced the percent symbols with "pct" (e.g., 45% became 45pct).<br/>
<br/>
In some cases, I would want a tool that could replace one or more undesirable characters, in a single bulk process, with one or more preferred characters.  In part, this was a simple interest in transliteration or Romanization (i.e., converting foreign-language characters to the standard English alphabet).  There would be at least two reasons to do that.  One was that I had run into some file handling issues with some such characters.  I recalled one recent case where something that looked like a C (maybe ḉ or ć or ĉ or ċ or č) was not working correctly with some backup program or something.  The other reason was that I might not remember which character to use when doing filename searches.  So, for instance, if I was looking for all of the files containing a copy of someone's resume, I might or might not want to have to search for both "resume" and "résumé."  There were many <a href="https://web.archive.org/web/20151125205034/http://www.loc.gov/catdir/cpso/roman.html" target="_blank">Romanization tables</a> for various languages, possibly best approached by finding conversion tables for the thousands of possible <a href="https://web.archive.org/web/20151125205034/http://ascii-table.com/unicode.php" target="_blank">Unicode characters</a>.  This could take further attention, as there were <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?q=%22kinds+of+unicode%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">multiple kinds</a> of Unicode, not all of which might be consistent with <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=J8B&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Excel+uses+Unicode%22&amp;oq=%22Excel+uses+Unicode%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=12&amp;gs_upl=851573l851573l0l854350l1l1l0l0l0l0l450l450l4-1l1l0&amp;gs_l=serp.12...851573l851573l0l854350l1l1l0l0l0l0l450l450l4-1l1l0" target="_blank">Excel's coding</a>.  In filenames, especially, examples involving several characters could include "pct" (above) and the replacement of $ with USD and of © with (C).  One readability example, arising where HTML has become involved, would be to replace the HTML code of <a href="https://web.archive.org/web/20151125205034/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=yHS&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=HTML+apostrophe&amp;oq=HTML+apostrophe&amp;aq=f&amp;aqi=g10&amp;aql=&amp;gs_l=serp.3..0l10.8110l11374l0l13140l15l9l0l4l4l2l302l851l2j1j1j1l5l0.frgbld." target="_blank">&amp;#39;</a> with the apostrophe.<br/>
<br/>
As I thought further about the problem, I realized that characters might be unwanted in context, not in isolation.  For instance, the hyphen ("-") could be fine in some settings, not fine in others.  At the risk of opening the door to complexity, it seemed the ideal approach (perhaps the less messy approach, in the long run) would give me the possibility of listing multi-character combinations and indicating their desired replacement.  I found a UDF called <a href="https://web.archive.org/web/20151125205034/http://www.ozgrid.com/forum/showthread.php?t=29700&amp;p=153516#post153516" target="_blank">SUPERSUB</a> that seemed to be just what the doctor ordered:<br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Function SuperSub(OriginalText As String, rngOldText As Range) <br/>
    Dim cel As Range <br/>
    Dim strOldText As String, strNewText As String <br/>
     'loop through list of old_text used in substitute<br/>
    For Each cel In rngOldText.Cells <br/>
        strOldText = cel.Value <br/>
        strNewText = cel.Offset(0, 1).Value <br/>
        OriginalText = Application.WorksheetFunction.Substitute(OriginalText, strOldText, strNewText) <br/>
    Next cel <br/>
    SuperSub = OriginalText <br/>
End Function </span><br/>
<br/>
But, again, I did not try this script at the time, but was merely preserving its information here for possible future application.<br/>
<br/>
<a href="https://web.archive.org/web/20151125205034/http://www.mrexcel.com/forum/showpost.php?p=1471922&amp;postcount=9" target="_blank">Another post</a> offered a UDF called REMOVEPUNCTUATION where I could create a list of items to replace, and their replacements, within the macro.  The text of that one (with a few illustrative examples) was as follows:<br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Sub test()<br/>
Dim c As Range, t As String<br/>
For Each c In Range("A1:A" &amp; Range("A" &amp; Rows.Count).End(xlUp).Row)<br/>
    t = UCase(" " &amp; RemovePunctuation(c.Text) &amp; " ")<br/>
    t = Replace(t, " AVE ", " AVENUE ")<br/>
    t = Replace(t, " BLVD ", " BOULEVARD ")<br/>
    t = Replace(t, " BVD ", " BOULEVARD ")<br/>
    t = Replace(t, " CYN ", " CANYON ")<br/>
    t = Replace(t, " CTR ", " CENTER ")<br/>
    t = Replace(t, " CIR ", " CIRCLE ")<br/>
    t = Replace(t, " CT ", " COURT ")<br/>
    t = Replace(t, " DR ", " DRIVE ")<br/>
    t = Replace(t, " FWY ", " FREEWAY ")<br/>
    t = Replace(t, " HBR ", " HARBOR ")<br/>
    t = Replace(t, " HTS ", " HEIGHTS ")<br/>
    t = Replace(t, " HWY ", " HIGHWAY ")<br/>
    t = Replace(t, " JCT ", " JUNCTION ")<br/>
    t = Replace(t, " LN ", " LANE ")<br/>
    t = Replace(t, " MTN ", " MOUNTAIN ")<br/>
    t = Replace(t, " PKWY ", " PARKWAY ")<br/>
    t = Replace(t, " PL ", " PLACE ")<br/>
    t = Replace(t, " PLZ ", " PLAZA ")<br/>
    t = Replace(t, " RDG ", " RIDGE ")<br/>
    t = Replace(t, " RD ", " ROAD ")<br/>
    t = Replace(t, " RTE ", " ROUTE ")<br/>
    t = Replace(t, " ST ", " STREET ")<br/>
    t = Replace(t, " TRWY ", " THROUGHWAY ")<br/>
    t = Replace(t, " TL ", " TRAIL ")<br/>
    t = Replace(t, " TPKE ", " TURNPIKE ")<br/>
    t = Replace(t, " VLY ", " VALLEY ")<br/>
    t = Replace(t, " VLG ", " VILLAGE ")<br/>
    t = Replace(t, " APT ", " APARTMENT ")<br/>
    t = Replace(t, " APTS ", " APARTMENTS ")<br/>
    t = Replace(t, " BLDG ", " BUILDING ")<br/>
    t = Replace(t, " FLR ", " FLOOR ")<br/>
    t = Replace(t, " OFC ", " OFFICE ")<br/>
    t = Replace(t, " OF ", " OFFICE ")<br/>
    t = Replace(t, " APT ", " APARTMENT ")<br/>
    t = Replace(t, " STE ", " SUITE ")<br/>
    t = Replace(t, " N ", " NORTH ")<br/>
    t = Replace(t, " E ", " EAST ")<br/>
    t = Replace(t, " S ", " SOUTH ")<br/>
    t = Replace(t, " W ", " WEST ")<br/>
    t = Replace(t, " NE ", " NORTHEAST ")<br/>
    t = Replace(t, " SE ", " SOUTHEAST ")<br/>
    t = Replace(t, " SW ", " SOUTHWEST ")<br/>
    t = Replace(t, " NW ", " NORTHWEST ")<br/>
    c = Trim(t)<br/>
Next<br/>
End Sub</span><br/>
<br/>
<span style='font-family: "Courier New", Courier, monospace; font-size: x-small;'>Function RemovePunctuation(r As String) As String<br/>
With CreateObject("vbscript.regexp")<br/>
    .Pattern = "[^A-Z0-9 ]"<br/>
    .IgnoreCase = True<br/>
    .Global = True<br/>
    RemovePunctuation = .Replace(r, "")<br/>
End With<br/>
End Function</span><br/>
<br/>
It seemed that, if I used REMOVEPUNCTUATION to make a large number of changes (more than just the few dozen shown here), I might use Excel to generate the text of the additional lines to be inserted into the REMOVEPUNCTUATION script.<br/>
<br/>
That was the extent of these notes.  I would have to await another situation requiring mass file renaming in order to test these techniques.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I used some aspects of this post inanother postfor renaming exported emails.

**raywood**:
Another postidentifies some freeware that may be useful for similar character-cleaning purposes.


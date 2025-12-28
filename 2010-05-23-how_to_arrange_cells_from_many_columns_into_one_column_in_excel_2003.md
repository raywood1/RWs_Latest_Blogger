---
layout: post
title: "How to Arrange Cells from Many Columns into One Column in Excel 2003"
date: 2010-05-23
---

<div class="post-body">
<p>Suppose you're using Microsoft Excel 2003.  Suppose you have data in multiple columns, in an irregular array, like this:<br/>
<br/>
<div class="separator" style="clear: both; text-align: center;"><a href="https://web.archive.org/web/20160124230112/http://3.bp.blogspot.com/_jBbsOO7VnH8/S_km_MqTQqI/AAAAAAAAAEM/8si22PbzlG0/s1600/Clipboard02.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="123" src="https://web.archive.org/web/20160124230112im_/http://3.bp.blogspot.com/_jBbsOO7VnH8/S_km_MqTQqI/AAAAAAAAAEM/8si22PbzlG0/s320/Clipboard02.jpg" width="320"/></a></div><br/>
<div class="separator" style="clear: both; text-align: center;"></div>And suppose you want to get all of that data into column A, like this:<br/>
<br/>
<div class="separator" style="clear: both; text-align: center;"><a href="https://web.archive.org/web/20160124230112/http://4.bp.blogspot.com/_jBbsOO7VnH8/S_knThoCf8I/AAAAAAAAAEU/RvLpjkNsTEo/s1600/Clipboard03.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="200" src="https://web.archive.org/web/20160124230112im_/http://4.bp.blogspot.com/_jBbsOO7VnH8/S_knThoCf8I/AAAAAAAAAEU/RvLpjkNsTEo/s200/Clipboard03.jpg" width="151"/></a></div><br/>
How should you proceed?<br/>
<br/>
<div style="text-align: center;"><b>Summary</b></div><br/>
To arrange an irregular table so that all of its cells are in a single column, create a separate worksheet for your calculations.  Count the number of cells containing data, so that you can be sure your process works correctly.  Use the CELL function to return the locations of the cells that actually contain data.  Copy those results into Word.  Convert that table to text.  Use Find-and-Replace to shrink that text file.  Paste it back into Excel.  Use string functions and indexing as needed to arrange the list as you wish. Use the INDIRECT function to show the contents of the referenced cells.<br/>
<br/>
If this post is helpful, please add a comment below. <br/>
<br/>
<div style="text-align: center;"><b>Step by Step</b></div><br/>
In this answer, I'll take the slow route, because it may be more efficient. <br/>
<br/>
First, find out how big your spreadsheet is.  From anywhere in the spreadsheet, hit Ctrl-Home.  Let's say that takes you to cell A1.  That's the upper left corner of your spreadsheet.  Now hit Ctrl-End.  Let's say that takes you to FB1765.  That's the lower right corner of your spreadsheet.  (That's a pretty big spreadsheet.)<br/>
<br/>
With a spreadsheet that big, things can get confusing.  If it were smaller, you could do the conversion manually.  There are a couple of ways to do that.  One would be to sort each column, by itself, and cut and paste only those cells containing data to the bottom of column A.  Another way would be to do an AutoFilter (Data &gt; Filter &gt; AutoFilter) and cut and paste the results from each column.<br/>
<br/>
But we have a big spreadsheet, and we want a faster and safer solution than we could get with a manual cut-and-paste operation.  So now open a new worksheet within the existing file.  That's Insert (from the menu bar) &gt; Worksheet.  Do your work here.  This will give you more space to work in, and will protect your original spreadsheet from unwanted changes.  (I'm referring to "spreadsheet" and "worksheet" interchangeably here.)  So remember:  we won't be making any changes to your original spreadsheet; all of this will take place on other spreadsheets.<br/>
<br/>
Let's say the original spreadsheet is called Multiword and this new spreadsheet is called Sheet1. In Sheet1, go to cell A1 and type this:<br/>
<br/>
=IF(LEN(Multiword!A1)&gt;0,"x","")<br/>
<br/>
This says, if the length of cell A1 in Multiword is greater than zero (that is, if there's something in the cell, even just a spacebar space), then give me an "x"; otherwise, give me nothing.  This is useful because sometimes formatting can cause cells in Excel to behave as though there were something in them, when there's not.<br/>
<br/>
Now let's copy that formula so that it covers the same territory in Sheet1 that your data occupy in Multiword.  Move your mouse cursor to the lower right corner of cell A1.  Your cursor will change into crosshairs.  Left-click on that lower right corner of cell A1 and drag it down to A1765.  Let go, and then left-click and drag it across to column FB, and let go.  This gives you an "x" corresponding to each cell in Multiword that contains data.  Now select it all (Ctrl-A) and then go to Format &gt; Column &gt; Width &gt; 1.  (Or even narrower, e.g., .5.)  This gives you a more easily visualized map of how your data is laid out.  You could have done the same thing by just making the formula say =Multiword!A1, and this would have had the advantage of showing you the actual contents of Multiword, as you moved your cursor from one cell to another; but this can be easier to think about.  Besides, we can use those consistent "x" values.<br/>
<br/>
Now let's see how many entries you should wind up with at the end.  In Sheet1, go to a cell outside your data map.  In this example, let's go to A1767.  There, type this:<br/>
<br/>
=COUNTIF(A1:FB1765,"x")<br/>
<br/>
That will tell us how many cells contain data.  It may not display correctly in cell A1767 because the column width is too narrow, but you can see what it says by either widening the column or going to A1767 and hitting F2 and then F9.  In my example, that shows me that I have 21,242 cells containing data.  So in my final result, I should wind up with data in cells A1 through A21242, and nowhere else.<br/>
<br/>
Now let's say I like that map in Sheet1, and I want to save it, but I don't want it to take up calculation time.  I can freeze it all forever -- that is, I can convert it all to values instead of formulas.  To do this, go to A1 and hit Shift End-Home (i.e., while holding Shift, hit End and then Home) to select it all.  Hit Edit &gt; Copy and then Edit &gt; Paste Special &gt; Values.  Hit the Enter key a couple of times, until it looks like it's done.  Now those formulas in Sheet1 will all be converted to simple "x" entries.  Save a version of the file for backup.  For instance, let's call it BigFile 01.xls, and then save again as a newer version (BigFile 02.xls).<br/>
<br/>
Alright.  On to the main event.  Let's create another spreadsheet, Sheet2.  Here, in cell A1, enter this formula:<br/>
<br/>
=if(Sheet1!A1&lt;&gt;"x","",CELL("address",A1))<br/>
<br/>
That tells Sheet2 to enter the location of cell A1 into cell A1.  That is, Sheet2!A1 will now say $A$1.  (Note that, if you didn't want to keep Sheet1 as a map, you could incorporate the LEN calculation (above) into this formula, and do both at the same time on Sheet1.)<br/>
<br/>
In Sheet2, copy that formula to all cells, from A1 to FB1765, as described above.  Here's a before-and-after picture of what that would look like, if I were trying to do it all in a single spreadsheet:<br/>
<br/>
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"><a href="https://web.archive.org/web/20160124230112/http://1.bp.blogspot.com/_jBbsOO7VnH8/S_k_8V7M6pI/AAAAAAAAAEc/giAYGXo33m0/s1600/Clipboard01.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="72" src="https://web.archive.org/web/20160124230112im_/http://1.bp.blogspot.com/_jBbsOO7VnH8/S_k_8V7M6pI/AAAAAAAAAEc/giAYGXo33m0/s400/Clipboard01.jpg" width="400"/></a></div><br/>
In that example, what I want next would look like this:<br/>
<br/>
$A$2<br/>
$A$3<br/>
$B$1<br/>
$B$2<br/>
$B$4<br/>
$C$3<br/>
<br/>
This would be a step on the way to getting values like this:<br/>
<br/>
3<br/>
2<br/>
5 <br/>
14<br/>
8<br/>
6<br/>
<br/>
So how do we do that?  In a big spreadsheet like mine, it's easier to do it in Microsoft Word.  So let's get Sheet2 ready for transfer.  Freeze Sheet2 as described above (with Paste Special etc.).  Hit Ctrl-A to select it all, and then Ctrl-C to copy it all.  In an empty Word document, hit Ctrl-V to paste it all.  With a big spreadsheet, this could take a while, as Word slowly gags on a couple hundred columns.  The result could be ugly -- mine was a pinstriped thing that didn't look like it contained any data at all -- but fear not.  When Word is done figuring it out, click somewhere on the resulting table.  Choose Table &gt; Convert &gt; Table to Text &gt; Paragraph marks.  It will default to a checkmark in "Convert nested tables," which is fine.  Click OK.  After a couple of years, Word will give you a very ragged document, with lots of spaces between rows.  (Mine was more than 3,000 pages long.)  These blank rows are easy to clean up with Find-and-Replace.  In Word, ^p is the newline character for most documents.  So do a Find-and-Replace (Ctrl-H) to replace two newlines with one.  In other words, replace ^p^p with ^p.  (Actually, before doing that, you may want to remove spacebar spaces before or after the ^p, else some lines may not get fixed.)  Repeat the ^p^p replacement until all of your cell references are in a nice list.  Word may continue to believe that it needs to remove a couple more ^p^p duplicates, but at some point you can tell it's lying.  Save the result.  Let's call it BigFile.doc.<br/>
<br/>
When I went through these steps with one file, they worked fine.  When I went through them with another file, however, I had a problem at this point.  The problem was that Word did not convert all of the lines properly.  It jammed a bunch of Excel cell contents together on the same line, instead of giving each its own line.  (I could tell:  I did a LEN in a separate column for each imported line in Excel, sorted on that column, and found that some were very long.)  To fix this, I had to search the Excel file to find a character that did not already occur in it (e.g., @ or `), and then revise the formula (above) so that it would stick that character on the end.  (Don't use ^ or ~ or other characters that don't turn up normal search results when you try to search for them.)  Then my first step in Word, after converting table to text, was to search for that character and replace it with ^p.<br/>
<br/>
Another innovation, in that second try, was to combine the text and its cell location.  Using the data shown above, this gave me this kind of result:<br/>
<br/>
3$A$2<br/>
2$A$3<br/>
5$B$1<br/>
14$B$2<br/>
8$B$4<br/>
6$C$3<br/>
<br/>
<br/>
That way, I could tell where the number (e.g., 3) had come from (e.g., cell A2), and I could use FIND and MID functions to put the numbers and their locations in separate columns.<br/>
<br/>
Anyway, to continue.  If cell order is important for your purposes, sort the Word doc.  If it's not too big, you can do it in Word.  Hit Ctrl-A and then Table &gt; Sort &gt; Sort by Paragraphs.  Mine was too big, so I created a new Excel spreadsheet, Sheet3, and pasted it back into there.  Sure enough, I had my 21,242 entries in column A.  Excel didn't sort them the way I liked, though:  it had $A$9 after $AY$896.  This called for some use of the LEN and &amp; functions.  For instance, if the LEN of the cell containing $A$9 is less than the LEN of the other cell, then insert some zeroes (using MID and FIND and &amp;) before the 9; and to get $A before $AY, consider using an Index column to rank the entries in the order they should go (with maybe a temporary addition before the $A).<br/>
<br/>
Once you have your 21,242 (or whatever) references in the order you prefer, there in column A in Sheet3, enter this in B1:<br/>
<br/>
="Multiword!"&amp;A1<br/>
<br/>
and enter this in cell C1:<br/>
<br/>
=INDIRECT(B1)<br/>
<br/>
copy cells B1 and C1 all the way down to the bottom of the spreadsheet.  You may want to save your work as a new file (BigFile 03.xls) and then freeze column C, and then delete all other columns and worksheets.<br/>
<br/>
<div style="text-align: center;"><span style="font-size: large;"><b>*  *  *  *  *</b></span></div><br/>
Again, if this post is helpful, please add a comment below.  Cheers!</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Mohammed Nasrallah**:
I didn't understand the last steps..!!Would you illustrated little bit more after the step of:In that example, what I want next would look like this:$A$2$A$3$B$1$B$2$B$4$C$3And how you made the rearrange of the columns into one column ?Thanks

**raywood**:
Mohammed -- can you tell me more specifically where you got stuck?  There's a lot of information after that step.  Were you able to get the data into Word?

**Anonymous**:
Would it be possible to explain how to do this in the 2007 version of excel and word? All steps complete with no problem up to when you copy and paste the data from excel into a word document. The problem starts at "When Word is done figuring it out, click somewhere on the resulting table.  Choose Table > Convert > Table to Text > Paragraph marks.  It will ...". Please let me know if you can give steps from this point on. Thanks in advance.

**raywood**:
I don't have Word 2007, but i believe it honors Word 2003 keystroke combinations.  When the blog post says, "Choose Table > Convert > Table to Text > Paragraph marks," I think you can achieve that as follows:  click somewhere on the table in Word, and then hit Alt-A, V, B, Enter.  In other words, hold down the Alt key and hit A.  Let them both go and type VB and then Enter.

**Adha**:
Nice Information, Thank you for sharing...

**raywood**:
Some of these steps are refined in the second (middle) section ofa more recent post(section titled "Lining Up the Phrases," beginning around the second image).

**raywood**:
A later postcontains a more refined approach to some aspects of the problem addressed here.


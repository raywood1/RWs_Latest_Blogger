---
layout: post
title: "Importing AutoCorrect Entries from Microsoft Word into OpenOffice Writer"
date: 2008-06-22
---

<div class="post-body">
<p>Microsoft Word allows users to save shortcuts that will correct or expand what they type.  For example, if I type "hte," Word has (I think) a built-in correction to "the."  Word knows that "hte" is not a word.

I have added a lot of other shortcuts to cut down on the typing:  "BO," for example, becomes "Barack Obama" if I type "BO" and then hit the spacebar or use some other punctuation.

The challenge, for me, was to import those thousands of built-in and added shortcuts from Word to OpenOffice.org's Writer program.  <a href="https://web.archive.org/web/20190906052410/http://www.oooforum.org/forum/viewtopic.phtml?t=40170">I had posted a question</a> on the matter some time back, but so far it has not yet drawn an answer I have found workable for my purposes.  Therefore, I decided to try modifying some advice I had found posted elsewhere.  The following is a complete description of the steps I took:

1.  I used Method 1 (using AutoCorrect.dot) from http://word.mvps.org/FAQs/Customization/ExportAutocorrect.htm.  In Word 2003, I clicked on the button to make a Backup of my Word AutoCorrect entries.  That gave me a Word document entitled "AutoCorrect Backup Document."

2.  I copied the entire document and pasted it into Microsoft Excel.  In Excel, I deleted all rows that did not have actual autocorrection values (e.g., I deleted the column headings).  I also deleted all columns other than the actual before-and-after values.  (In my case, there was just one such column, called RTF, filled with entries of "FALSE.")  I saved this Excel spreadsheet as AC.XLS.

3.  Find the OOo language file you're using.  For me, using US English, that file was called acor_en-US.dat, and was located (by default) in C:\Program Files\OpenOffice.org 2.4\share\autocorr.  I will call this simply the DAT file.

4.  Although it claims to be a DAT file, it is actually a zipped file, containing several different files.  Use your file zip utility to view the contents of the DAT file.  Inside it, you will see a file called DocumentList.xml.  You can view the contents of DocumentList.xml using Notepad.

(Some of these steps may not be as straightforward for you as they were for me.  I'm using 7-Zip for my zipper and OpenWith (a Windows Explorer extension) to open DocumentList.xml using Notepad without having to extract the file first.  But whatever.  Other tools may work as well or better.)

5.  With Notepad's WordWrap feature turned off, here's what I saw at the start of DocumentList.xml:

[?xml version="1.0" encoding="UTF-8"?][block-list:block-list list="http://openoffice.org/2001/block-list"][block-list:block name="--&gt;" name="→"][block-list:block name="-&gt;" name="-&gt;"][block-list:block name="(C)" name="©"][block-list:block name="(R)" name="®"]

and it basically just went down the list from there.  What I saw at the end of DocumentList.xml was this:

[block-list:block name="yuo" name="you"][block-list:block name="yuor" name="your"][/block-list:block-list]

Actually, that wasn't <span style="font-style: italic;">exactly</span> what I saw.  My blog website here, Blogger.com, is too smart for me.  It automatically converts HTML coding into HTML, so I can't show you exact HTML.  I have had to modify it for this presentation.  The modification I have made has been to replace angle brackets with square brackets.  In other words, when you see "[" above, please replace it in your own typing with "&lt;" and when you see "]" above, please replace it with "&gt;".

Also, be advised that there are no line breaks in the DocumentList.xml file.  It just runs on without interruption from beginning to end.  It is not like the nice, organized table that AutoCorrect.dot gives you.  So when you are inserting additional AutoCorrect items into DocumentList.xml, you need to just stick them into the flow, not put each one on its own separate line.

As the foregoing materials from the start and end of DocumentList.xml show, all I had to do was to insert my own AutoCorrect entries between the beginning and the end.  The beginning (before the first AutoCorrect entry) was like this:

[?xml version="1.0" encoding="UTF-8"?][block-list:block-list list="http://openoffice.org/2001/block-list"]

and the ending was simply

[/block-list:block-list]

(Remember, again, that you need to type "&gt;" where you see "]" etc. in this presentation.)

In between the beginning and the ending, as shown by the examples above (where e.g., "(C)" becomes "©"), the entries each have this format:

[block-list:block name="BEFORE" name="AFTER"]

So if I wanted to have only one AutoCorrect entry in OOo, replacing "BO" with "Barack Obama," here would be my complete DocumentList.xml file:

[?xml version="1.0" encoding="UTF-8"?][block-list:block-list list="http://openoffice.org/2001/block-list"][block-list:block name="BO" name="Barack Obama"][/block-list:block-list]

Therefore, going back to my AC.XLS file in Excel, here's what I had to do:

6.  Insert a column before the BEFORE column.  In other words, the new column A in my spreadsheet would be blank, and column B would contain the characters to be replaced ("BO" in the present example).  The purpose of this blank column, and of other blank columns C and E discussed below, is to contain material that we are going to combine together into one grand entry in column F.  The steps described below provide a basic Excel technique that you may find useful for a variety of applications in the future.

7.  Insert a column between the BEFORE and AFTER column.  In other words, column C in my spreadsheet would now be blank, and column D would contain the replacement ("Barack Obama," in the present example).

8.  In the blank column A, on the first row of the spreadsheet, type the stuff that appears on each individual replacement line before the BEFORE item.  In other words, the first cell, at the top left corner of the AC.XLS spreadsheet, should contain just this:

[block-list:block name="

including the quotation mark.  (Again, you should have an opening angle bracket "&lt;" rather than an opening square bracket "[" on that line.)

9.  In the blank column C, type the stuff that appears between the BEFORE and the AFTER items, including the quotation marks, as follows:

" name="

Finally, in the blank column E, type the stuff that appears after the AFTER item, including the quotation mark, as follows:

"]

replacing the closing square bracket "]" with a closing angle bracket "&gt;".

10.  Column F can now concatenate (i.e., combine) the contents of columns A through E.  This calls for use of Excel's CONCATENATE function.  To enter a function in Excel, just type = and then the name of the function, followed by open parentheses.  Then follow the pop-up tips and close the parentheses.  In this case, the command that goes into cell F1 is:

=CONCATENATE(A1,B1,C1,D1,E1)

If you are having problems so far, it may be helpful to mention two Excel factoids.  First, you can use the ampersand (&amp;) to concatenate instead of CONCATENATE.  Second, you can use CHAR(34) to insert a quotation mark manually.

11.  What you have entered into the blank cells in row 1 of AC.XLS needs to be copied all the way down.  So do that.  Fast way:  go to cell A1; hit Ctrl-C; hold down Shift and hit the End key and then the Home key; use arrow keys so that only column A is highlighted; and then hit Enter.  Do the same with columns C, E, and F.

12.  If all has gone well, you should now have a column F filled with entries in the format shown above:

[block-list:block name="BEFORE" name="AFTER"]

for each of your Word AutoCorrect entries.  These are now in OOo Writer format.  Now you've got to get them into Writer.  Column F in AC.XLS is dependent on columns A through E.  To remove column F from Excel, set it in stone so that its contents do not depend on columns A through E anymore.  To do that, select column F (Shift End-DownArrow) and then (in Excel 2003) select Edit &gt; Copy and then Edit &gt; Paste Special &gt; Values &gt; OK &gt; Enter.  Changes in columns A through E should now have no effect upon column F.

13.  Delete columns A through E.  Save AC.XLS as AC.TXT in Text (MS-DOS) format.  Kill Excel.  Open AC.TXT in Word.  You will see that Excel found it helpful to insert extra quotation marks everywhere.  Make sure that AutoFormat and AutoFormat As You Type are set <span style="font-style: italic;">not</span> to replace straight quotes with smart quotes.  Then, using Ctrl-H (or whatever), replace "" (i.e., double double quotes) with " (i.e., just one double quotation mark) throughout the entire file.

14.  Another set of unwanted quotation marks may appear at the start and end of each line.  Remember, the desired format is

[block-list:block name="BEFORE" name="AFTER"]

not

"[block-list:block name="BEFORE" name="AFTER"]"

(Remember to see "&lt;" when I use "[" as discussed above.)

To get rid of those unwanted extra starting and ending quotation marks, take advantage of the fact that ^p is Microsoft Word's way of saying it's time to start a new line.  (That's for a carriage return.  For a line feed, it's ^l (that's ell, not one).)  Do a Ctrl-H to replace "^p" (including quotation marks) with ^p (having no quotation marks).  Thus

"^p"
becomes
^p

and

"[block-list:block name="BEFORE" name="AFTER"]"
becomes
[block-list:block name="BEFORE" name="AFTER"]

for each item in the list.  You may have to clean up the first and last items in the list manually.  After this, there were still some lingering beginning and ending quotation marks, so I had to run each part of the foregoing replacement again:

"^p
becomes
^p

and

^p"
becomes
^p

15.  You may need to do some additional clean-up, now or later.  In my case, I saw that (C) was now going to produce a question mark (?) rather than a copyright (©) symbol.  Evidently Word and/or Excel didn't use standard ASCII for that symbol.  That would be something I would have to fix later, probably by inserting the symbol into some text and then copying and pasting it into the AutoCorrect dialog box.  I also saw that smart single quotes had sneaked in:  "don't" was now "don?t."  I started to fix that with a manual search and replace, putting apostrophes (') in place of question marks (?); but then I saw that fancy French accents had also gotten mangled into question marks too, and would require individual attention, so I just made it Replace All and to hell with it.

16.  Now it's time to mash it all together, in good old DocumentList.xml format.  Do another global replace (Ctrl-H), this time replacing ^p with nothing.  Your nice clean lines will disappear, and you'll have just one tremendously long paragraph full of autocorrect commands.

17.  Having done a huge amount of work, it's a good idea to do a very belated backup.  While we're at it, let's save it as a different file name.  In my case, I saved it as AC1.TXT.  Choose US-ASCII (Other encoding), don't insert line breaks, and don't allow character substitution.  When I did this, I got a warning that text marked in red would not save correctly in the chosen encoding, but I couldn't find any text in red, else I would have tried to fix it in Word.

18.  Open AC1.TXT in Notepad.  If WordWrap is off, it should look a lot like DocumentList.xml did.  You should be looking at the introductory material, like this:

[?xml version="1.0" encoding="UTF-8"?][block-list:block-list xmlns:block-list="http://openoffice.org/2001/block-list"]

where, again, I have replaced angle with square brackets so this website will not treat it as HTML.  After the introductory material, we have the familiar long list of OOo Writer autocorrect entries.  If you're interested in merging those into the set you're bringing over from Word, you might want to copy them from Notepad into Excel back around step 5, above, and then sort them to insure you aren't installing duplicates or contradictions.

19.  I wasn't interested in OOo's AutoCorrect entries, so I just deleted everything in DocumentList.xml between that introductory material and the ending line, which I will show here in quotation marks so you can see it with its angle brackets intact:

""

Then I pasted the full contents of AC1.TXT into that gap between the starting and ending material in DocumentList.xml.  7-Zip allowed me to save this updated version of DocumentList.xml in the DAT archive; otherwise, I'd have had to save it as a separate file and then zip it into the DAT file as an update.

20.  Having done all this work, I made a backup of acor_en-US.dat.  I ran OOo Writer.  It didn't seem to recognize my definitions.  So I saved this post at this point, rebooted, and tried it again.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
A more recent postupdates this one.


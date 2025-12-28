---
layout: post
title: "Doing a Mass Search in Google"
date: 2007-08-29
---

<div class="post-body">
<p>I was looking for a surgeon who would specialize in fixing collarbones.  The lists of doctors were giving me orthopedists, but were not this specific.  So I decided to try Google searches for each doctor's name provided by my insurance company's list of doctors.  There were a lot of names on the list.  I wanted a way to automate the search.  Here is the approach I used.

First, I narrowed the long list of orthopedists to those who were within a small geographic radius (so as to minimize the hassle, for the person who would drive me home from the hospital after surgery) and who had an affiliation with a highly recommended local hospital.  I copied the contents of that list into Notepad, to remove its HTML content, and then from Notepad into Excel, so as to sort out only those lines that contained doctors' names.  I then eliminated those who did not have an <a href="https://web.archive.org/web/20150703235908/http://www.aetna.com/docfind/docfind_additional_information_aexcel.html">Aexcel designation</a>, as indicated by the health insurance company's list.  I figured out the Google search format that I wanted for these names.  Here is an example:
<blockquote>http://www.google.com/search?num=50&amp;hl=en&amp;q=
orthopedi*+OR+orthopaedi*+indianapolis+clavicle+
marcus+welby+&amp;btnG=Search</blockquote>That all came from a single line in the address box in my Google search results page.  The variable, for each doctor, was the first and last name ("marcus" and "welby," in this example).  So in Excel, I used the &amp; symbol to combine these two fixed portions of the search:
<blockquote>http://www.google.com/search?num=50&amp;hl=en&amp;q=
 orthopedi*+OR+orthopaedi*+indianapolis+clavicle+</blockquote>and
<blockquote>+&amp;btnG=Search</blockquote> with this variable portion in the middle, as shown above:
<blockquote>marcus+welby</blockquote>which would vary, of course, with each doctor.  The point is, I was searching for webpages that would contain references to "clavicle" and to that particular doctor.  As I say, I pasted together the three parts of each search line in Excel, using the &amp; operator.  That is, with the list of doctors' names and the knowledge of what a search for each of them should contain, I came up with a list of searches, like this:
<blockquote>http://www.google.com/search?num=50&amp;hl=en&amp;q=
orthopedi*+OR+orthopaedi*+indianapolis+clavicle
+Fish+Mark D.+&amp;btnG=Search
 
http://www.google.com/search?num=50&amp;hl=en&amp;q=
orthopedi*+OR+orthopaedi*+indianapolis+clavicle
+Fisher+David+&amp;btnG=Search
 
http://www.google.com/search?num=50&amp;hl=en&amp;q=
orthopedi*+OR+orthopaedi*+indianapolis+clavicle
+Fisher+David+&amp;btnG=Search
</blockquote>where, again, each of those sets (shown here in three lines, to keep Blogger from truncating them) comprised a single output line in Excel.  I needed just one more thing, namely, to tell the computer to open each of those lines as separate Google search tabs in Firefox.  To do that, I had to prepend the appropriate command, which was simply "start firefox.exe."  So, using the first example of the three just shown, I wound up with this line:
<blockquote>start firefox.exe http://www.google.com/search?num=50
&amp;hl=en&amp;q=orthopedi*+OR+orthopaedi*+indianapolis
+clavicle+Fish+Mark D.+&amp;btnG=Search</blockquote>I pasted the results into Notepad and saved it as DocSearch.bat.  The "bat" extension told the computer to run this like a program.  Then, realizing that opening a hundred Firefox tabs might cause the system to crash, I pared it down by dividing the file in half and running about 50 searches at a time, calling the batch files DocSearch1.bat and DocSearch2.bat.  This failed because I had forgotten to put quotation marks around the search.  Once I corrected it, like this:
 <blockquote>start firefox.exe "http://www.google.com/search?num=50
&amp;hl=en&amp;q=orthopedi*+OR+orthopaedi*+indianapolis
+clavicle+Fish+Mark D.+&amp;btnG=Search"</blockquote> everything else was fine.  (Note:  Word's smart quotes may not work for this purpose.)  Then it was just a matter of viewing the search pages and deleting the ones that found no link between the named doctor and the clavicle.  For some reason, my insurer's list repeated the same doctors' names multiple times, so I wound up with some duplicate searches.  But when the dust settled, I also wound up with a small number of specialists who looked like they might be on target for what I needed.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

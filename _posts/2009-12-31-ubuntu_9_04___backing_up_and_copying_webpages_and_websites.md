---
layout: post
title: "Ubuntu 9.04:  Backing Up and Copying Webpages and Websites"
date: 2009-12-31
---

<div class="post-body">
<p>As described in <a href="https://web.archive.org/web/20151130171514/http://raywoodcockslatest.blogspot.com/2009/12/ubuntu-backup-with-rsync.html">a previous post</a>, I had been using rsync to make backups of various files.  This strategy was not working so well in the case of webpages and websites, or at least I wasn't finding much guidance that I could understand.  (Incidentally, I had also tried the Windows program <a href="https://web.archive.org/web/20151130171514/http://www.google.com/search?hl=en&amp;q=httrack&amp;sourceid=navclient-ff&amp;rlz=1B3GGGL_enUS318US318&amp;ie=UTF-8">HTTrack Website Copier</a>, but had found it to be complicated and frustrating.  It seemed to want either to download the entire Internet or nothing at all.)<br/>
<br/>
The immediate need driving this investigation was that I wanted to know how to back up a blog.  I used the blog on which I am posting this note as my test bed.<br/>
<br/>
Eventually, I discovered that maybe what I needed to use was <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/">wget</a>, not rsync.  <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html">The wget manual</a> seemed thorough if a bit longwinded and complex, so I tried <a href="https://web.archive.org/web/20151130171514/http://en.wikipedia.org/wiki/Wget">the Wikipedia entry</a>.  That, <a href="https://web.archive.org/web/20151130171514/http://www.veen.com/jeff/archives/000573.html">and another source</a>, gave me the parts of the command I used first:<br/>
<br/>
<blockquote>wget -r -l1 -np -A.html -N -w5 http://raywoodcockslatest.blogspot.com/search?max-results=1000 --directory-prefix=/media/Partition1/BlogBackup1<br/>
</blockquote><br/>
The parts of this wget command have the following meanings:<br/>
<br/>
<ul><li>-r means that wget should <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Recursive-Download">recurse</a>, i.e., it should go through the starting folder and all folders beneath it (e.g., www.website.com/topfolder and also www.website.com/topfolder/sub1 and sub2 and sub3 . . .)<br/>
</li>
<li>-l1 (that's an L-one) means stay at level number one.  That is, don't download linked pages.</li>
<li>-np means "no parent" (i.e., stay at this level or below; don't go up to the parent directory)</li>
<li>-A.html means <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options">Accept only</a> files with this extension (i.e., only .html files)</li>
<li>-N is short for Newer (i.e., only download files that are newer than what's already been downloaded).  In other words, it turns on <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Time_002dStamping">timestamping</a></li>
<li>-w5 means wait five seconds between files.  This is because large downloads can overload the servers you are downloading from, in which case <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Recursive-Download">an irritated administrator</a> may penalize you<br/>
</li>
<li>The URL shown in this command is the URL of this very blog, plus the additional information needed to download all of my posts in one html file.  But it didn't work that way.  What I got, with this command, was each of the posts as a separate html file, which is what I preferred anyway</li>
<li>--directory-prefix indicates where I want to put the download.  If you don't use this option, everything will go into the folder where wget is running from.  I came across <a href="https://web.archive.org/web/20151130171514/http://www.linuxforums.org/forum/linux-applications/99494-wget-default-download-directory.html#post491723">a couple</a> of <a href="https://web.archive.org/web/20151130171514/http://www.mail-archive.com/wget@sunsite.dk/msg08468.html">suggestions</a> on what to do if your path has spaces in it, but I hadn't gotten that far yet<br/>
</li>
</ul><br/>
Incidentally, I also ran across another possibility that I didn't intend to use now, but that seemed potentially useful for the future.  Someone asked if there was a way to save each file with a unique name, so that every time  you run the wget script, you get the current state of the webpage.  <a href="https://web.archive.org/web/20151130171514/http://www.mail-archive.com/wget@sunsite.dk/msg09186.html">One answer</a> involved using <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/coreutils/manual/coreutils.html#mktemp-invocation">mktemp</a>.  Also, it seemed potentially useful to know that I could download all of the .jpg files from a webpage by using something like this:  wget -e robots=off -r -l1 --no-parent -A.jpg http://www.server.com/dir/<br/>
<br/>
The first download was pretty good, but I had learned some more things in the meantime, and had some questions, so I decided to try again.  Here's the script I used for my second try:<br/>
<blockquote>wget -A.html --level=1 -N -np -p -r -w5 http://raywoodcockslatest.blogspot.com --directory-prefix=/media/Partition1/BlogBackup2<br/>
</blockquote><br/>
This time, I arranged the options (or at least the short ones) in alphabetical order.  The -p option indicated that images and style sheets would be downloaded too.  I wasn't sure I needed this -- the basic html pages looked pretty good in my download as they were -- but I thought it might be interesting to see how much larger that kind of download would be.  I used a shorter version of the source URL and I designated a different output directory.<br/>
<br/>
I could have added -k (long form:  --<a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Recursive-Retrieval-Options">convert-links</a>) so that the links among the downloaded html pages would be modified to refer to the other downloaded pages, not to the webpage where I had downloaded them from; but then I decided that the purpose of the download was to give me a backup, not a local copy with full functionality; that is, I wanted the links to work properly when posted as webpages online, not necessarily when backed up on my hard drive.  I used the long form for the "level" option, just to make things clearer.  Likewise, with <a href="https://web.archive.org/web/20151130171514/http://www.gnu.org/software/wget/manual/wget.html#Robot-Exclusion">a bit of learning</a>, I decided against using the -erobots=off option.  There were probably a million other options I could have considered, in the long description of wget in the official manual, but these were the ones that others seemed to mention most.<br/>
<br/>
The results of this second try were mixed.  For one thing, I was getting a lot of messages of this form:<br/>
<br/>
<blockquote>2010-01-01 01:43:03 (137 KB/s) - `/[target directory]/index.html?widgetType=BlogArchive&amp;widgetId=BlogArchive1&amp;action=toggle&amp;dir=open&amp;toggle=MONTHLY-1196485200000&amp;toggleopen=MONTHLY-1259643600000' saved [70188]<br/>
<br/>
Removing /[target directory]/index.html?widgetType=BlogArchive&amp;widgetId=BlogArchive1&amp;action=toggle&amp;dir=open&amp;toggle=MONTHLY-1196485200000&amp;toggleopen=MONTHLY-1259643600000 since it should be rejected.<br/>
</blockquote><br/>
I didn't know what this meant, or why I hadn't gotten these kinds of messages when I ran the first version of the command (above).  It didn't seem likely that the mere rearrangement of options on the wget command line would be responsible.  To find out, I put it out of its misery (i.e., I ran "pkill wget" in a separate Terminal session) and took a closer look.<br/>
<br/>
Things got a little confused at this point.  Blame it on the late hour.  I thought, for a moment, that I had found the answer.  A quick glance at <a href="https://web.archive.org/web/20151130171514/http://www.linuxforums.org/forum/linux-applications/129038-wget-since-should-rejected.html">the first forum</a> that came up in response to <a href="https://web.archive.org/web/20151130171514/http://www.google.com/search?hl=en&amp;q=wget+removing+%22should+be+rejected%22&amp;sourceid=navclient-ff&amp;rlz=1B3GGGL_enUS318US318&amp;ie=UTF-8">my search</a> led me to recognize that, of course, my command was contradictory:  it told wget to download style sheets (-p), but it also said that only html files would be accepted (-A.html).  But then, unless I muddled it somehow, it appeared that, in fact, I had not included the -p option after all.  I tried re-running version 2 of the command (above), this time definitely excluding the -p option.  And no, that wasn't it; I still got those same funky messages (above) about removing index.html.  So the -p option was not the culprit.<br/>
<br/>
I tried again.  This time, I reverted to using exactly the command I had used in the first try (above), changing only the output directory.  Oh, and somewhere in this process, I shortened the target URL.  This gave me none of those funky messages.  So it seemed that the order of options on the command line did matter, and that the order used in the first version (above) was superior to that in the second version.  To sum up, then, the command that worked best for me, for purposes of backing up my Blogger.com (blogspot) blog, was this:<br/>
<br/>
<blockquote>wget -r -l1 -np -A.html -N -w5 http://raywoodcockslatest.blogspot.com --directory-prefix=/media/Partition1/BlogBackup1<br/>
</blockquote><br/>
Since there are other blog hosts out there, I wanted to see if exactly the same approach would work elsewhere.  I also had <a href="https://web.archive.org/web/20151130171514/http://raywoodcock.wordpress.com/">a WordPress blog</a>.  I tried the first version of the wget command (above), changing only the source URL and target folder, as follows:<br/>
<br/>
<blockquote>wget -r -l1 -np -A.html -N -w5 http://raywoodcock.wordpress.com/ --directory-prefix=/media/Partition1/WordPressBackup<br/>
</blockquote><br/>
This did not work too well.  The script repeatedly produced messages saying "Last-modified header missing -- time-stamps turned off," so then wget would download the page again.  As far as I could tell from the pages I examined in <a href="https://web.archive.org/web/20151130171514/http://www.google.com/search?hl=en&amp;safe=off&amp;rlz=1B3GGGL_enUS318US318&amp;num=50&amp;newwindow=1&amp;q=%22last+modified+header+missing%22+wget&amp;btnG=Search">a search</a>, there was no way around this; apparently WordPress did not maintain time stamps.<br/>
<br/>
The other problem was that it did not download all of the pages.  It would download only one index.html file for each month.  That index.html file would contain an actual post, which was good, but what about all the other posts from that month?  I modified the command to specify the year and month (e.g., http://raywoodcock.wordpress.com/2009/03/).  This worked.  Now the index.html file at the top of the subtree (e.g., http://raywoodcock.wordpress.com/2009/03/index.html) would display all of the posts from that month, and beneath it (in e.g., .../2009/03/01) I had named subfolders for each post, each of which contained the index.html file displaying that particular post.  So at this rate, I would have to write wget lines for each month in which I had posted blog entries.  But then I found that removing the -A.html option solved the problem.  But if I ran it at the year level, it worked only for some months, and skipped others.  I tried what appeared to be <a href="https://web.archive.org/web/20151130171514/http://savannah.gnu.org/bugs/index.php?27473">the suggestion</a> of running it twice at the year level (i.e., at .../wordpress.com/ with an ending slash), with --save-cookies=cookies.txt --load-cookies=cookies.txt --keep-session-cookies.  That didn't seem to make a difference.  So the best I could do with a WordPress blog, at this point, was to enter separate wget commands for each month, like this:<br/>
<br/>
<blockquote>wget -r -l1 -np -N -A.html -w5 http://raywoodcock.wordpress.com/2009/01 --directory-prefix=/media/Partition1/WordPressBackup<br/>
</blockquote><br/>
I added back the -A.html option, as shown, because it didn't seem to hurt anything; html pages were the only ones that had been downloaded anyway.<br/>
<br/>
Since these monthly commands would re-download everything, I would run the older ones only occasionally, to pick up the infrequent revision of an older post.  I created a bunch of these, for the past and also for some months into the future.  I put the historical ones in a script called backup-hist.sh, which I planned to run only occasionally, and I put the current and future ones into my backup-day.sh, to run daily.<br/>
<br/>
But, ah, not so fast.  When I tried this on another, unrelated WordPress blog, it did not consistently download all posts for each month.  I also noticed that it duplicated some posts, in the sense that the higher-level (e.g., month-level) index.html file seemed to contain everything that would appear on the month-level webpage on WordPress.  So, for example, if you had your WordPress blog set up to show a maximum of three posts per page, this higher-level webpage would show all three of those.  The pages looked good; it was just that I was not sure how I would use this mix in an effective backup-and-restore operation.  This raised the question for my own blog:  if I ever did have to restore my blog, was I going to examine the HTML for each webpage manually, to re-post only those portions of text and code that belonged on a given blog page?<br/>
<br/>
I decided to combine approaches.  First, since it was yearend, I made a special-case backup of all posts in each blog.  I did this by setting the blogs to display 999 posts on one page, and then printed that page as a yearend backup PDF.  Second, I noticed that rerunning these scripts seemed to catch additional posts on the subsquent passes.  So instead of separating the current and historical posts, I decided to stay with the original idea of running one command to download each WordPress post.  I would hope that this got most of them, and for any that fell through the crack, I would refer to the most recent PDF-style copy of the posts.  The command I decided to use for this purpose was of this form:<br/>
<br/>
<blockquote>wget -r -l1 -np -N -A.html -w5 [URL] --directory-prefix=/media/Backups/Blogs/WordPress<br/>
</blockquote><br/>
I had recently started one other blog.  This one was on Livejournal.com.  I tried the following command with that:<br/>
<br/>
<blockquote>wget -r -l1 -np -N -A.html -w5 http://rwclippings.livejournal.com/ --directory-prefix=/media/Backups/Blogs//LiveJournal<br/>
</blockquote><br/>
This was as far as I was able to get into this process at this point.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

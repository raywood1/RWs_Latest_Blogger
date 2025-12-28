---
layout: post
title: "Windows Explorer Has Stopped Working:  FreeCommander and Other Alternatives to Windows Explorer"
date: 2012-06-21
---

<div class="post-body">
<p><div style="text-align: left;">
I was using Windows 7.  I installed a new EVGA video card.  Immediately, I began getting "Windows Explorer has stopped working" error messages, especially when I would right-click on a file or folder and try to move it somewhere else.  <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?q=%22Windows+7%22+%22Windows+Explorer+has+stopped+working%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> led to <a href="https://web.archive.org/web/20151121003238/http://support.microsoft.com/kb/2694911" target="_blank">a Microsoft webpage</a> that identified the video driver as the first culprit.  I had also had problems with the previous video card (also an EVGA), but had partially resolved those by rolling back to an earlier driver.  That solution did not work this time.  While awaiting EVGA's reply to a service request, I decided to look into Windows Explorer replacements.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
This was not the first time I'd had problems with Windows Explorer.  As far back as the late 1990s, I had found <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=JI2&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=PowerDesk98+OR+%22PowerDesk+98%22&amp;oq=PowerDesk98+OR+%22PowerDesk+98%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_l=serp.3...8576.14275.0.14768.8.8.0.0.0.0.156.1010.1j7.8.0.cish..0.0.VdzDCAd3wsg" target="_blank">PowerDesk 98</a> to be a superior alternative to Windows Explorer in Windows 95 and 98.  I had grown so attached to it that I was still occasionally looking, years later, to see whether they had come out with an update.  It just offered a lot of features and advantages that I hadn't found in Windows Explorer.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
To me and to at least some other users, Windows Explorer in Windows 7 had seemed like a step backwards from Windows Explorer under Windows XP.  Some functionality was lost; some new problems appeared.  For example, not long before this latest "stopped working" issue, I started getting the unwanted reminder that "This folder is shared with other people," which would come up when I tried to move or delete a folder.  Despite <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2012/04/windows-7-eliminating-this-folder-is.html" target="_blank">some effort</a>, I hadn't been able to get rid of that.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: center;">
<div style="text-align: center;">
<b>FreeCommander</b>
</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
In the past year or so, after repeated albeit <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/01/windows-7-choosing-replacement-for.html" target="_blank">superficial looks</a> at various Windows Explorer alternatives, I had started using <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?q=FreeCommander&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">FreeCommander</a> for <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2012/05/batch-converting-multiple-word-doc.html" target="_blank">some tasks</a>.  One thing pushing me in that direction was that, in Win7, Windows Explorer seemed eager to forget file selections.  That is, I could go through a list of files and select some; but then Windows Explorer would de-select them if I (or anything else) changed the file list.   In FreeCommander, unlike Windows Explorer, I could select files, and they would tend to stay selected -- even if I deleted one entry from the list (from within another program, for example, or another Windows Explorer session) or if I re-sorted the list by file size rather than file name.  FreeCommander wasn't perfect about this.  At this writing, a quick test revealed that it, too, would lose selections if I sorted by file type.  Nonetheless, FreeCommander was much better than the current version of Windows Explorer in this regard, in my ordinary usage.  FreeCommander was also not crashing, at present, during these instances when I was getting these "Windows Explorer has stopped working" messages.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
FreeCommander also did a better job of putting me where I wanted to be.  It would remember my last location, and would never put me in a pseudo-folder under Ray (my user name in the navigation pane), as Windows Explorer insisted on doing, when I actually wanted to be in Computer &gt; Drive D &gt; Folder X.  I also liked that FreeCommander did not lard down my navigation pane with all sorts of Libraries and other top-level folders (which, to some degree, I had been able to eliminate from Windows Explorer by using <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/11/win7regeditreg-updated.html" target="_blank">registry tweaks</a>).</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
On the downside, unlike Windows Explorer, FreeCommander did not preserve a memory of multiple sessions after a reboot.  That is, if I had three Windows Explorer sessions and three FreeCommander sessions open before a crash, all focused on different folders, I would wind up with those same three Windows Explorer sessions after the crash, but only one FreeCommander session (or pair of sessions, if I was using FreeCommander's split-window feature).  (I think I had to enable an option somewhere in Windows, or in a tweaking program, to get this functionality from Windows Explorer.)  Then again, FreeCommander's option to open or close tabs (via View &gt; New Folder Tab or else Ctrl-T and Ctrl-W) had the potential to make it unnecessary to have so many Windows Explorer sessions open at once.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
At first, I did not realize that I could turn FreeCommander's split-window feature off.  There were times when it was convenient to be able to view two separate lists of files -- from, say, two different drives -- within one FreeCommander session (and to split the screen either horizontally or vertically).  The options to split the window or to view just the left or right sides were available through the menu (View &gt; Split Window) or by shortcuts (Ctrl-Shift F1, F2, and F3).  If I had multiple tabs open on one side, it would remember them, even if it was currently displaying only the other side.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
I didn't like that FreeCommander wouldn't show me a full navigation tree (in the left-hand pane) for all drives:  instead, it was focused on just one drive.  To switch drives, I had to go to the top of the screen and select another drive from a list or combo box (configurable via Extras &gt; Settings &gt; View &gt; Drives).  That seemed inconvenient, and that top bar took up screen space.  One workaround might be to have a different tab open for each drive, and just navigate within that tab whenever I wanted to work in a different drive.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
I had some <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/07/windows-7-batch-files-that-run-things.html" target="_blank">batch files</a> that would open various Windows Explorer sessions automatically, on certain dates or at certain times of day.  There was a simple <a href="https://web.archive.org/web/20151121003238/http://support.microsoft.com/kb/130510" target="_blank">command format</a> to specify which folder a Windows Explorer session should display:  start explorer.exe /e,"D:\Folder Name\File Name.doc."  I wondered if I could do something similar with FreeCommander.  It would let me specify a pair of starting folders (via Extras &gt; Settings &gt; Start Program), but could I go further than that?  <a href="https://web.archive.org/web/20151121003238/http://www.freecommander.com/fc_faq_en.htm" target="_blank">It appeared</a> that, to match what I was doing with Windows Explorer in this regard, I would have to set up a relatively complicated arrangement with alternative .ini files in FreeCommander.  (I wasn't entirely sure whether this was what the program's author meant when <a href="https://web.archive.org/web/20151121003238/http://www.freecommander.com/fc_details_en.htm" target="_blank">he said</a> that "several layouts can be saved.")  I probably wouldn't go to that trouble for the most part, though I could imagine setting up a couple of really complicated sets of tabs and linking to them with shortcuts on my semi-portable <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/01/windows-7-setting-up-customized-start.html" target="_blank">customized Start Menu</a>.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
One feature of FreeCommander that I liked immediately was its more condensed display.  Windows Explorer had seemed to add more space between lines, going from Windows XP to Windows 7.  I wasn't sure why.  The result was that Windows Explorer would display 38 items at a time (or a few more, if the top menu and bottom status bar were turned off) while FreeCommander would display 45 -- and those 45 would be presented in a larger, more readable font.  FreeCommander's status bar was also more informative, telling me that I had selected 45 out of 110 items within a folder, and such information would remain visible in the status bar, whereas for some reason Windows Explorer would sometimes replace it with the date when a folder was created.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
One thing I didn't like about the FreeCommander interface was that it didn't have an address bar into which I could paste an address for a quick switch to a different directory.  In FreeCommander, I had to use the Edit menu to get a folder's address for pasting elsewhere, and the Folder &gt; Go to Folder menu pick to paste an address from elsewhere into FreeCommander.  These steps were inconvenient because (a) they required more steps and (b) they were in two different locations, which made things a little more confusing.  On the other hand, FreeCommander offered the option (via Alt-Ins or Edit &gt; Copy Full Name as Text) of copying both the path and the file name in one step, which Windows Explorer did not do.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
I felt that FreeCommander needed some reorganization and clarification.  There was apparently a new <a href="https://web.archive.org/web/20151121003238/http://www.freecommander.com/fc_beta_en.htm" target="_blank">XE version</a> in the works; it appeared that <a href="https://web.archive.org/web/20151121003238/http://www.freecommander.com/fc_logchanges_en.htm" target="_blank">the present version</a> dated from 2009.  On the other hand, I wasn't sure how much I could complain about the program's offerings.  Quite aside from the fact that it was free,  FreeCommander had all kinds of features not available in Windows Explorer, and there didn't seem to be much that WinEx could do that FreeCommander couldn't.  I figured that, with or without reorganization, I would become familiar with FreeCommander's menus and possibilities if I began using it more extensively. 

<br/>
<br/></div>
<div style="text-align: left;">
One particular area that I did not explore, within FreeCommander, was its offering of various built-in utilities.  These included file viewing (e.g., hex, image, binary formats), zipping, searching, wiping, checksums, listing, renaming, and splitting; multiple file renaming; directory comparison and synchronization; and the option to add more tools to the list.  I didn't look into this because I was not sure how much I would use these tools.  As indicated in other posts in this blog, a lot of problems and questions could arise when you really got into the details of these sorts of functions.  For example, I had paid some attention, in recent years, to <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/01/synchronizing-two-computers-detailed.html" target="_blank">GoodSync</a> and <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2012/03/synchronizing-two-computers-goodsync.html" target="_blank">alternatives</a> for synchronization between computers, and to <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2012/03/backup-arrangement-with-beyond-compare.html" target="_blank">Beyond Compare</a> and <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2010/06/ubuntu-1004-rsync-failed-to-set.html" target="_blank">rsync</a> for comparing a computer's files against backups.  I was hesitant to replace those sorts of dedicated tools with what might be a simplistic form of file comparison that could make a mess.

</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
In terms of other conveniences, there was quite a list of <a href="https://web.archive.org/web/20151121003238/http://www.freecommander.com/fc_ShortCuts_en.htm" target="_blank">hotkeys</a>.  FreeCommander was available in both installed and portable versions.  There were <a href="https://web.archive.org/web/20151121003238/http://www.forum.freecommander.com/" target="_blank">user forums</a> with a total of maybe 10,000 posts.  It was definitely a stable and worthy program.  Given my previous searches and my experiences to date with FreeCommander, the question for me at this point was whether there was some other Windows Explorer alternative that was even better.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: center;">
<div style="text-align: center;">
<b>Other Windows Explorer Alternatives</b>
</div>
<div style="text-align: left;">
<b><br/></b></div>
<div style="text-align: left;">
Along with various ways to <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;tbo=1&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;biw=1090&amp;bih=930&amp;tbs=qdr%3Ay&amp;q=%22Windows+7%22+%22modify+Windows+Explorer%22+OR+%22tweak+Windows+Explorer%22+OR+%22customize+Windows+Explorer%22&amp;oq=%22Windows+7%22+%22modify+Windows+Explorer%22+OR+%22tweak+Windows+Explorer%22+OR+%22customize+Windows+Explorer%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_l=serp.3...13115.24097.0.24683.31.30.0.0.0.2.341.3478.14j12j2j2.30.0.cish..0.0.I6y2BDP2jJ0" target="_blank">customize Windows Explorer</a> (which did not presently appeal to me, given the fact that it was crashing every time I looked at it sideways), there were various <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;tbo=1&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;biw=1090&amp;bih=930&amp;tbs=qdr%3Ay&amp;q=%22Windows+7%22+%22Windows+Explorer+replacements%22+OR+%22alternatives+to+Windows+Explorer%22&amp;oq=%22Windows+7%22+%22Windows+Explorer+replacements%22+OR+%22alternatives+to+Windows+Explorer%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_l=serp.3...14957.24639.0.24951.49.43.4.0.0.0.258.4160.21j21j1.43.0.cish..0.0.F5Wpd8bG6VM" target="_blank">lists</a> of Windows Explorer alternatives.  For example, a <a href="https://web.archive.org/web/20151121003238/http://www.pctips3000.com/top-5-windows-explorer-replacements/" target="_blank">PCTIPS 3000 webpage</a> briefly listed FreeCommander as one of the best (free) Windows Explorer replacements, along with Q-Dir, Explorer XP, NexusFile, and CubicExplorer.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
A potentially manipulable <a href="https://web.archive.org/web/20151121003238/http://www.nsaneforums.com/topic/130624-which-windows-explorer-replacement-if-any-do-you-use/" target="_blank">poll</a> suggested that users of one forum were using Total Commander, Directory Opus, XYplorer, Explorer++, Q-Dir, and FreeCommander, in approximately that (descending) order.  A <a href="https://web.archive.org/web/20151121003238/http://superuser.com/questions/90/replacement-for-windows-explorer" target="_blank">SuperUser thread</a> ranked the leading Windows Explorer alternatives as being (in this order) Total Commander, QTTabBar, FreeCommander, FarManager, XYplorer, Directory Opus, the command line, xyplorer2 <a href="https://web.archive.org/web/20151121003238/http://www.google.com/search?q=xyplorer2&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">(?)</a>, Q-Dir, TeraCopy <a href="https://web.archive.org/web/20151121003238/http://codesector.com/teracopy/" target="_blank">(!)</a>, CubicExplorer, SpeedCommander, Altap Salamander, Xplorer2, muCommander, and others recommended by at least one person.  <a href="https://web.archive.org/web/20151121003238/http://www.technize.net/30-free-and-paid-alternatives-to-windows-explorer-file-manager/" target="_blank">Another webpage</a> listed at least 30 free and paid alternatives to Windows Explorer.  <a href="https://web.archive.org/web/20151121003238/http://www.techrepublic.com/blog/five-apps/five-free-replacements-for-windows-explorer/1103" target="_blank">TechRepublic</a> listed these as its preferred free Windows Explorer replacements:  CubicExplorer, Explorer++, Xplorer2, NexusFile, and Q-Dir.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
<a href="https://web.archive.org/web/20151121003238/http://en.wikipedia.org/w/index.php?title=Comparison_of_file_managers" target="_blank">Wikipedia</a> provided a comparison of many such programs.  It appeared that they could first be divided into free and nonfree categories.  Since I was not likely to pay for something that FreeCommander (not to mention Windows Explorer) could already do for free, I focused on the free ones.  This removed Total Commander ($40) from consideration -- a perennial favorite that I had <a href="https://web.archive.org/web/20151121003238/http://raywoodcockslatest.blogspot.com/2011/01/windows-7-choosing-replacement-for.html" target="_blank">tried briefly</a> but hadn't found that terribly impressive.  The nonfree group also included some other popular entries from the lists cited above:  Directory Opus ($85!), XYplorer ($43), SpeedCommander (~$55), Xplorer2 ($30), and Salamander ($30) -- assuming the lite versions available for some of these programs would fail to match a competitive freeware alternative like FreeCommander.  It was not clear how recently the Wikipedia page had been updated -- it didn't include any reference to some of the programs listed above, and therefore might not reflect pricing changes (including decisions to offer a given program for free, or to stop doing so).  Then again, I guessed that any developer who was on top of the game would know of this Wikipedia page and would be updating the pricing information pretty quickly.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
<a href="https://web.archive.org/web/20151121003238/http://www.explorerxp.com/" target="_blank">ExplorerXP</a> did not appear to have been updated for Windows 7.  I had encountered other programs, great in Windows XP, that had stumbled at one point or another in Win7.  Given the number of competing programs, I tentatively ruled out those that were not clearly Windows 7 compatible.  I was also inclined to exclude those whose screenshots provided a clunky interface and/or limited information -- notably, <a href="https://web.archive.org/web/20151121003238/http://www.farmanager.com/screenshots.php?l=en" target="_blank">Far Manager</a>.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
The leading free Windows Explorer alternatives, other than FreeCommander, thus appeared to include Q-Dir, NexusFile, CubicExplorer, Explorer++, QTTabBar, and muCommander.  The Wikipedia comparison page provided a table indicating the kinds of views that each such program offered.  I considered a Details view option essential.  Evidently no such view was available in CubicExplorer.  I was not sure if a twin-panel or tab options were essential, but CubicExplorer seemed to lack those features too.  As noted above, I was not especially interested in the utilities (e.g., file compression) that such programs might offer, so I did not examine the Wikipedia tables on those matters.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
I looked at the webpages for the ones that remained on my list:  <a href="https://web.archive.org/web/20151121003238/http://www.softwareok.com/?seite=Freeware/Q-Dir" target="_blank">Q-Dir</a>, <a href="https://web.archive.org/web/20151121003238/http://www.xiles.net/nexusfile/" target="_blank">NexusFile</a>, <a href="https://web.archive.org/web/20151121003238/http://www.explorerplusplus.com/" target="_blank">Explorer++</a>, <a href="https://web.archive.org/web/20151121003238/http://sourceforge.net/projects/qttabbar/" target="_blank">QTTabBar</a>, and <a href="https://web.archive.org/web/20151121003238/http://www.mucommander.com/" target="_blank">muCommander</a>.  I had previously glanced at QTTabBar but, for reasons I did not recall, had not gone far with it.  On this review, I was not too impressed.  <a href="https://web.archive.org/web/20151121003238/http://sourceforge.net/projects/qttabbar/forums" target="_blank">Its forums</a> seemed to be lonely places; there was an <a href="https://web.archive.org/web/20151121003238/http://sourceforge.net/projects/qttabbar/" target="_blank">indication</a> that it was still in "public beta"; and there were <a href="https://web.archive.org/web/20151121003238/http://superuser.com/questions/90/replacement-for-windows-explorer" target="_blank">remarks</a> of instability and Windows 7 incompatibility.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
Q-Dir's <a href="https://web.archive.org/web/20151121003238/http://www.softwareok.com/?seite=Freeware/Q-Dir/Screenshot-4" target="_blank">screenshots</a> seemed to offer the potential to divide up the screen in a number of interesting ways.  They did not seem to display a tabbed browsing option, but I gathered that tabbing was an option somehow.  There did not appear to be a forum, but the author did provide an array of <a href="https://web.archive.org/web/20151121003238/http://www.softwareok.com/?seite=faq-Q-DIR&amp;faq=0" target="_blank">FAQs</a>, with perhaps some English-language limitations.  My principal reaction at this point was that, having glanced ahead at Explorer++, I thought it might be a little more of what I was looking for.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
NexusFile had a snazzy webpage, especially for people who like black, but I wasn't so sure about its content.  Forum posts didn't seem to be categorized, and there didn't seem to be a way of searching them.  Generally, as with most of the other programs noted here, the information provided on the webpages did not seem responsive to the detailed concerns noted in my review of FreeCommander (above).  That might have been alleviated in some cases if I had plunged into their FAQs in detail.  It would not have been alleviated in the case of NexusFile, whose <a href="https://web.archive.org/web/20151121003238/http://www.xiles.net/nexusfile/#faq" target="_blank">FAQs page</a> had a total of six questions.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
Between muCommander and Explorer++, a comparison of forum posts suggested that muCommander was more of a cross-platform option, with many of its posts coming from Linux users.  There also seemed to be somewhat more recent activity in the Explorer++ forums.  MuCommander, not listed on the Wikipedia comparison page (above) at this point, apparently did not yet have <a href="https://web.archive.org/web/20151121003238/http://trac.mucommander.com/wiki/FAQ" target="_blank">tab support</a>.  Between the two, then, I was inclined toward Explorer++.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
The thing is, I wasn't seeing anything in any of these alternatives that FreeCommander lacked.  At present, the best course of action seemed to be to focus on FreeCommander, to the extent that it performed more stably and functionally than Windows Explorer.  I decided that I would return to these alternatives if, at some point, neither Windows Explorer nor FreeCommander seemed to be working well for me.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: center;">
<div style="text-align: center;">
<b>Suggestion</b>
</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
It seemed, in particular, that while these various programs were trying to compete to be the best Swiss Army knife, doing everything fairly well, there might actually be some merit in taking more of a niche approach.  For example, I tended to use a few folders very frequently.  I had not really worked out the whole thing of using Favorites, links, Send To, Move To, Copy To, and other ways of moving and sorting my attention, or my files, among these key folders.  It would have been very helpful if, for instance, I could have just punched a function key or other hotkey to move a file to any of a number of previously designated folders.  I often found myself sorting files; this would have been very useful.</div>
<div style="text-align: left;">
<br/></div>
<div style="text-align: left;">
In that particular example -- and that was obviously not the only specialized way in which people might use Windows Explorer -- there seemed to be a lot of room for people to develop tools that would help me navigate across my computer adequately, while providing a really special experience among key locations.  In that case, I could easily imagine running this other program along with (not "instead of") Windows Explorer or FreeCommander.
</div>
</div>
</div>
</div></p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I notified the FreeCommander forum of this post.  There may be some discussion atthat location.

**raywood**:
I was not prepared to discount the possibility thatsome newly installed programor virus was causing the "Windows Explorer has stopped working" problem.EVGA tech support came back with this:The problem you are describing is not likely related to the video card, but there are a few steps you can take to test the video card.Please run EVGA Precision, and check the temperature of the card at idle and under load. The temperature should not be going above 97c under load.Please boot into your BIOS settings and check the output voltage of the 12v rail of your power supply. The voltage should be between 11.4v to 12.6v and not fluctuating by ±0.05v or more. Check your RAM with MemTest86 and run a stress test with OC scanner for about 30 minutes to test for artifacting on the card. I would also recommend setting your RAM timings manually, according to the documentation from the manufacturer of your RAM.If possible, please test the card in another system or test another card in this system to rule out any possible hardware problem with the current system. Also test with a different power supply if possible.

**raywood**:
Withfurther use, I began to think that Explorer++ was visibly superior to FreeCommander.

**raywood**:
Regarding the EVGA video card, I don't believe the problem was with any of the hardware items listed in their tech support reply.  Temperature was not a problem; voltage was fine.  I had recently done a Memtest.  It wasn't just one card; it was two.  There were two likely explanations.  One, sad to say, was dust:  I detected dust in the connector.  The other was the driver.  This time around, I uninstalled all NVIDIA drivers, rebooted, and reinstalled the 285.62 driver.  That was the one that had worked best with the previous card.  It was about eight months old at this point.  At the moment of this writing, Windows Explorer was working fine.  I did think that I would continue to use Explorer++ as a Windows Explorer replacement and as my primary file management utility, though, at least for a while.  There were a lot of things to like about it.

**svatas**:
After reading of that post I am really missing 2 programs which I am using on some computers after my administration :Unreal commander (http://x-diesel.com)This is a freeware and program which has an inspiration in Total Commander. This product is stable and very handfull.Double commander (http://doublecmd.sourceforge.net)Even it is in beta version, this product is really stable and multiplatform. It is opensource product and if there is a lack of your favorite functionality, you can try to push developers to implement it.

**Anonymous**:
I too had issues with Win7 Explorer and missed much of XP. I was able to 'fix' much of Win7 Explorer with QTTabBar and various registry tweaks, but it was much work.. Still not happy, I tried all the popular Explorer alternatives. In the end I settled with CubicExplorer. It has everything I was looking for and more. It has tabs that you can move/drag items into, custom detail views. It does not have a double pane feature, but I like to just open another window for that. CubicExplorer is my default file manager now. I'm happy.

**Anonymous**:
Ray,  just a "blast-from-the-past" comment:  Remember XTREE GOLD?OK,  there is a Windows version.  ZTREE-WIN.  Have a look at it,  it's not a freebie,  but you  get a month to try it.I use it all the time,.  never bother with Explorer.

**Boy**:
You copy pasted from https://askmeboy.com/windows-explorer-has-stopped-working-freecommander-and-other-alternatives-to-windows-explorer/ :P

**raywood**:
Boy -- you've got it backwards. Look at the site you've named -- you'll see that the text refers to "Ray." They copy-pasted from me.


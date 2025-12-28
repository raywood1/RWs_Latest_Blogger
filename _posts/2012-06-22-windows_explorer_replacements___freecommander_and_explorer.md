---
layout: post
title: "Windows Explorer Replacements:  FreeCommander and Explorer++"
date: 2012-06-22
---

<div class="post-body">
<p>In <a href="https://web.archive.org/web/20151121003121/http://raywoodcockslatest.blogspot.com/2012/06/windows-explorer-has-stopped-working.html" target="_blank">a previous post</a>, I looked at replacements for Windows Explorer ("WinEx"), including especially FreeCommander.  The runner-up, at that point, was Explorer++.  Further experience with FreeCommander prompted me to take a closer look at Explorer++ after all.  This post provides further information on these two utilities.<br/>
<br/>
As I used FreeCommander, I was surprised to find that a few right-click (context menu) options were missing.  For example, I often used LockHunter to find out why Windows was not letting me move or delete a certain file or folder.  But in FreeCommander, I was no longer seeing the context menu question, "What is locking this file?"  That option did continue to appear in Explorer++, as it had appeared in WinEx.  One possible explanation was that FreeCommander did not offer a 64-bit version, whereas Explorer++ did, and I was using the 64-bit version of LockHunter.<br/>
<br/>
Another problem in both FreeCommander and Explorer++ was that I no longer had the option to create a new text file in a specified folder.  That option had been available in WinEx, as I recalled, via File &gt; New &gt; Text File.  I was pretty sure there was a way to create a new text file in FreeCommander.  It seemed to me that I had done so by accident, once or twice, while trying to do something else with a familiar command from WinEx.  But I was not seeing that option on the menu nor in the list of shortcuts, and likewise in Explorer++.  <a href="https://web.archive.org/web/20151121003121/http://www.petri.co.il/quickly_create_txt_file_from_cmd.htm" target="_blank">Workarounds</a> in either program were to open a command window in the selected folder and type one of these options:<br/>
<ul>
<li>copy con filename.txt Enter.  Then type the text.  End with F6 or Ctrl-Z.</li>
<li>echo [a line of text to put into new text file] &gt; filename.txt</li>
<li>notepad filename.txt Enter</li>
</ul>
Both FreeCommander and Explorer++ made the command window available in multiple ways:  via Ctrl-D or menu pick in FreeCommander, via menu pick in Explorer++, and via toolbar icon in both programs.  Both also allowed the customized context menu option to "Open command window here," available through <a href="https://web.archive.org/web/20151121003121/http://raywoodcockslatest.blogspot.com/2011/12/windows-7-tweaked-installation-latest.html" target="_blank">Ultimate Windows Tweaker</a>.  But the toolbar itself, the most readily accessible of these options, was smaller and less obtrusive in Explorer++ because it could be made to fit on the same line (at the top of the screen) as the address bar and the list of drives, whereas FreeCommander insisted on putting the toolbar (if I opted to display it) on its own separate row, and with somewhat larger icons.<br/>
<br/>
Unlike FreeCommander, it was not necessary to display a toolbar listing all drives in Explorer++, because the navigation pane already showed all drives, as in WinEx.  Also like WinEx, Explorer++ allowed me to customize the toolbar area by right-clicking on it.  By contrast, FreeCommander required me to go to Extras &gt; Settings &gt; View &gt; Toolbar; and once there, I had to save changes to each segment of the toolbar separately.  Explorer++ offered more toolbar icons that I was likely to find useful, including Back, Forward, and Up buttons.<br/>
<br/>
Explorer++ did not offer the dual panel option.  But in recent weeks, I had not found myself using that option very often in FreeCommander.  I tended to prefer to keep my windows to half-screen width (using the half-screen snap available in Windows 7 via WinKey - left- (or right-) arrow), and a half-screen was too narrow for many filenames.  Moving from one tab to another was an easier way to work among multiple folders.  Explorer++ (unlike FreeCommander) further aided that by offering the option of bookmarking folders.  A bookmark would not create a new tab; it would change the focused folder in the already focused tab.<br/>
<br/>
Unlike FreeCommander, Explorer++ offered the option of being treated as a replacement for WinEx.  This meant that my Start Menu icon (and other menu picks in various programs) that previously would have opened a Windows Explorer session were now opening an Explorer++ session instead.  That option was available via Tools &gt; Options &gt; General tab &gt; Default File Manager.  I still had the option of opening Windows Explorer by typing "explorer" in a command box; hence, batch commands designed to open WinEx to a particular folder would still do so.<br/>
<br/>
FreeCommander appeared to offer more <a href="https://web.archive.org/web/20151121003121/http://www.forum.freecommander.com/viewtopic.php?t=2020" target="_blank">command-line options</a>.  The <a href="https://web.archive.org/web/20151121003121/http://www.explorerplusplus.com/forum/viewtopic.php?f=2&amp;t=1034&amp;p=3155&amp;hilit=+command+line+#p3155" target="_blank">options in Explorer++</a> appeared to be limited to (a) the possibility of listing multiple directories to open when Explorer++ started up, each opening in its own tab and (b) the possibility of opening virtual folders by using their names (e.g., explorer++.exe "control panel").  I did not think I would need the latter.  The former would be useful only when dealing with relatively short pathnames; Windows might balk at a command listing several long paths.  I obtained information about these options by typing "explorer++.exe /?" at the command prompt.  That seemed to work only in the folder where explorer++.exe was located.<br/>
<br/>
Other points of comparison:  Both Explorer++ and FreeCommander seemed to remember their window positions better than WinEx had done.  Even more so than FreeCommander, Explorer++ displayed much more information onscreen than WinEx:  51 rows, in my configuration.  Regrettably, unlike FreeCommander, the status bar in Explorer++ did not state both the number of items selected and the total number of items in the folder.  Like FreeCommander, Explorer++ did not offer an Undo option, in case I had accidentally moved or deleted the wrong file or folder.  Using Explorer++ or FreeCommander did not stop the annoying "This folder is shared with other people" messages.<br/>
<br/>
As these remarks probably suggest, I found myself gravitating toward Explorer++ shortly after I began using FreeCommander in earnest as my WinEx replacement.  There would surely be many more contrasts between the two.  But I wasn't sure how many of them I would detect, since by this point it seemed that I would mostly just be using Explorer++.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
To get Explorer++.exe commands to work at the command prompt, I copied explorer++.exe and its accompanying config.xml to C:\Windows.

**raywood**:
A later postaddresses Explorer++ configuration.


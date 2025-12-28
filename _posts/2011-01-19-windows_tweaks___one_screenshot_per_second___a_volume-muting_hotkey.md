---
layout: post
title: "Windows Tweaks:  One Screenshot Per Second & A Volume-Muting Hotkey"
date: 2011-01-19
---

<div class="post-body">
<p><strong>The Mute Hotkey</strong><br/>
<br/>
To set up a hotkey that would quickly mute or unmute the computer sound, I followed <a href="https://web.archive.org/web/20171105060315/http://www.howtogeek.com/howto/windows-vista/create-a-shortcut-or-hotkey-to-mute-the-system-volume-in-windows/">advice</a> to download <a href="https://web.archive.org/web/20171105060315/http://www.nirsoft.net/utils/nircmd.html">NirCmd</a>.  I unzipped it to an out-of-the way folder. I right-clicked on nircmd.exe and created a shortcut called Toggle Mute.  I right-clicked it &gt; Properties.  On the extreme right end of the Target line, after the closing quotation mark, I left a space and then typed "mutesysvolume 2" (without quotation marks).  Then I clicked on the Shortcut Key space and hit Ctrl-0 (that is, the zero on the numeric keypad), which happened to be two apparently unused, relatively adjacent keys (therefore easy to find and do with one hand).  I clicked on Change Icon and put this in the box:  "%SystemRoot%\System32\SndVol.exe" -- and then clicked OK (not Browse).  I just left the shortcut there in the NirCmd folder, since all I needed from it was the keyboard shortcut.<br/>
<br/>
<strong>Lots and Lots of Screenshots</strong><br/>
<br/>
Inspired by that experiment with NirCmd, I created a batch file to give me an alternative to video screen capture software.  As long as audio wasn't required, I figured that a series of screenshots would give me better resolution and a smaller cumulative file size than a video would do.  That would suffice for a slideshow.  If I wanted to make a video of it, I could just stretch out the screenshots for as long as I needed to talk about them and draw arrows and such on them.  The batch file was as follows:<br/>
<br/>
<span style="font-family: 'Courier New', Courier, monospace; font-size: x-small;">:: Shotshooter.bat<br/>
<br/>
:: No guarantees. May screw up your system. Proceed at your own risk.<br/>
<br/>
:: Captures a series of screenshots.<br/>
:: See http://www.nirsoft.net/utils/nircmd.html for info on NirCmd.exe.<br/>
<br/>
:: Takes 3600 screenshots, one per second (1000 milliseconds) = one hour.<br/>
:: To kill the program sooner, use Task Manager (Ctrl-Alt-Del) &gt; Processses &gt; nircmd.exe &gt; End Process<br/>
<br/>
:: Screenshots are named by date and time.:: IrfanView provides a fast way to play back results. <br/>
<br/>
D:<br/>
md \Screenshots<br/>
cd "D:\Installation\Start Menu\Programs\Tools\DOS and Batch Files\Multifunction\NirCmd"<br/>
<br/>
nircmd.exe loop 3600 1000 savescreenshot D:\Screenshots\scr~$currdate.yyyy-MM-dd$-~$currtime.HH_mm_ss$.png<br/>
</span></p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
A later postprovides a sample use for Shotshooter.bat.


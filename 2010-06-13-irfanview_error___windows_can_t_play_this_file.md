---
layout: post
title: "IrfanView Error:  Windows Can't Play This File"
date: 2010-06-13
---

<div class="post-body">
<p>I was using Windows XP SP3 as the guest operating system in a VMware Workstation 7 virtual machine (VM) on Ubuntu 10.04 (Lucid Lynx).  For some months, I had been using <a href="https://web.archive.org/web/20151224204115/http://irfanview.com/">IrfanView</a> to play various audio and sometimes video files in that VM.  Suddenly, with a number of files, I started getting this error message:<br/>
<blockquote>IrfanView<br/>
Error:  Windows can't play this file!<br/>
Windows error text:  The specified file cannot be played on the specified MCI device.  The file may be corrupt, not in the correct format, or no file handler available for this format.<br/>
You can try to install additional video/audio codecs from this site:<br/>
http://www.fourcc.org/indexcod.htm<br/>
or try the DirectShow option in 'Properties-&gt;Video'</blockquote>At first I thought this was a problem with IrfanView.  I upgraded to the most current version of IrfanView and tried again.  The error was still there.  I tried playing the file in Windows Media Player (WMP).  I got this message:<br/>
<blockquote>The file you are attempting to play has an extension (.wav) that does not match the file format. Playing the file may result in unexpected behavior.<br/>
Do you want the Player to try to play this content?</blockquote>I said Yes.  It took a few seconds, but then it was able to play the file.  So yes, IrfanView was not handling it as well as WMP, but both of them were telling me there was a problem with the file.  And then I knew what the problem was.  I had bulk-renamed a bunch of files, and had inadvertently named some *.wma files to be *.wav files instead.  I renamed this file to be filename.wma instead of filename.wav.  Now IrfanView was able to play it without a problem.<br/>
<br/>
I was surprised to encounter this problem.  IrfanView had an "Ask to rename if incorrect extension" option, and I had enabled it.  That option had often asked me if I wanted to rename a file that had somehow acquired an incorrect extension.  Why not this time?  Apparently IrfanView was not able to detect the problem in this particular scenario.  I checked what codecs I had been installing.  I was not too sure what codecs were all about, and for some years I had been using <a href="https://web.archive.org/web/20151224204115/http://www.codecguide.com/download_kl.htm">K-Lite Codec Packs</a> as a sort of all-purpose Band-Aid.  But as I checked on it, it appeared that I had just been reinstalling the same old copy of version 3.5.9 or possibly 4.7.0, whereas K-Lite was now up to version 6.0.4.  So I <a href="https://web.archive.org/web/20151224204115/http://www.codecguide.com/download_kl.htm">downloaded</a> and installed the latest 32-bit K-Lite Mega Codec Pack.  It was a big honker -- 25MB -- but my understanding was that, if somebody sent me a file of a Mongolian shepherd beating on a bucket and recording it on a 1960-era IBM tape drive, this would be all I would need to enable Windows to play it in five-channel glory with four-part harmony.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I posted a bug report on this in the IrfanView bug report forum.  See http://en.irfanview-forum.de/vb/showthread.php?6597-IrfanView-Can-t-Play-This-File&p=30624#post30624


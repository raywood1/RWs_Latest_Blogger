---
layout: post
title: "Plugins Needed in Ubuntu 9.10"
date: 2010-01-25
---

<div class="post-body">
<p>I was trying to play a .wav file in 64-bit Ubuntu 9.10 (Karmic Koala).  (This was a compressed .wav in 4-bit 22 kHz IMA ADPCM format.)  I double-clicked on it in Nautilus.  Movie Player opened up and gave me this message:<br/>
<br/>
<blockquote>Search for suitable plugin?<br/>
<br/>
The required software to play this file is not installed.  You need to install suitable plugins to play media files.  Do you want to search for a plugin that supports the selected file?<br/>
<br/>
The search will also include software which is not officially supported.<br/>
</blockquote><br/>
I went with that.  Unfortunately, the next message said this:<br/>
<br/>
<blockquote>No packages with the requested plugins found.<br/>
<br/>
The requested plugins are:<br/>
<br/>
image/vnd.microsoft.icon decoder<br/>
</blockquote><br/>
I clicked OK.  That gave me another message:<br/>
<br/>
<blockquote>An error occurred<br/>
<br/>
The playback of this movie requires a image/vnd.microsoft.icon decoder plugin which is not installed.<br/>
</blockquote><br/>
A search for relevant terms led to <a href="https://web.archive.org/web/20190906053801/http://ubuntuforums.org/showthread.php?t=1172736">a thread</a> in which someone asked whether the user had "the w32codecs" installed.  I didn't see that package in Synaptic.  But then someone else in that thread said maybe I wouldn't need it for my 64-bit Ubuntu.  One person pointed toward an <a href="https://web.archive.org/web/20190906053801/http://ubuntuforums.org/showthread.php?t=766683">extended tutorial</a> in setting up multimedia in Ubuntu.  There was <a href="https://web.archive.org/web/20190906053801/http://ubuntuforums.org/showthread.php?t=1172736&amp;page=2">some discussion</a> on whether 32-bit codecs (e.g., w32codecs) were necessary in a 64-bit system; the consensus (supported, of course, by the actual error message on my system) was that they might well be.  The same opinion emerged in <a href="https://web.archive.org/web/20190906053801/http://ubuntuforums.org/showthread.php?t=1034752">another discussion</a>.  The way to get those 32-bit codecs seemed to be, first, to <a href="https://web.archive.org/web/20190906053801/https://help.ubuntu.com/community/Medibuntu">add the Medibuntu repository</a> to my Ubuntu installation.  The simple way to do this was to cut and paste this command into Terminal:<br/>
<blockquote>sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &amp;&amp; sudo apt-get --quiet update &amp;&amp; sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &amp;&amp; sudo apt-get --quiet update<br/>
</blockquote><br/>
all on one line.  For additional multimedia options and capabilities and such, it was also recommended that I enter these commands:<br/>
<br/>
<blockquote>sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu<br/>
</blockquote><br/>
<blockquote>sudo apt-get install libdvdcss2<br/>
</blockquote><blockquote>sudo apt-get install w64codecs <br/>
</blockquote><br/>
So I did that.  This all went smoothly.  I was now able to play other .wav files, but I was not able to play that particular one.  I tried playing it in Windows, using IrfanView, and got these error messages:<br/>
<br/>
<blockquote>[filename]:  Can't read file header !<br/>
<br/>
Unknown file format or file not found !<br/>
<br/>
IrfanView: i_view32.exe - Corrupt File<br/>
<br/>
The file or directory [filename] is corrupt and unreadable.  Please run the Chkdsk utility.<br/>
</blockquote><br/>
So possibly that was why Ubuntu had been unable to play it.  I had checked its properties in Ubuntu, but had not seen any such message.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

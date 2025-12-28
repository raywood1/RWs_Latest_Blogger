---
layout: post
title: "No Video in MPEGs"
date: 2007-08-26
---

<div class="post-body">
<p>I was using Premiere Elements 3.0 on Windows XP.  Working on a short piece of video, I chose File &gt; Export &gt; Movie.  The resulting file, Test.avi, played video and audio in Windows Media Player (WMP).  Next, I chose File &gt; Export &gt; MPEG &gt; NTSC DVD.  The resulting file, Test.mpg, played neither audio nor video in WMP.  But WMP did appear to believe that something was playing, because (a) it said, "Codec acquired," (b) it provided its colorful visualization, and (c) the progress slider moved across the screen until completion.

I tried playing Test.mpg using IrfanView, which normally would play MPGs.  IrfanView, too, could play neither audio nor video.  Unlike WMP, IrfanView's slider did not move; it appeared to consider the file empty.  Windows Explorer reported that the file size was 115MB.

In a previous test, WMP and IrfanView did play the audio portion of the X.MPG output file, but no video; but now there was also no audio.

Using WMP and IrfanView, I played another MPG that was known to work previously.  I got the same results.  This suggested that the problem was not with Premiere, but was rather with something else on this computer.  This was the first time I had tried to create video on this newly built computer.  I suspected there might be an incomplete installation of hardware or software at issue.

In a TechGuy.org forum, <a href="https://web.archive.org/web/20190906053833/http://forums.techguy.org/multimedia/530759-solved-mpeg-video-decoder-codec.html">t bone suggested</a> downloading and installing <a href="https://web.archive.org/web/20190906053833/http://filehippo.com/download_codec_pack/">Codecs6030_allin1.exe </a>(Codec Pack All-In-1 6.0.3.0).  I did that, and it solved the problem with both WMP and IrfanView.

If that hadn't worked, I would have continued with <a href="//web.archive.org/web/20190906053833/https://www.google.com/search?num=50&amp;hl=en&amp;rlz=1B3GGIC_enUS235&amp;q=%22no+video%22+xp+mpg+OR+mpeg&amp;btnG=Search">my Google search</a> and would also have checked these particular solutions <a href="https://web.archive.org/web/20190906053833/http://techrepublic.com.com/5208-6230-0.html?forumID=101&amp;threadID=220721&amp;messageID=2227654">for ATI hardware</a> or if my <a href="https://web.archive.org/web/20190906053833/http://bink.nu/forums/10883/PrintPost.aspx">AVIs had not played</a>.  Also, <a href="https://web.archive.org/web/20190906053833/http://techrepublic.com.com/5208-6230-0.html?forumID=101&amp;threadID=220721&amp;messageID=2245146">newkenbo</a> reported this solution:  "I opened the CCC [ATI Catalyst Control Center, and] went to Video - Video Basics. Video Presets was set to Custom. I just changed it to Home and everything works again. Didn't have to reinstall or anything."  Finally, one person got a solution by downloading and using the <a href="https://web.archive.org/web/20190906053833/http://www.videolan.org/vlc/">VLC Media Player</a>, which (unlike WMP) was available for use on Linux and other platforms.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

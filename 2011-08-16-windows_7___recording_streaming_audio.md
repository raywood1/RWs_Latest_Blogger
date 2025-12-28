---
layout: post
title: "Windows 7:  Recording Streaming Audio"
date: 2011-08-16
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20190906053818/http://raywoodcockslatest.blogspot.com/search?q=%22streaming+audio%22">previously tried</a>, but failed, to get my system to record streaming audio.  The concept, in this mission, was that I wanted to be able to capture, in a file, the sound that I was hearing in my headphones.  Seemed like a simple expectation, and as I recalled it had been almost automatic on my previous system.  But it wasn't happening on my current motherboard, a Gigabyte GA-MA785GM-US2H, so I searched for solutions.<br/>
<br/>
The first requirement seemed to be to use the right software.  Not every audio program is capable of recording streaming video.  The free <a href="https://web.archive.org/web/20190906053818/http://audacity.sourceforge.net/">Audacity</a> program could, so I was using that.  I found <a href="//web.archive.org/web/20190906053818/https://www.youtube.com/watch?v=Kv2kbwoLjqs&amp;feature=player_embedded">a video</a> and <a href="https://web.archive.org/web/20190906053818/http://audacity.sourceforge.net/help/faq?s=recording&amp;i=streaming">a webpage</a> that were supposedly going to help me, and probably I did incorporate some of their suggestions into the approach that eventually worked for me.  The only suggestion that I recall making a difference was that, as recommended, I was using the version 1.3.13 beta of Audacity, not an older one, though at this point I'm not absolutely certain that was necessary either.<br/>
<br/>
Ultimately, I found two ways to record streaming audio.  One was to use a video capture program and convert the resulting file to audio.  I'd had tried a number of video capture programs, with very mixed results.  The only one that seemed to work reliably was <a href="https://web.archive.org/web/20190906053818/http://www.nchsoftware.com/capture/index.html">Debut</a>, and it cost money after its free trial period.  Ultimately, I did buy a copy of that.  For the conversion, I used <a href="https://web.archive.org/web/20190906053818/http://www.oxelon.com/media_converter.html">Oxelon</a>.<br/>
<br/>
The other approach was to use an audio cable to connect the computer's headphone jack directly to its microphone jack.  Basically, I would be recording what the headphones were supposed to be hearing.  Sadly, this didn't work as advertised, when I used the actual jacks on the computer itself.  But I was able to make it work in a different way.  I bought a <a href="//web.archive.org/web/20190906053818/https://www.google.com/search?q=Syba+SD-CM-UAUD&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a">Syba SD-CM-UAUD</a> USB-to-audio adapter.  No software required.  I just plugged it into a USB port, plugged both ends of the patch cable into it, and it worked.  Actually, to make that work, I had to set Audacity as follows:  the audio host was Windows DirectSound; the output device was Primary Sound Driver; the input device was Microphone.<br/>
<br/>
The Syba device gave me really loud volume.  Later, I had to fiddle with Control Panel &gt; Sound to get all my devices back the way they were before.  But so far, it seemed worth it.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

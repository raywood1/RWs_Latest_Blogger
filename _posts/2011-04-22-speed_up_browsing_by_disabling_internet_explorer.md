---
layout: post
title: "Speed Up Browsing by Disabling Internet Explorer"
date: 2011-04-22
---

<div class="post-body">
<p>I had installed Internet Explorer 9.  Now I was getting these completely dumb-assed messages at the bottom of the screen:  "Speed up browsing by disabling add-ons."  The first time, I thought this was a good idea, and I went ahead with that.  When it kept happening, though, I realized I needed to find a way to shut it off.  This post describes how I did that.<br/>
<br/>
<a href="https://web.archive.org/web/20190906051608/http://www.webtlk.com/2010/06/01/how-to-turn-off-internet-explorer-from-asking-you-to-set-it-as-default-browser/">One suggestion</a> that came up in <a href="https://web.archive.org/web/20190906051608/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=ENH&amp;as_qdr=all&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22Speed+up+browsing+by+disabling+add-ons%22+-%22screen+shot+of+notification+bar%22&amp;tbs=search%3Fas_&amp;lr=&amp;as_filetype=&amp;aq=f&amp;aqi=&amp;aql=&amp;oq=">my search</a> was to click Disable Addons, on that reminder, and set the reminder time to as high as possible.  It seemed the best one could do was to choose the "<a href="https://web.archive.org/web/20190906051608/http://www.microsoftblog.co.in/?cat=231">Don't Disable</a>" option to be left alone for 30 days.<br/>
<br/>
But I wanted to eliminate this stupid reminder permanently.  <a href="https://web.archive.org/web/20190906051608/http://angrytechnician.wordpress.com/2011/04/01/how-to-disable-ie9-add-on-performance-notifications-you-idiots/">A different approach</a> involved making a change in Group Policy settings.  I wasn't sure how to do that, or even to see if I had the option in question, so I ran <a href="https://web.archive.org/web/20190906051608/http://www.google.com/search?as_qdr=all&amp;num=50&amp;q=%22Windows+7%22+%22Group+Policy%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a">a search</a> and found <a href="https://web.archive.org/web/20190906051608/http://www.techrepublic.com/blog/10things/10-ways-to-tweak-windows-7-using-the-local-group-policy-editor/1014">a tweaks article</a> that reminded me that I could get into the Local Group Policy Editor via Start &gt; Run &gt; gpedit.msc.<br/>
<br/>
In the policy editor, I didn't see exactly the option described.  The message said to start with the Windows Components area, but there were at least two of those:  one under Computer Configuration &gt; Administrative Templates, and one under User Configuration &gt; Administrative Templates.  I did find Internet Explorer subheadings in both, but neither had a "Disable add-on performance notifications" option.  The advisor told me that I might need to copy updated inetres.admx and inetres.adml files from a machine with IE9 installed, but this machine had IE9 installed already, so that did not seem to apply.<br/>
<br/>
That pretty much exhausted my focused search.  At this time, then, there was no good solution to this problem.  I hoped that the Don't Disable option did indeed give me 30 days of peace.  At the end of that time, it was possible but doubtful (since I rarely used IE, and had just discovered one more reason for that) that I would actually appreciate the reminder.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Mrs Crolla**:
This nag annoys me unutterably. i've repeated reset the times I want to allow for my addons to start up. It still comes back. I'm using IE9 less and less...

**Anonymous**:
Here's some more information that might be helpful,IE9 - Stop "Speed up browsing by disabling add-ons"PetePeteNetLive

**Anonymous**:
My current understanding is that one simply cannot turn off "speed up browsing by disabling add-ons". This message is by far the silliest message and/or message-position I've ever come across. How on earth did it pass testing? A non-critical message that appears every single time the browser opens, without any obvious way to control the behaviour!

**Anonymous**:
This is silly. Every user needs to balance the time they spend optimizing versus actually getting stuff done. Your tools shouldn't be forcing you one way or the other.

**Samy**:
Following tutorial from a Microsoft MVP provides detailed instructions to disable this annoying popup notification message:http://www.askvg.com/how-to-disable-speed-up-browsing-by-disabling-add-ons-popup-notification-message-in-internet-explorer/It also contains a Registry Editor method for Windows editions which don't come with Group Policy Editor.

**raywood**:
I have looked at the links provided byPeteNetLiveand bySamy.  Thanks to both for providing potential solutions.Among the several solutions provided by the latter, the easiest seems to be to justdownloadand run a REG file.  I've given that a try.  I'm not sure yet whether it works.  If I remain silent, it probably means I'm happy.


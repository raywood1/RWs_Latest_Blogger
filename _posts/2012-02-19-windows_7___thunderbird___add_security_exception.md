---
layout: post
title: "Windows 7:  Thunderbird:  Add Security Exception"
date: 2012-02-19
---

<div class="post-body">
<p>I was using Mozilla Thunderbird 10.0 for email.  I suddenly got this message:<br/>
<blockquote>Add Security Exception<br/>
<br/>
You are about to override how Thunderbird identifies this site.<br/>
<br/>
Legitimate banks, stores, and other public sites will not ask you to do this.<br/>
<br/>
Server Location:  imap.exchange.iu.edu:993<br/>
<br/>
Certificate Status<br/>
<br/>
This site attempts to identify itself with invalid information.<br/>
<br/>
Wrong Site<br/>
<br/>
Certificate belongs to a different site, which could indicate an identity theft.</blockquote>Below that, there was an option to "Permanently store this exception" and buttons to Confirm Security Exception or else Cancel.  Canceling didn't achieve anything:  the same dialog came right back.  I was afraid to click anything else.  The site in question was linked to Indiana University, which seemed legit.  I had gotten something like this <a href="https://web.archive.org/web/20151205115542/http://forums.mozillazine.org/viewtopic.php?f=39&amp;t=2239733" target="_blank">before</a>, using an earlier version of Thunderbird, but there the problematic email account had been Hotmail.<br/>
<br/>
I wasn't sure why I was getting this.  <a href="https://web.archive.org/web/20151205115542/https://support.mozillamessaging.com/en-US/kb/Add-Security-Exception" target="_blank">A Mozilla page</a> said, "The problem usually arises when the mail server's certificate is invalid for some reason. . . . Often this problem takes care of itself, in that the mail server provider will realize that they have made an error with their certificate and will replace it with a corrected version."  I had started getting this program maybe a year earlier.  I didn't know if this meant that I was the only person at Indiana University using Thunderbird, or what the explanation might have been.<br/>
<br/>
I didn't find anything on point in <a href="https://web.archive.org/web/20151205115542/http://kb.iu.edu/index.cgi?searchOptionBtn=KB&amp;search=%22Add+Security+Exception%22+Thunderbird&amp;Search=Search&amp;maxdocs=15" target="_blank">Indiana's knowledgebase</a>.  <a href="https://web.archive.org/web/20151205115542/https://www.google.com/search?q=Thunderbird+%22Add+Security+Exception%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">A search</a> led to <a href="https://web.archive.org/web/20151205115542/https://getsatisfaction.com/mozilla_messaging/topics/how_do_i_resolve_a_add_security_exception" target="_blank">advice</a> to make a change in Server Settings.  To get there, I had to click Cancel with the "Permanently store this exception" box checked; otherwise the dialog wouldn't budge.  Even so, I had to click Cancel a bunch of times to get out of there.  I went into Thunderbird &gt; Tools &gt; Account Settings.  I went to the Server Settings heading under the listing for the Indiana University account on the left side.  The advice seemed to be that, in that area, I should go to the Security Settings area and set Connection Security to None, instead of its present setting of "SSL/TLS."  Doing that changed the Authentication Method from "Normal password" to "Password, transmitted insecurely."<br/>
<br/>
I wasn't sure about that.  I looked further down that same thread.  Someone else seemed to be saying that the address should be imap.exchange.iu.edu.:993, with a period before the colon.  Staying in the Account Settings dialog, and looking specifically at the list of options on the left side, I moved from the Server Settings option down to "Security," the last option for the Indiana University email account.  There, I went into Certificates &gt; View Certificates &gt; Servers tab.  I saw that I had certificates here for Mozilla, Google, Yahoo, etc.  It seemed like a legitimate list.  I decided to go with the advice, which was to go into Add Exception and type <a href="https://web.archive.org/web/20151205115542/https://imap.exchange.iu.edu.:993/">https://imap.exchange.iu.edu.:993</a>.<br/>
<br/>
Before I finished that, I took another look at the Mozilla page.  They said that the mail server provider (i.e., IU) should provide the necessary connection information.  They said that the Add Security Exception option that I was just about to finish would make my email through that account nonencrypted and visible to third parties.  Writers in <a href="https://web.archive.org/web/20151205115542/http://forums.mozillazine.org/viewtopic.php?f=39&amp;t=2013413" target="_blank">another recent thread</a> indicated that they, too, were having this problem.  The list of certificates (for e.g., Google, Yahoo) seemed to indicate that they had done what was necessary to provide email security at some level, but Indiana University had not.  I tried <a href="https://web.archive.org/web/20151205115542/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=Mrp&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Thunderbird+%22You+have+certificates+on+file+that+identify+these+servers%22&amp;oq=Thunderbird+%22You+have+certificates+on+file+that+identify+these+servers%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=3540310l3548190l0l3549399l59l18l0l0l0l7l549l3033l9.1.6.1.0.1l18l0" target="_blank">another search,</a> but it led to surprisingly few hits, among which the main relevant reaction was <a href="https://web.archive.org/web/20151205115542/http://forums.mozillazine.org/viewtopic.php?f=38&amp;t=2340071" target="_blank">puzzlement</a>.<br/>
<br/>
The Mozilla page seemed to be saying that you have three options in this kind of case.  You can ask the mail server people to get it together.  You can add a security exception -- or, as it appeared in my case at least, you would have to add a security exception if you wanted the program to be usable.  Or you could switch to a different account.  I wasn't sure whether switching to a different email program would provide another possible solution.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

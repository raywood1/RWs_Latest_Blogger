---
layout: post
title: "Blocking Unwanted Websites from Google Searches"
date: 2012-05-07
---

<div class="post-body">
<p><a href="https://web.archive.org/web/20151205114044/http://raywoodcockslatest.blogspot.com/2011/03/google-search-freeware-get-rid-of.html" target="_blank">I had been using</a> the <a href="https://web.archive.org/web/20151205114044/https://addons.mozilla.org/en-US/firefox/addon/optimizegoogle/?src=search" target="_blank">Optimize Google</a> add-on in Firefox, and the <a href="https://web.archive.org/web/20151205114044/https://chrome.google.com/webstore/search/search%20engine%20blacklist" target="_blank">Search Engine Blacklist</a> extension in Chrome, to keep unwanted websites from clogging up my searches.  I especially like the approach of Optimize Google:  it would still show the sites that I was blocking, but they would be greyed-out.  This made it easier to keep an eye on what I was blocking.  I didn't want to be accidentally preventing myself from seeing good sites.<br/>
<br/>
Unfortunately -- in Firefox 8 and 10, as distinct from Firefox 3 -- OptimizeGoogle was messing up my Google search tools.  I noticed it particularly in my ability to select a date range for a search.  Meanwhile, in Chrome, I eventually found that Google offered an option to <a href="https://web.archive.org/web/20151205114044/https://www.google.com/reviews/t?hl=en" target="_blank">Manage Blocked Sites</a> -- but in that option, as in Search Engine Blacklist, I had to enter each website manually, rather than just pasting in a list from a file, as Optimize Google would let me do.  Even if these extensions had worked perfectly and easily, they still didn't help with other browsers (e.g., Internet Explorer, Opera).<br/>
<br/>
I found <a href="https://web.archive.org/web/20151205114044/http://comptrick.com/?p=434" target="_blank">a Computrick webpage</a> that told me I could block out websites for all browsers in one move.  The recommended approach was to open the Hosts file in C:\Windows\System32\drivers\etc. (<a href="https://web.archive.org/web/20151205114044/http://allthingsmarked.com/2006/08/28/howto-block-websites-using-the-hosts-file/" target="_blank">elsewhere</a> in earlier versions of Windows).  (It would apparently take administrator privileges to modify that file.)  The modification was to add lines like this to the end of that Hosts file:<br/>
<blockquote>127.0.0.1 localhost<br/>
127.0.0.1 www.badsite.com<br/>
127.0.0.1 badsite.com</blockquote>In other words, each line would begin with "127.0.0.1" followed by at least one space, and then the brief URL of the unwanted website.  As that example shows, I was supposed to enter the site's URL both with and without the "www" prefix.  The first line, 127.0.0.1, was apparently required to make the process work.  It was already there in Hosts, but it was commented out (i.e., its line was prefixed with a # symbol, making it nonoperational).  So I removed the # symbol before that line to make it work, and likewise for the next line, the last one that was already there when I first opened Hosts:  ::1.<br/>
<br/>
I still had the list of sites that I tended to paste into Optimize Google's filter list.  I pasted that list into Excel, worked up formulas to produce the two versions suggested above (i.e., with and without the "www"), pasted those into Hosts, and saved it.  As soon as I did that, Microsoft Security Essentials (my antivirus program) popped up a message warning of a potential security threat.  I told it to Allow this instance.<br/>
<br/>
I had decided to look into this website-blocking issue because I had just done a Google search that was plagued by sites I did not want to see.  I suspected that some of them were probably on that long list of unwanted sites that I had developed.  So now I hit F5 to refresh that search.  It didn't look like anything had changed.  I was looking particularly at one website that I knew I didn't want to see in my search results.  I made a point of adding it to Hosts, and I saved Hosts again.  Then I hit F5 to refresh the webpage again.  The unwanted site was still listed.<br/>
<br/>
Further investigation led to <a href="https://web.archive.org/web/20151205114044/http://winhelp2002.mvps.org/hosts.htm" target="_blank">an MVPS.org post</a> that said Hosts was loaded at startup.  So apparently I would have to reboot the system for it to take effect.  This would be another drawback in comparison against a tool like Optimize Google, which could be fine-tuned on the fly to keep removing unwanted sites until my search results would be as pure as the driven snow.  OptimizeGoogle would also let me designate subparts of a website (e.g., www.GoodSite.org/CrappyDownloads).<br/>
<br/>
I was thinking it would be great if someone had cooked up a list of suspicious or unwanted websites.  Presto!  Ask, and it shall be given unto you.  <a href="https://web.archive.org/web/20151205114044/http://someonewhocares.org/hosts/" target="_blank">Someonewhocares</a> posted a truly monumental Hosts file, free for the copying.  I was pretty sure that, if I pasted their Hosts file into mine, I would not be troubled by contacts from anyone anymore.  I was intrigued, but I decided that I would work into this thing more gradually, starting with my modest list of a hundred or so sites that I wanted to block.<br/>
<br/>
While browsing this subject, I came across <a href="https://web.archive.org/web/20151205114044/http://www.google.com/support/forum/p/Chrome/thread?tid=088b5465a6f7f44e&amp;hl=en" target="_blank">a long discussion</a> that looked like it would have been interesting, if I had been interested.  One topic that did have potential had to do with sites like ad.doubleclick.net.  It sounded like my browsing might speed up if sites like that were not bogging down my system.  I went back to the Someonewhocares.org webpage and searched for ad.doubleclick.  They did have a few lines for websites like that.  But their comments indicated that blocking those sorts of ad sites could mess up some retailers' websites (e.g., Sears) and also Google itself.  I decided not to proceed further with that issue at this point.<br/>
<br/>
I saved my newly revised Hosts file.  I also saved a copy of it to another drive, to be protected in case I had to reinstall Windows for some reason.  When I rebooted, I took another look at that most recent Google search.  No effect:  the unwanted sites were still there.  That was in Opera.  I tried the same search in Firefox, Internet Explorer, and Chrome.  Same result:  nothing had been filtered.  I looked again at C:\Windows\System32\drivers\etc\hosts.  It was still there, and it still contained the list of unwanted websites.<br/>
<br/>
That was as far as I got with this project at this point.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
I decided to try the approach of manually entering unwanted sites in Google > Search Settings > Block Unwanted Sites.  I chose this approach based onthe claimthat Google might use our block lists, collectively, to adjust search results.

**Rana Adeel**:
Wow that's great addition for Google service it will help to fight spam. Thanks for sharing

**raywood**:
Another sitehas a Greasemonkey script that, so far, is working well for this.


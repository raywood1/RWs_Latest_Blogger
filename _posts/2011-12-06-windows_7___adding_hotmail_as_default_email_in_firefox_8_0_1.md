---
layout: post
title: "Windows 7:  Adding Hotmail as Default Email in Firefox 8.0.1"
date: 2011-12-06
---

<div class="post-body">
<p>I was using Firefox 8.0.1 in Windows 7.  (Apparently these instructions would also work for Firefox 3.0.)  I was looking at a webpage containing an email address.  I clicked on the email link and got a dialog saying this:<br/>
<br/>
<blockquote>Launch Application<br/>
<br/>
This link needs to be opened with an application.<br/>
Send to:<br/>
Thunderbird<br/>
Yahoo! Mail<br/>
Gmail<br/>
<br/>
Choose an Application</blockquote><br/>
Hotmail was not on the list.  But I wanted to use Hotmail.  To find a solution, I did <a href="https://web.archive.org/web/20151205115826/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Firefox+%22launch+application%22+OR+%22choose+an+application%22+Hotmail+%22Windows+7%22&amp;oq=Firefox+%22launch+application%22+OR+%22choose+an+application%22+Hotmail+%22Windows+7%22&amp;aq=f&amp;aqi=&amp;aql=1&amp;gs_sm=e&amp;gs_upl=73580l75266l0l76304l16l9l0l0l0l4l233l1198l3.4.2l9l0" target="_blank">a search</a> and wound up with <a href="https://web.archive.org/web/20151205115826/http://www.techbuzz.in/how-to-can-i-add-hotmail-livemail-as-default-mail-clients-in-firefox.php" target="_blank">some advice</a> on the process.  I decided to save a writeup of the advice here because it took me a while to find it.<br/>
<br/>
The advice was to type "about:config" in the Firefox address bar, hit Enter, type "gecko" into the Filter box, and double-click on the first item on the list.  This was the item called "gecko.handlerService.allowRegisterFromDifferentHost."  Double-clicking on it put it into boldface and changed its value from false to true.  Then I closed the about:config tab.  I went back to the address bar and typed this command, all on a single line:<br/>
<br/>
Javascript:window.navigator.registerProtocolHandler("mailto","<a href='https://web.archive.org/web/20151205115826/http://hotmail.msn.com/secure/start?action=compose&amp;to=%s","Hotmail'>http://hotmail.msn.com/secure/start?action=compose&amp;to=%s","Hotmail</a>")<br/>
<br/>
and then I hit Enter.  This gave me a bar at the top with the question, "Add Hotmail (hotmail.msn.com) as an application for mailto links?"  I clicked on "Add Application."  That gave me a blank screen.  I went to Tools &gt; Options &gt; Applications.  There were a bunch of items listed there.  I went down the Content Type column until I found "mailto."  I selected it.  This gave me a drop-down menu on the right side.  I selected the "Use Hotmail" option and clicked OK.<br/>
<br/>
I went back to the webpage where I saw that email link.  I clicked on that link.  This opened up the Hotmail sign-in webpage.  I signed in.  Hotmail immediately started an email addressed to that email address.  I composed and sent an email.  It seemed to go OK.  Problem solved.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
HELP!!! I've tried typing in the required address and all I get is a blank page. There is no pop down menu to select add. I've definitely changed step 3 to true, and after that NOTHING happens. I'm getting so frustrated but want hotmail as my default email.

**raywood**:
You mean you typed about:config into the address bar and it didn't give you a list of items?

**Greg**:
I have the same problem. When copy pasting the javascript and hitting enter, nothing happens

**raywood**:
Greg -- sorry to hear it.  I don't have an answer for you.  It does seem like you're not alone.  If you find a solution, please come back and post a link to it.  Good luck!

**Anonymous**:
open up the "about:config" in firefox again, type in "noscript.allowURLBarJS" (without quotes) and change to this to "true" by double clicking.  Then try again.   Don't forget to go back to the about:config page and change this back after it works.

**Anonymous**:
Firefox 9 doesn't have any noscript configuation at all so that didn't work.

**ICT Tower**:
I've spent ages on this too, no luck either in Firefox 9.0.1.FF 9.0.1 doesn't have the noscript.allowURLBarJS config option, but it does have an option browser.urlbar.filter.javascript , changing this does not have any effect though.I also tried changing this option, network.protocol-handler.external.javascript , to True. I did get a popup telling me that FF didn't know what to do witht the Javascript protocol, but at least I got something to happen!I put it all back afterwards, am hoping someone can fix this soon.Thanks.Mr V

**Anonymous**:
Using Firefox 10. I had the nothing popping up problem, too, so I thought I'd try disabling my NoScript add-on to see if that would help. No such luck. When I tried looking for the noscript.allowURLBarJS that Anon mentioned, I couldn't find it. I re-enabled my NoScript add-on and looked again and I DID find it. Made the change, tried pasting javascript:window.navigator.registerProtocolHandler (etc. etc.) again and it worked just fine!I guess you need to have the NoScript add-on for it to work? Hope this helps!

**Anonymous**:
for those having problems with adding hotmail to your list of options, check this outhttp://www.enigmagroup.org/forums/javascriptajax/javascript-wont-work-in-my-firefox/all the other suggestions here didnt work for me, but that did. I use FF10.0.2no about:config settings need changing as far as i know. just need the ctrl+shift+k

**ICT Tower**:
Brilliant!Just tried the last suggestion by Anonymous and it works!Many thanks, this has bugged me for months, glad I bookmarked the page.:-)

**Anonymous**:
The enigma group link doesn't seem to work.  Here's the solution as it worked for me for FF12.You can no longer run JavaScript code via the location bar.You need the workaround and create a bookmark with the code in the location field.Then you can run (click) that bookmark once to run the code.That should work. You need to paste the full text in the location field starting with javascript: and ending with "Hotmail");The location to use is:javascript:navigator.registerProtocolHandler("mailto","http://mail.live.com/default.aspx?rru=compose&to=%s","Hotmail");Or as an alternative:javascript:navigator.registerProtocolHandler('mailto','http://mail.live.com/secure/start?action=compose&to=%s','Live Mail');

**Anonymous**:
Huge thanks to Franpa on sevenforums.com for the following info which also works for Waterfox X64There are some additional steps you must take in recent versions of Firefox, took me a while to discover them (Found out by posting on the Firefox/Mozilla forum). Check below for the additional steps you must take.1) Type about:config into your location bar and hit enter. If you've never edited used about:config before, you'll see a warning.2) Click "I'll be careful, I promise!" This will bring you to the about:config window.3) In the filter field type "gecko". Double click the first entry gecko.handlerService.allowRegisterFromDifferentHost to change the value to true.4) Create a bookmark for any website.5a) Edit the bookmark you just created and change the Location to javascript:navigator.registerProtocolHandler('mailto','http://hotmail.msn.com/secure/start?action=compose&to=%s','Hotmail');5b) For people who have configured there Hotmail to use HTTPS, type the following instead.javascript:navigator.registerProtocolHandler('mailto','https://hotmail.msn.com/secure/start?action=compose&to=%s','Hotmail https');6) Click the Bookmark you just edited.7) You will see an information bar drop down at the top of the window. Click "Add Application." You've finished installing the Hotmail protocol now you just need to select it.8) Go to Firefox>Preferences>Applications, if you are using a Mac, or Tools>Options>Applications, if you are using Windows. Now scroll down the list by content type and find mailto. In the drop-down menu to the right select "Use Hotmail" or "Use Hotmail https" (Whichever is appropriate).9) Next, return to about:config.10) If the warning comes up again, click "I'll be careful, I promise!"11) In the filter field type "gecko", and double click the first entry gecko.handlerService.allowRegisterFromDifferentHost to change the value back to false.hope this helpsThe reason for this is because they disabled executing Javascript from the location bar, hence the need for using a bookmark instead.

**raywood**:
I tried several of the foregoing options and got the best results witha searchfor Firefox mailto addons.  The one I chose wasLive Mailer.  I've tried it with just one email link on a webpage, and it worked fine for that.


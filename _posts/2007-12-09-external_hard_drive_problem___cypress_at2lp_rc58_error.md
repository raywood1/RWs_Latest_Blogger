---
layout: post
title: "External Hard Drive Problem:  Cypress AT2LP RC58 Error"
date: 2007-12-09
---

<div class="post-body">
<p>I bought an Apricorn EZ-Bus-DT (sometimes called an EZ Bus DT, without the hyphens) external hard drive enclosure <a href="https://web.archive.org/web/20160128055952/http://www.newegg.com/Product/Product.aspx?Item=N82E16817155601">from Newegg</a>.  I really liked it, and I got it with a big rebate, though now I see I could also have bought a discounted, refurbished one directly <a href="https://web.archive.org/web/20160128055952/http://apricorn.com/product_detail.php?type=reg&amp;id=1198">from the manufacturer</a>, whose <a href="https://web.archive.org/web/20160128055952/http://apricorn.com/products.php?cat_id=55">current products webpage</a> led me to understand that this newly purchased product was no longer state-of-the-art.

One day, the system stopped recognizing this external drive.  Instead, I was getting a Found New Hardware dialog.  It wanted me to insert my disk or install the drivers for a Cypress AT2LP RC58.  I didn't know what that was, so I went online to research it.  Sources there said that this meant the system was no longer recognizing my external hard drive enclosure, which apparently <a href="https://web.archive.org/web/20160128055952/http://uk.answers.yahoo.com/question/index?qid=20061214152841AAFe7k0">uses Cypress hardware</a>.  I verified that the problem was not just with my computer, by connecting the external drive to another computer, where I got the same message.

The drive itself was fine, <a href="https://web.archive.org/web/20160128055952/http://forums.techguy.org/hardware/476679-external-hd-problem-cypress-at2lp.html">they said</a>, but I would have to install it directly inside my computer as a slave if I wanted to access its data.  I was hoping that the Apricorn would actually resume working, though, so I forged ahead in the search for alternatives.  I found no FAQs at all on <a href="https://web.archive.org/web/20160128055952/http://apricorn.com/support5.php">the Apricon support webpage</a>, and <a href="https://web.archive.org/web/20160128055952/http://apricorn.com/ezbusdt_drivers.php">they said</a> no drivers were necessary for Windows XP.  The product manual itself did not address any troubleshooting problems.  I dropped them an e-mail and continued my search.

A Google search turned up several hundred hits, from all over the world, so it seemed that this problem affected a number of users.

I found no downloads for the AT2LP RC58 on the <a href="https://web.archive.org/web/20160128055952/http://www.cypress.com/portal/server.pt?space=CommunityPage&amp;control=SetCommunity&amp;CommunityID=285&amp;PageID=0&amp;type=900&amp;CID=ILC-shortlinks&amp;shk=search">Cypress downloads page</a>.  For some reason, Cypress required me to register and log in before searching its webpage for a solution, so there would be no point providing links, here, to the various webpages I searched.  (They kept requiring me to log in again and again when I checked those pages.)  Suffice it to say that I found no answers in their Communities (which did not appear to be user forums in the usual sense), and eventually figured out that this was different from their Discussion Forums.  I think I found the latter by using their Contact Us link and selecting Technical Support.  (When I tried the link for actual technical support, a/k/a contact with a human, I got "Sorry, an error has occurred and has prevented your request from being processed."  A search of their KnowledgeBase took me back to their homepage.  In a general search for AT2LP across their webpage, I found a document called <a href="https://web.archive.org/web/20160128055952/http://download.cypress.com.edgesuite.net/design_resources/application_notes/contents/at2lp_revision__c_reset_issue_and_workaround___an14569_12.pdf">AN14569.pdf</a> that alerted me to the existence of some software known as the Cypress Configuration Utility, which looked like it might enable the technically very knowledgeable user to reconfigure the programmable chip that was apparently responsible for the existence and possible resolution of this problem.  I also found a link to a mass storage driver for various versions of Windows (including WinXP), but it dated from 2003, so I had to assume it was already incorporated in whatever I had done when I first received and installed the unit and found it to be working.

I found a simplistic solution on <a href="https://web.archive.org/web/20160128055952/http://www.mvixusa.com/support/index.php?_m=knowledgebase&amp;_a=viewarticle&amp;kbarticleid=74">the MVIXUSA.com webpage</a>, but <a href="https://web.archive.org/web/20160128055952/http://mvixcommunity.com/showtopic.php?tid/285/">someone said</a> that this did not resolve the problem for them.  The MVIX solution appeared to be a shorthand version of a much longer and many-dimensioned <a href="https://web.archive.org/web/20160128055952/http://daltrey.org/linux/cypress.html">investigation of the problem</a> by Barrington Daltrey.  His page offered a number of different possible solutions and perspectives on the issue.  Someone posting in the Cypress forums (which I did ultimately find) offered this shorter summary of what was apparently Daltrey's most pithy suggestion, as follows:

<span style=";font-family:arial;font-size:85%;">Downloading the files
---------------------

1.  Download this file: http://daltrey.org/linux/DBFlash.exe.  Save it to your desktop.
2. Double click the file. It will prompt you to choose a location to unzip it to. Doesn't matter where you put it - unzipping it to the Desktop is easiest.
3.  Click "Unzip"
4.  Go to your desktop and check that you have a new folder, called "PH-1003 EE SW".  If so, you're good to move on.

Installing the new driver
-------------------------

1.  Click Start -&gt; Control Panel
2. Double click "System". If you can't find an entry labeled "System", click "Switch to classic view" on the left hand side of the window, then check again.
3.  Click the "Hardware" tab
4.  Click "Device Manager".  This will open the device manager, and let you view all your devices.
5. Find the Cypress entry. It should be pretty obvious. You might need to expand the "Universal Serial Bus controllers" section to find it. Most likely it will have a yellow question mark next to it. Once you find it, right click on it and select "Update driver...".
6.  Select "No, not this time" and click "Next"
7.  Select "Install from a list or specific location (Advanced)" and click "Next"
8.  Select "Don't search.  I will choose the driver to install." and click "Next"
9. If a big list of different types of devices appears, click "All devices" and click "Next". If you don't see this list, don't worry.
10.  Click "Have Disk..."
11.  Click "Browse..."
12.  Browse to your desktop.  Enter the "PH-1003 EE SW" folder.  Enter the "Driver" folder.  Select "CyUSB.inf" and click "Open"
13.  Click "OK"
14.  Click "Next"
15.  Windows will now install the new driver.  Once it's done, click "OK" or "Done" or whatever it says.
16.  The question mark next to the Cypress device should now be gone.  It's name might change too.
17.  Reboot your computer.

Resetting your hard drive's firmware
------------------------------------

1.  Back at your desktop, open up the "PH-1003 EE SW" folder.
2.  Double click on "Primer.exe"
3. Wait... it should display some messages about plugging in your hard drive, then it should find the hard drive quickly and do some stuff before saying "Successful".
4.  Shut down your computer
5.  Unplug and turn off the hard drive.
6.  Wait a moment...
7.  Plug the hard drive back in and turn it on.
8.  Turn the computer back on.
9.  With any luck, once it boots it will show up as a hard drive again!
</span>
I decided to wait for a response from Apricorn before undertaking all that.  I also pondered the possibility of returning the unit to Newegg as defective.  It wasn't entirely clear to me, from either Daltrey's long page (which I did not read word-for-word) or this summary, whether this would be a one-time fix, a reprogramming of the hardware, or whether this was instead a driver issue that might need to be repeated from time to time.

A few days later, I did get a reply from Apricorn.  Here's what they said:

<pre><blockquote>Yes, it sounds like there is a problem with the USB controller chip. That is
the default prom chip information. Please call support and have them set up
a replacement for you. If this is not possible, you can send me your
shipping and contact information and I can set it up for your, but it will
be quicker if you can call in.
</blockquote></pre>So I was pleased that I got tech support on it; pleased at the prospect of having a model that did not suffer from the problem ... and uncertain as to whether I wanted to keep the unit.  I had meanwhile considered that maybe I should have bought a model that would handle SATA as well as IDE drives, since SATA was the wave of the future I already had one SATA drive that I thought I might be wanting to convert to external usage at some point.  Preliminarily, though, it looked like those enclosures were more expensive, and anyway I didn't really need one right now.  So I went ahead with Apricorn's RMA option.  On that point, they were very cooperative.  They took my credit card information and sent me a replacement unit, and they allowed extra time for my return under the RMA.

The replacement enclosure worked without problems.  One possibility is that I was more careful in never powering it down or switching it to the other computer when it was working.  Basically, this meant that I always had to shut down the computer before switching, because the system tray icon for "Safely Remove Hardware" would always give me a message indicating that the hard drive can't be safely removed right now.

My only other note on this item is that, as of this writing, it appeared Apricorn was going to screw me out of my rebate.  I was really surprised.  They had seemed like a class act.  Maybe I can get them to get with the program on that.  Not sure.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**ghost**:
see this thing herehttp://shigekuni.blogspot.com/2007/12/cypress-at2lp-rc58-problem.html

**Anonymous**:
here a suggestion that worked for me. try a different usb cable! the one that comes with the external drive is cheap crap. here is a related blog post i just found. http://mvixcommunity.com/showtopic.php?tid/285/

**Anonymous**:
Thanks man, great post. Will check it out, but sounds like thats exactly what I needed. Cheers,-Max

**Anonymous**:
I have a Seagate 100GB external usb drive and I mostly use Windows XP. Recently I wanted to unplug the drive and Windows refused permission several times. In frustration I just unplugged it anyway. I didn't want to reboot to clear the problem. The next time I plugged it in I got the Cypress driver error. I can't remember for certain now but it was the less popular version, RC58 I think. I then started searching the internet for explanations and solutions and found several pages like yours. It looked like I was in for a lot of work. My PC is configured to dual boot Windows XP and Ubuntu 7.10 so I thought I might as well see what linux would make of the faulty drive and rebooted into Ubuntu. Ubuntu mounted the drive perfectly without comment and when I tried it again so did Windows. Maybe I was just lucky or maybe Ubuntu fixed it, but I think it's worth passing on the idea in case it helps other users. I would expect any recent linux live CD would be appropriate.

**WebSmurf**:
http://www.mvixusa.com/support/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=74This solved my problemWebsmurf

**Nikolay Duylovskiy**:
This was solve the problem:http://www.mvixusa.com/support/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=74Just make all StepByStep and this will make you happy =)))

**Anonymous**:
August 2008. After 2 days surfing the web, this solution worked for me with a LACIE MOBILE HD. and WINDOWS VISTA. Thank you, thank you, thank you.

**Anonymous**:
Thanks you once more- I changed my external box two weeks ago and I think that I had lost all the information again

**Anonymous**:
Thanks for the help!

**sbeser**:
Thanks a lot... works like a charm with VISTA and LACIE MOBILE DRIVE. You saved me hours of frustration.

**PAH**:
I had this same problem on 2 PCs following an automated windows update. In my case both PC's "lost" their external drive and the device manager showed that the Cyprus AT2LP was now shown in its place. Since I use Windows XP Pro I merely rolled back the driver and the USB drive reappeared as normal. This solution took no more than 1 minute to solve so if this works for you it saves a lot of bother!

**Co3**:
Thanks for posting this topic. Websmurf's solution worked for me 100%. I was able to get my drive up and running again in less then 15 min. I'm one happy camper again. Once again, thank you for taking the time in sharing this with us Ray.

**Co3**:
Thanks for posting this topic. Websmurf's solution worked for me 100%. I was able to get my drive up and running again in less then 15 min. I'm one happy camper again. Once again, thank you for taking the time in sharing this with us Ray.

**Anonymous**:
This *totally worked*, thank you so much.  I didn't want to crack the case on my PC and install this drive internally, and this worked like a charm on my 32 bit system.  Thanks!~Stacy

**Marcus Loh**:
It worked! Thanks!

**Anonymous**:
Thank you so much for the time and research you put into this! I HAVE MY HARD DRIVE BACK!!!! yEAI will be shopping for a body to install the card in though as I will always be nervous about it now.KevinWhitehorse, Yukon, Canada

**Neil**:
Outstanding Ray! I can't thank you enough. I've had this problem with a Toshiba/Western Digital driver for 4 months with Tosh support being as much use as a chocolate teapot. I see your first post was in 2007 and still no fix or admission of error from the manufacturers?! I'm very grateful for your simple, idiotproof fix. Many thanks and I owe you a pint or three when you're in London. Neil

**Anonymous**:
Websmurf's post worked for me, too. Less than ten minutes (not counting the two hours I spent looking for answers in the first place!)Can't thank you enough.


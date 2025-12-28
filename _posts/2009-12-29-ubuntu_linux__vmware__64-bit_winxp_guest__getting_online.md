---
layout: post
title: "Ubuntu Linux, VMware, 64-bit WinXP Guest: Getting Online"
date: 2009-12-29
---

<div class="post-body">
<p>I was using Ubuntu 9.04 (Jaunty Jackalope).  On Ubuntu, I was running VMware Workstation 6.5.2.  In VMware, I had just installed 64-bit Windows XP.  I was now trying to get online.<br/>
<br/>
At first, I thought the problem was with my Linksys WRT54GL Wireless-G 2.4GHz 54Mbps broadband router.  I inserted the Linksys setup CD and ran through its setup steps.  It said, "Checking your computer settings, Please wait."  After a minute or so, it gave me an error message:  "Setup Wizard MFC Application has encountered a problem and needs to close."  It did this repeatedly.  But when I connected the computer directly to my DSL modem, bypassing the router, I still couldn't go online.  Anyway, a post I saw somewhere said that the Linksys setup CD was to set up the router, not the computer.  The router had already been set up from a previous installation, so that didn't seem to be the issue.  I was able to access the Internet in Firefox in the underlying Ubuntu layer, so the problem was just with getting Windows connected from within the virtual machine (VM).<br/>
<br/>
In VMware, I went to VM &gt; Settings &gt; Network.  I saw that it was set to Bridged.  I believed it was supposed to be NAT, not Bridged, so I changed it.  I did the same thing with Network Adapter 2.  I saved that and tried again to go to a webpage in Internet Explorer, but once again got "The page cannot be displayed."  I connected the computer directly to the DSL modem again.  This didn't seem to make any difference, but I left it that way for the moment, just in case I had more than one problem.<br/>
<br/>
It occurred to me that maybe I was supposed to restart VMware in order for the changes to take effect, so I suspended the WinXP VM, closed VMware, and restarted it.  Just to test it, I started a different VM and tried to go online.  Internet Explorer worked with no problems in that machine, but still wouldn't work in the new 64-bit WinXP VM.  I dug out my AT&amp;T Yahoo SBC installation CD -- I had forgotten that I had such a thing, but I got reminded of it when I ran Start &gt; Settings &gt; Network Connections &gt; New Connection Wizard &gt; Next &gt; Connect to the Internet.  All the hardware was already plugged in, so I moved pretty quickly to AT&amp;T's Software Installation dialog.  When I clicked there, I got a message, "You need to install an Ethernet adapter in your computer."  So the problem seemed to be that Windows was not recognizing the VMware virtual network connector.<br/>
<br/>
Looking again at the VM settings, I noticed that the working VM only had one Network Adapter.  There was no Network Adapter 2 there.  The <a href="https://web.archive.org/web/20190906053732/http://communities.vmware.com/docs/DOC-1490">VMware FAQs</a> said there could be problems if you had two network interface cards (NICs), so I deleted Network Adapter 2.  This didn't help with the AT&amp;T installation; I was still getting the message that I needed to install an Ethernet adapter.   A <a href="//web.archive.org/web/20190906053732/https://www.google.com/search?q=%22at%26T%22+%22you+need+to+install+an+ethernet+adapter%22+vmware+ubuntu&amp;sourceid=navclient-ff&amp;ie=UTF-8&amp;rlz=1B3GGGL_enUS291US291">Google search</a> for that message didn't turn up anything.<br/>
<br/>
I went to Start &gt; Settings &gt; Control Panel &gt; System &gt; Hardware &gt; Device Manager, as I should have done at the beginning.  There, I saw a yellow question mark and a yellow circle with a black exclamation mark next to "Ethernet Controller."  I right-clicked on it and said, Update driver.  The Hardware Update Wizard couldn't find a driver.  <a href="https://web.archive.org/web/20190906053732/http://communities.vmware.com/thread/182243">Someone said</a> they had resolved this problem by installing a new WinXP x64 VM using the 64-bit rather than the default 32-bit WinXP setup.  I powered down the VM and checked in VMware's "Edit virtual machine settings" option for that VM.  It showed that, under Options &gt; Guest Operating System, I had already indicated that the guest was Microsoft Windows, Windows XP Professional x64 Edition.  This didn't seem like it was the problem in my case, so I <a href="https://web.archive.org/web/20190906053732/http://communities.vmware.com/thread/212639">posted a question</a> on it.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**leo[dot]krajewski[at]gmail[dot]com**:
I had a similar problem porting an XP 64-bit image to a VM.  Ended up editting the vmx file to change the virtual NIC.  Made the change; came right up.  Here's the link w/ the details:  http://communities.vmware.com/thread/194536


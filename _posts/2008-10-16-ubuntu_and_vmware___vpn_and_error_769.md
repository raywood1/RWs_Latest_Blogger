---
layout: post
title: "Ubuntu and VMware:  VPN and Error 769"
date: 2008-10-16
---

<div class="post-body">
<p>I was running VMware Workstation 6.0 on Ubuntu Hardy Heron 8.04.  Within VMware, I was running a Windows XP virtual machine.  I sometimes needed to make a VPN connection within the WinXP VM.  To make that connection, I would first have to shut down ZoneAlarm.  I had no other antivirus or firewall software running within the VM.

I upgraded to Workstation 6.5.  I did not make any other changes to the Ubuntu base layer, which continued to run the Firestarter firewall.  Firestarter had not interfered with VPN previously, and I did not think it was inclined to start doing so now.  On the Windows XP virtual machine level, I installed the latest VMware Tools in the VM.

Once this was done, I was no longer able to connect using VPN inside the WinXP VM.  When I tried to do so, I immediately got this:<blockquote>Error Connecting to VPN

Connecting to [VPN address] ...

Error 769:  The specified destination is not reachable.
</blockquote>There did not appear to be any problem with the router, the network card, or Ubuntu.  I was still able to use Firefox in Ubuntu to browse the Internet, do new Google searches, etc.  Instead, the problem appeared to be between VMware and Ubuntu.  I looked at the VMware settings (VM &gt; Settings &gt; Hardware &gt; Network Adapter).  Nothing had changed; I was still using a NAT network connection.  Setting up a new VPN connection within Windows did not solve the problem.

After fiddling with things for a while, I <a href="https://web.archive.org/web/20140828163206/http://communities.vmware.com/thread/174526">posted a question</a> on this problem.  While I was waiting for an answer, I decided it was time to start transitioning some additional functions from Windows XP to Ubuntu.  In particular, I was using VPN to access e-mail and also to access some article databases at the university.  Since I had been pursuing a long-term project of finding Ubuntu replacements for Windows programs and functions, I thought the logical next step might be to learn how to make VPN work on Ubuntu.

I had <a href="https://web.archive.org/web/20140828163206/http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-and-vmware-multimedia.html">tried this once before</a>, on my secondary computer, without success.  The only thing I had been able to guess, in that previous attempt, was that maybe my router was blocking the VPN connection.  But that seemed unlikely, since I had been using VPN successfully from within Windows on the primary computer all along.  Nonetheless, to test it, I cabled directly from the secondary computer to the DSL modem, left-clicked on the Wired Network Connection icon on my top panel in Ubuntu -- and still got a connection error.  Since VPN had worked within WinXP in a VM on the primary computer, I didn't think it was likely to be a router issue.  I wasn't sure about that, because I had set up VMware Workstation to use an NAT network connection, but this was my starting hypothesis.

In case the primary and secondary computers did differ somehow, at this point I went through the steps required to set up VPN on the primary computer.  In my previous post on this topic, I had written up those steps like this:
<blockquote>I searched in Applications Add/Remove. Well, and wasn't that interesting: I had gotten the impression that Synaptic was more comprehensive and more reliable, but here was VPN Connection Manager, just like the webpage said. I killed Synaptic, checked this one, and clicked Apply. Then I rebooted. The instructions said to look for the Network Manager icon in my system tray, but I didn't have a system tray. Using Ubuntu's System &gt; Administration &gt; Network menu option, I got a Network Settings dialog, but I did not see any VPN Connections option. Nor was there one under Applications &gt; Internet. Using another guide, I found that my mistake was that I was supposed to left-click on the network icon that somehow, at least in my case, had migrated to my top panel; and there, I was to select VPN Connections &gt; Configure VPN &gt; Add. From there, I mostly went with the preferred options.</blockquote>I did it pretty much the same this time.  I did check Synaptic and still didn't find VPN Connection Manager per se.  In Add/Remove, I chose the one with four stars, VPN Connection Manager (PPP generic), rather than the ones with three stars (i.e., OpenVPN and vpnc).  This added a VPN Connections option to my Wired Network Connection icon.  Within the VPN Connections box, I chose Configure VPN &gt; Add, and typed in my gateway.  I didn't know what to do about the other options, so I did nothing with them.  Now the VPN connection I had just added appeared within the VPN Connections box.  But unlike on te secondary computer, this did not add a new VPN entry directly under Wired Network Connection &gt; VPN Connections.  Maybe I needed to reboot to add that.  I had too many things open at that point, though, so I decided to bag it for the time being.

To review, then, the option of avoiding Error 769 -- by using VPN within Ubuntu rather than within a WinXP VM -- was not turning out to be an obvious and easy workaround.  I did want to get VPN working within Ubuntu, but at this point the reasons why I could not do so were no clearer to me than were the reasons why I was suddenly getting Error 769.  It seemed there must be a solution, but what would it be?  People had worked through <a href="https://web.archive.org/web/20140828163206/http://forums.linksys.com/linksys/board/message?board.id=Wireless_Routers&amp;thread.id=183&amp;view=by_date_ascending&amp;page=3">a bazillion different possible fixes</a> and, so far, it sounded like those were very much hit-or-miss (and usually miss).  Experience suggested that this was one of those things that a person could devote an entire day to, and still not have a stable answer.

Rather than go through all those complexities, I decided to try a different temporary solution.  I could do VPN from within my native WinXP dual boot on the secondary computer.  So at this point I bailed out of Ubuntu on the secondary computer and rebooted into Windows.  I set up Microsoft Outlook 2003 there and used that, for the time being, as my VPN mail and research center.  My hope was that perhaps the next version of Ubuntu, due out within about two weeks, would conceivably provide a solution, or that possibly someone would respond to my posted question in the meantime.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**alex smith**:
I've recently got my hands on an Asus Eee PC 901. I got the version which ships with Linux (Xandros heavily modified by Asus) on it since I'm that way inclined. I found that whilst it is possible to use the pre-loaded software to connect to the University's Hotspotvpn, doing so doesn't result in connection that is actually usable.


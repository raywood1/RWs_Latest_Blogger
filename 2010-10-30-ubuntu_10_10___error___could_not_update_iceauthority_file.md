---
layout: post
title: "Ubuntu 10.10:  Error:  Could Not Update ICEauthority File"
date: 2010-10-30
---

<div class="post-body">
<p>When I was booting a new Ubuntu 10.10 installation, I got an error message, "Could not update ICEauthority file /home/ray/.ICEauthority." I clicked through that, checked Update Manager, and rebooted. The ICEauthority error message was there again. <br/>
<br/>
Seeking answers to this problem, I ran <a href="//web.archive.org/web/20190906053657/https://www.google.com/search?hl=en&amp;q=%22could+not+update+iceauthority+file%22&amp;sourceid=navclient-ff&amp;rlz=1B3GGLL_enUS403US403&amp;ie=UTF-8">a search</a> and tried the suggestion to type Ctrl-Alt-F1 to get a text console. There, I hit Enter to get a login prompt. I logged in with my username and password, and this gave me a regular command prompt. I typed "sudo chown -R ray:ray .ICEauthority," where ray was my username. Then I typed "sudo /etc/init.d/gdm restart" to go back into the Gnome GUI. But the ICEauthority error message was still there. (From another post, it appears I could have just entered the chown command in Terminal, without Ctrl-Alt-F1.) People for whom this approach worked seemed to think that the problem was caused by opening a graphical (i.e., not purely text-based) program owned by root using sudo instead of gksudo. If that was relevant, it evidently meant I should have edited fstab by typing "gksudo gedit /etc/fstab." But was gedit a graphical program? Probably the better explanation was that my problem was caused by something else, and that this is why their solution didn't work for me.<br/>
<br/>
Comments in another thread suggested that the problem might have been caused by an update, and also that the chown command (above) wouldn't work on an encrypted home partition. In a variation, I tried this:<br/>
<blockquote>sudo -i<br/>
chown ray:ray /home/ray/.ICEauthority<br/>
chmod 644 /home/ray/.ICEauthority\<br/>
exit</blockquote>But this didn't do it either; the error was back when I rebooted. Somebody else said the problem had to do with changing passwords, and that was possibly relevant for me, so I went into System &gt; Administration &gt; Users and Groups and changed my user password, and also checked the box that said, "Don't ask for password on login."  But Ubuntu hung when I clicked OK; the circle icon (like the Windows hourglass, meaning "I'm working on it") stayed there for a couple of hours.  When I came back to the machine, I killed the dialog box and tried changing the password again, but it hung again.  I ran <a href="//web.archive.org/web/20190906053657/https://www.google.com/search?hl=en&amp;q=ubuntu+%22change+user+password%22+hung+OR+hangs+OR+grayed+OR+greyed&amp;sourceid=navclient-ff&amp;rlz=1B3GGLL_enUS403US403&amp;ie=UTF-8">a search</a> on that subproblem and tried <a href="https://web.archive.org/web/20190906053657/http://start.ubuntuforums.org/showthread.php?t=1535843">the advice</a> to kill that GUI approach and just type "sudo passwd [username]" in Terminal (my username was ray).  That worked.  So, back to the ICEauthority problem.  I rebooted, but no, the password fix was not the solution; the error message was still there.<br/>
<br/>
Another suggestion was to make sure that the entire home directory belonged to the user (me).  That sounded like it might be on the money.  My impression was that moving around and copying this old /home partition could easily have screwed up the permissions.  So now, how to make sure I owned the whole /home directory?  In Nautilus (i.e., Places &gt; Computer), I right-clicked on Home Folder &gt; Properties &gt; Permissions.  It said root (i.e., not ray) was the owner.  In Terminal, I typed "sudo nautilus" and, using the Tree (i.e., not Places) view (top of left panel), went to File System &gt; home &gt; ray &gt; right-click Properties &gt; Permissions and changed the permissions to me with full access.  I clicked on the "Apply Permissions to Enclosed Files" button, closed out of there, and rebooted.  Eureka!  That was the solution.  Done!</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Thanks. It worked!!!

**David A. Del Corral U.**:
Hi!I didn't try any so dramatical as you did;  changing all the permisology to /home; but following your guideI checked who was the owner of my /home/{user} and I found that tit was owned by user "1060=###",then had proceeded to change the owner of this directorysudo chown {user}:{user} /home/{user}and...EVERYTHING IS WORKING PROPERLY!!!Again, thanks a all for your advise and your story, saving me plenty of time of try-fail-try again-fail...!!Note: this failure starte after an update the last wensday!!!

**shawinder**:
I also faces same problem when chowned /var directory so my solution wassudo chown gdm:gdm /var/lib/gdm/ICEauthoriy

**Don**:
Ray!! You are THE man!  Works like a charm now... Like you, I had tried all of the things others had said too, but nothing seemed to work until I found your piece of advice.Thanks for the info.

**Hélio F. F. Félix**:
It worked. Nice post!

**Gonçalo Leite Velho**:
that's it! thanks

**Anonymous**:
Worked great for me... In my system, i think the error was caused by trying to install veetle...

**Anonymous**:
Thank you very very much. this error was killing me, in last months it simply was appearing some day without an easy-explain reason. Some times I fixed it changing the permissions with chmod and other times I was obligated to reinstall the OS. Now I know how fix it finally! Thanks!

**Michael**:
I had moved my usb drive as the number one harddrive boot priority and recived this messege but after i changed it back to the drive everything was on it worked like a charm

**Anonymous**:
@David A. Del Corral U. (and @ray)!Thanks, that did the trick!@Anonymous (January 9, 2011 4:19 PM) I myself think that isntalling Veetle, messed up with the system!

**Anonymous**:
Just wanted to confirm that this worked for me. I had to get rid of that damn "User 1016."Also VEETLE was the problem. I suppose other programs might have the same effect as well ...

**Demian**:
thanks i resolved my problem, damn veetle and user 1016.veetle is the problem see the folder .mozilla permission and the owner is the user 1016

**Cap't Bob**:
Hi Ray, thanks for the information - here's an even simpler way to fix it (try first):In Terminal,sudo chown {user}:{user} ./.ICEauthorityThe problem occurred for me when I installed KDEsniffer and then uninstalled it.  Apparently it has to run under root and for some reason changes the ownership of that file.It was the only file in my home directory that wasn't mine.Fixed the problem, and perhaps the hint of what caused it.Best regards, and thanks for the tip!Bob

**Anonymous**:
David thanks man it actually fix it...my issue came after installed VEETLE player which worked perfect but give me a lot of trouble with the ICEauthority error message...THANKS AGAINvic/Nj

**ole**:
i tried the sudo nautilus way bit it dont allow me to change permissions. so i triedsudo chown {user}:{user} ./.ICEauthoritywhat is user and what is user ?im user ole but if i replace user user with ole it just says illegal user.

**Anonymous**:
THANKS!!!!! That worked!!!! I tried a bunch of things but this solution did the trick for me

**Amilcar Aristides - TIDI**:
Thanks a lot. I was around searching and trying everything else. Very good post. Merci ;)

**Anonymous**:
Thank you so much! It finaly worked!

**Anonymous**:
Brilliant, I had also installed veetle, kept getting the error message and had also lost my sound. Despite the fact I had never even heard of nautilus before it all worked perfectly. Many thanks :-)

**Anonymous**:
I was at a loss on what to do until I found your post.  I checked my home folder and somehow it changed ownership to 1060=####.  Changed it to back to me and all is good now.Tusen Tack!

**VirtualResh**:
ICE Authority File Update Error - Ubuntu LinuxUsing Ubuntu and found the following error when logging in to your user account.Could not update ICE authority file/home/Here is the step by step process on solving this problem,http://virtualresh.blogspot.com/2011/08/ice-authority-file-update-error-ubuntu.html

**Mike Schroeder**:
I had this same problem and tried a few other things and nothing worked.  So, I thought to myself, "Self...I bet if you upgraded from 10.04 to 10.10, it would take care of this little problem!" So I updated it.  And I still had the problem.  Major problem in my book because it also prevented the sound from working.  Never one to admit defeat or accept failure, I did what most of us clueless people do when we can't solve the problem ourselves.  I looked on the Internet! :D  That's when I came across this guide and it was so easy to do.  It fixed my computer in a heartbeat!  Now I'm working on installing Ubuntu 11.04 on a different partition to see whether I like it or not.  Thanks for the blog!!

**Galbinus_Caeli**:
This can also indicated an out of disk space condition.  Apparently my IT department started enforcing quotas this week and this was the symptom that led me to discover this.To test try to 'touch' a file.touch nothing.datIf it succeeds, you are not out of disk space.

**Jesse Munos**:
For me the none of the changing permissions or ownership fixed the issue. None of the solutions I found around the web solved the issue. However, I ran across a comment that someone had made about the system trying to auto log them in and that causing the error to spawn. So what worked for me was to:sudo rm -rf /etc/gdm/custom.conf


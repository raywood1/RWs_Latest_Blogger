---
layout: post
title: "WinXP Loops at Startup:  Loading, Saving, Logging Off -- Forever"
date: 2007-12-01
---

<div class="post-body">
<p>I started Windows XP after restoring a previous <a href="https://web.archive.org/web/20190906053848/http://raywoodcockslatest.blogspot.com/2007/07/drive-imaging-software.html">drive image backup</a> to drive C.  It wouldn't start properly.  It kept looping between messages that it was "Loading your personal settings" and "Logging off" and "Saving your settings."  That happened when I tried to boot WinXP normally, and also when I tried booting into Safe Mode or using Last Known Good Configuration.

Some people seemed to be having this problem in connection with Blazefind, which I gather is some form of spyware.  Of the numerous posts I saw on that problem, <a href="https://web.archive.org/web/20190906053848/http://www.tomshardware.com/forum/19519-45-login-loop">one on Tom's Hardware</a> seemed to provide as good as any an explanation of how to solve the problem.  Another <a href="https://web.archive.org/web/20190906053848/http://www.winxptutor.com/wsaremove.htm">one on WinXPTutor</a> also had information that may help in some cases.

But I didn't have the Blazefind problem.  I did try the registry edit recommended by WinXPTutor, but that, by itself, did not solve the problem.  Since I could not run Regedit from within WinXP, and since <a href="https://web.archive.org/web/20190906053848/http://support.microsoft.com/kb/314058">WinXP's Recovery Console</a> does not have a registry editing tool, I used the free download BartPE, which I loaded from a bootable CD created with the help of <a href="https://web.archive.org/web/20190906053848/http://www.nu2.nu/pebuilder/">the Bart PE website</a>.  In BartPE, I was able to use Go &gt; Run &gt; Regedit.

I did find that the value for Userinit.exe, which I was supposed to be editing in Regedit, was not what people were saying on various webpages.  So after making it read as the WinXPTutor webpage said, I looked at <a href="https://web.archive.org/web/20190906053848/http://support.microsoft.com/default.aspx?scid=kb;EN-US;q249321">a Microsoft troubleshooting webpage</a>.  I was prepared to do it their way, bu then I saw that WinXP had replaced what I had entered in the registry after the previous reboot.  The registry entry was back to what it had been before.  It referred to a nonexistent drive X.  I tinkered around and found that Regedit in BartPE did appear to be saving the thing properly.  So evidently WinXP was revising it back to X on reboot.

The recurring registry entry was pointing to a drive X, which I didn't have.  So I looked at <a href="https://web.archive.org/web/20190906053848/http://support.microsoft.com/kb/223188/">the accompanying Microsoft webpage</a> that had to do with changing the system/boot drive letter.  They pointed me toward HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices which, sure enough, did have a reference to drive X.  But their instructions told me to change it to drive C (after renaming drive C to something else).  That didn't make sense to me, since I did want to retain my other programs' references to drive C.  (Bart PE was also seeing drive C correctly.)  So I tried just deleting the reference to drive X at that registry location.

But that didn't fix the problem on reboot.  Not only did the system still loop as before, but back in Bart PE the registry was still pointing the system to drive X, and the reference to drive X in Mounted Devices was back too.  So this time, I did exactly what Microsoft said, or as nearly as I could under the circumstances of my own system (their example didn't exactly fit my situation), exited Regedit and BartPE, and rebooted -- back into BartPE, to see whether the changes were being saved.  They weren't.  Or at least the Mounted Drives one wasn't; I'm not sure if I checked the other one at this point.  It seemed that BartPE wasn't able to save registry changes.

I wasn't sure if the problem was just BartPE.  So I exported those registry changes, from within Regedit, to REG files.  Then I went to Bart PE's version of Windows Explorer (Go &gt; Programs &gt; A43 File Management Utility) and ran those REG files, adding them back to the registry.  All seemed to function just as normal in Windows.  I then looked at the registry locations in question.  Now I saw that the changes had indeed been made.  Instead, the problem was that the reference to drive X was being recreated despite my efforts.  That is, the new drive T that I had created, trying to follow Microsoft's instructions, was still there; it's just that X was back.

So I reviewed Microsoft's instructions and saw that I had neglected one final step.  I had failed to run Regedt32 and reset the administrator privileges for Mounted Devices to Read Only.  After doing that, once again I rebooted into Bart PE.  None of the changes had been saved.  I was back to square one.  I tried it once more.  This time, I did not do what may have been a mistake on the previous try:  I did not uncheck the Read box on the Administrator permissions.  Doing so had caused the Administrator option to vanish from the dialog box.  This time, instead, I left Read permission in place after making the other changes.

I mickey-moused around with this for quite a while, but got no joy.  This approach basically didn't work for me, as I found upon repeated attempts to reboot into WinXP.  In Recovery Console, I tried FIXBOOT and FIXMBR once more, just for old times' sake, and rebooted once again into WinXP.  Same situation as before.

I was kicking myself for not having used the WinXP backup program to save the system state.  Bizarrely, my two most recent Drive Image backups were showing up as corrupt when I tried to restore them, despite that I had verified them with Image Explorer when I had made them.  What I had restored was the most recent one, just a few days old; but it was not working.

Acting on a tip I had seen in one post, I tried another approach.  On another computer, I used Image Explorer to extract three files from my most recent Drive Image backup.  The three files were named SYSTEM, SOFTWARE, and SECURITY (with no extensions, i.e., not SYSTEM.EXE).  They were found in C:\WINDOWS\system32\config.  Someone's comment led me to understand that these files held the contents of several of the main branches of the registry.  I burned them to a CD and was going to use Bart PE to copy them to the same folder on the target machine.

It was about this time that I discovered why that reference to drive X had been so recurrent.  Drive X was my CD drive.  I was an idiot.  I don't know how it ceased to be drive Z, which was what I had long intended it to be, and when it became drive X.  But there it was.  So that explained why I couldn't get that durned registry to stop referring to drive X.

Anyway, now I went ahead and tried to use BartPE to copy the files from that CD to that folder.  But BartPE needed its own CD to be in the drive, so this didn't work.  I couldn't get it to recognize a jump drive, either, so I rebooted into the WinXP Recovery Console and tried there.  But although the WinXP CD said it was loading USB drivers, it didn't recognize the USB drive.  Of course, it also wouldn't let me remove itself for a minute to copy from the CD, either.  So I had to actually shuffle some hard drives to get those files into that C:\Windows\system32\config folder on the target drive.

Well, and that made a difference!  At least when I rebooted, I did not immediately fall into the load-save-logoff loop.  Instead, I got a dialog:  "The system could not log you on.  Make sure your User name and domain are correct, then type your password again," etc.  So I did.  And I was in!  That was the solution.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
you are the man, that last fixed worked like a charm.. Thanks.

**Anonymous**:
I have no idea what you are talking about but I'll get my geek brother to read this and we'll try it out.Thanks!

**Anonymous**:
I had the same problem here...I cloned the old C the the new hd and booted the pc couple times while moving stuff from the old hds to the new one, the new hd working as the new boot drive at the time.But then I removed the old drives, and got this "loading settings saving settings loop" problem.Your post led me to do the most easiest workaround since all others c:\windows.....userinit.exe->userinit.exe / MountedDevices etc failed)I cloned the C drive again and immediately shutdown the pc and removed the old drives so that the "new C" drive was the only one on the pc and then booted succesfully the PC. (Also make sure that the new hd's mbr is ok (xp rescue console->fixmbr and/or fixboot and that the correct partition is set active->diskpart->select disk->select part->active)Before I got that far, I had to get my Samsung HD753LJ recognized by the bios this post http://blog.techflaws.org/2008/07/22/samsung-hd753lj-sata-hdd-750-gb/ I had to set the speed to SATA2/3.Gbps _NOT_ SATA1/1.5Gbps.Plug & Play my ass, Plug & Pray is more accurate.


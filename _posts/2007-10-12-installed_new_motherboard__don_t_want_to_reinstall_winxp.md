---
layout: post
title: "Installed New Motherboard; Don't Want to Reinstall WinXP"
date: 2007-10-12
---

<div class="post-body">
<p>I installed a new motherboard.  I did not want to have to reinstall Windows XP, because that would mean reinstalling and reconfiguring all of the many pieces of software (including tweaks, Firefox extensions, etc.) that I had installed.  I was looking for a shortcut.

Unfortunately, WinXP would not boot with the new motherboard.  At best, with much tinkering, I got it to go into Safe Mode; but even that died after a while:  when I tried going into Safe Mode after that, I got an error message reading, "Windows XP Setup cannot run under Safemode.  Setup will restart now."

So then I <a href="https://web.archive.org/web/20180904030808/http://webcast.broadcastnewsroom.com/articles/viewarticle.jsp?id=8658-1">found a very step-by-step webpage</a> where there were instructions that seemed to offer a workaround.  The instructions were kind of screwed up, though.  They said there had been some problems with their HTML.  Maybe they'll have it fixed by the time you read this.  But at this writing, to make the instructions work, I had to do some translation.

*** At this point, we undertake an optional detour.  It has to do with the entry of DOS-style commands in Recovery Console.  If you need that, great -- read this section.  But this approach did not solve the problem.  So if you're looking to continue with the main topic, skip to the *** END OF DOS DETOUR *** marker below.

The first step was to boot from the WinXP CD, go into <a href="https://web.archive.org/web/20180904030808/http://support.microsoft.com/kb/314058">Recovery Console</a>, enter <a href="https://web.archive.org/web/20180904030808/http://www.petri.co.il/forgot_administrator_password.htm">the Administrator's password</a>, and then enter some commands.  The basic idea behind these commands was to make a backup of existing system files in a temporary folder, and then replace them with default, original WinXP system files.   The files in question were as follows:

copy c:\windows\system32\config\system
copy c:\windows\system32\config\software
copy c:\windows\system32\config\sam
copy c:\windows\system32\config\security
copy c:\windows\system32\config\default

Those may look like folder names, but those were the actual system files in question.  There were no extensions.  I didn't feel like making a directory and making backups of these files, so I skipped this step.  Most people would probably not want to do that, but I had just restored my whole C drive from a <a href="https://web.archive.org/web/20180904030808/http://raywoodcockslatest.blogspot.com/2007/07/drive-imaging-software.html">Drive Image backup</a>, and I could use Image Explorer to go back into that image and extract these files if I needed them.  If they were indeed corrupt, I wouldn't want to save them; and if they weren't, I didn't have another plan where I would need them anyway.

Also, if I wanted another copy of them, I could copy them over on a CD if necessary.  (The SOFTWARE file, at 8MB, was too big for a floppy.)  The CD drive was accessible from within Recovery Console as drive E.  I found it by typing D: and hitting Enter, followed by DIR to show me a directory listing of D.  That turned out to be another partition on my hard drive, so I tried again with E.  That directory listing looked like the CD, but I typed CD DOCS (since DOCS was one of the folders that showed up in the DIR for drive E) and watched my CD drive light up, which told me I was in the right place.

Anyway, back at drive C, if I had wanted to make a backup of the files in question, I would have used the MD and CD combination.  MD is short for Make Directory, and CD is short for Change Directory.  You only have to make a directory once, and change to it once.  Your DOS prompt will show you where you are after that.  So here are the commands I would have entered to make the first backup copy:
<tt><tt><pre>md c:\windows\tmp
copy c:\windows\system32\config\system c:\windows\tmp\system.bak
</pre></tt></tt>You'd best be sure not to neglect that space before the last C:\.  Anyway, those two commands would give you a copy of the SYSTEM file, which you would have copied as SYSTEM.BAK, in your newly created TMP folder.  (I'm using capital letters for clarity.  DOS is not case-specific.  This isn't exactly DOS, but it's close enough for these purposes.)

Since I didn't bother making those backups, I proceeded instead to the heart of the matter.  The concept here is to copy fresh versions of some WinXP system files to your c:\windows\system32\config folder.  Those files, listed above, come from your c:\windows\repair folder.

If Recovery Console allowed for batch files, I could have done this all in one simple command (after copying these lines into Notepad to create the batch file).  If I could have gotten into Safe Mode, I could have copied these files over all at once from my other computer.  If I had thought of putting them on a USB flash drive, and had plugged it in before booting the WinXP CD, maybe that drive would have been recognized and I could have just copied them from there.  Another possibility:  <a href="https://web.archive.org/web/20180904030808/http://en.wikipedia.org/wiki/BartPE">Bart PE</a> might recognize USB flash drives, so if I had wanted to go to the trouble of bailing out of Recovery Console and booting Bart PE, that might have been an option.  Booting Linux was not an option, because at this point I didn't know of any live Linux CDs that would recognize and copy files to an NTFS drive, which is what my WinXP program partition was.

Judging from the files shown in the REPAIR folder on my other computer, the idea was to copy each non-extension file (e.g., SAM, but not CONFIG.NT)  from the REPAIR folder to the CONFIG folder.  The instructions on the webpage mentioned earlier called for typing in the full pathname (e.g., copy c:\windows\system32\config\system c:\windows\tmp\system.bak) for each file, but I found it easier to CD to one of the folders (another word for "directory") and use a shorter command.

So with all that background information, here's what I actually typed, choosing what seemed like the simplest route.  I was starting at the C:\WINDOWS prompt because that's where Recovery Console started me.  From there, I typed the following:

CD SYSTEM32\CONFIG

[This put me in the CONFIG folder.]

COPY \WINDOWS\REPAIR\DEFAULT

[This copied the DEFAULT file from the repair folder to my present location.  For more information on COPY or any other Recovery Console command, request HELP by typing the command followed by /?.  For example, COPY /? would give information on the COPY command.]

COPY \WINDOWS\REPAIR\SYSTEM
COPY \WINDOWS\REPAIR\SOFTWARE
COPY \WINDOWS\REPAIR\SAM
COPY \WINDOWS\REPAIR\SECURITY X

So now I had all five replacement files from the REPAIR folder in the CONFIG folder.  I didn't take the intermediate step of deleting the presumably corrupted versions of those files from the CONFIG folder before copying.  I just used COPY, and answered Yes when it asked me, each time, if I wanted to overwrite the existing file in the CONFIG folder.

Note that the Up arrow, in Recovery Console, would repeat the previous command.  So it was easy to type those five commands; I just had to type the first one, and then I could repeat it by using the Up arrow, using Backspace to delete the filename, and then typing in the name of the next file.

I verified that I had correctly copied each file by doing a DIR listing and checking the dates of the five files I had just copied.  They were much earlier than most of the other files in the CONFIG folder.  Then I typed EXIT and rebooted from the WinXP CD again.  This time, according to the instructions on that guy's webpage, I was supposed to be able to boot right into WinXP, where I would have to take additional steps.  I doubted it would work.  But I tried.  After typing EXIT, while the system was rebooting, I removed the WinXP CD from the CD drive and watched and waited.  It didn't work.  The system went to exactly the same point and then, once again, shortly after showing me the WinXP bootup logo, it flashed a BSOD (blue screen of death) and rebooted.

*** END OF DOS DETOUR ***

Next time around, I kept hitting F8 while it was going through the introductory stages of booting up.  This gave me the menu of options, including Safe Mode.  I selected "Disable automatic restart on system failure."  That way, the sucker would freeze at the BSOD, giving me a chance to read it and see what it said.  Sometimes BSODs would name a specific problematic driver.  But that wasn't the case here.  I just got the generic one:
<blockquote>A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer.  If this screen appears again ...</blockquote>So I hit the computer's reset button and rebooted.  This time, I used F8 to get into Safe Mode.  I had just restored the system backup that I had saved in a drive image, so at this point I wasn't yet getting the "Windows XP setup cannot run under Safemode" error mentioned above.  Instead, the system proceeded to recognize and "install" various pieces of hardware.

In the previous go-round, I had decided to hit Cancel for each hardware wizard that came up.  My idea was to let the system detect and install as much hardware as possible automatically.  In the previous try, I had already followed the advice of disconnecting as much hardware as possible, just in case there was a conflict between the motherboard and some piece of equipment.  I also ran Memtest86+ for a while; it found no errors.

This time, I came across another webpage that made me think I should try a different approach.  I didn't keep the link for this writing, but the advice was to begin with a Repair Install.  The instructions were as follows:
<blockquote>Changing the motherboard (or the entire system) under your Windows XP installation will stop it working until the system files are repaired and updated.

To do this, you should perform a Repair Install.

The repair install process reinstalls all Windows system files while leaving directories, settings and user data intact. This should fix any corrupted files that are causing BSODs and crash issues. To perform a repair install:

1. Boot from the Windows XP installation CD
2. Choose the 'press enter to set up Windows XP now' option
3. Press F8 to skip through the EULA
4. Now press R to begin a repair installation

Your system will go through the entire XP install process, but will not attempt to replace any of your existing data. It will simply reinstall the system files and redetect all hardware. Once the process has completed, your computer will reboot.
</blockquote> So I rebooted from the WinXP CD and did as I was told.  As instructed, I pressed R to repair my designated Windows installation.  In a previous go-round, I had learned the hard way that the other option would completely reinstall Windows.  Some of my previously installed programs would still work, but many would not.  That was a last-chance possible approach, but I was not too excited about it.

The process ran; the system rebooted; and once again I got the same BSOD and reboot.  So this time I tried something a little different.  When the WinXP CD was loading, I noticed this message:
<blockquote>Press F2 to run Automated System Recover (ASR) ...
</blockquote>So this time I pressed F2.  But that was no answer:  it gave me a screen reading, "Please insert the disk labeled:  Winodws Automated System Recovery Disk into the floppy drive."  I didn't have a disk of that nature.  So that was a dead-end.

I tried booting back into Safe Mode.  Now I got that error message again, "Windows XP Setup cannot run under Safemode."  This time, I thought I might try using the command-line options in Recovery Console.  I was a little discouraged because I had just come across a webpage where the guy said you could spend days trying to get a WinXP installation from one machine (or, in this case, from one motherboard) to work on another.

In Recovery Console, I typed HELP to see the list of possible commands.  From that list, based on previous experience and on comments I'd seen on various webpages in this day's research, I felt that the ones to investigate were BOOTCFG, CHKDSK, FIXBOOT, and FIXMBR.  After further HELP inquiries for each of those (e.g., BOOTCFG /?), I decided to start with BOOTCFG /REBUILD.  That was a mistake.  I managed to create another boot entry, discovering at that point that there was no option to delete it.  I hoped some such option would materialize once I was back in Windows, if I ever got there.

Next, I ran CHKDSK /R.  That, at least, was informative.  It said, "The volume appears to contain one or more unrecoverable problems."  I doubted that those problems had existed in the drive image that I had just restored, since I had restored drive images many times and had never seen this particular error message before.  I figured the problems had probably originated when I had run the Repair Install.

To complete this exploration of Recovery Console, I looked at HELP for FIXBOOT and FIXMBR.  I went ahead and ran FIXMBR, typed Exit, and rebooted.  It crashed at the usual place when attempting to install WinXP in Normal Mode.  In Safe Mode, I got the usual "WinXP can't run under Safemode" message.

I found <a href="https://web.archive.org/web/20180904030808/http://discussions.virtualdr.com/archive/index.php/t-199285.html">a webpage where they said</a> C:\WINDOWS\SYSTEM32\DRIVERS\IPVNMON.SYS might be responsible for that message.  But I didn't have a file by that name on my system.  Another webpage made me think that IPVNMON.SYS should be suspected only where the BSOD is naming that file specifically.

At this point, it seemed that the "fresh install" option was the only alternative to a full reinstallation of Windows XP.  To get there, I took the same first couple of steps as with the Repair Install, above:
<blockquote>  1. Boot from the Windows XP installation CD
2. Choose the 'press enter to set up Windows XP now' option</blockquote>But after that, this time I chose the other option:  "To continue installing a fresh copy of Windows XP without repairing, press ESC."  I pointed the installer toward drive C and told it to go ahead and install on top of the existing WinXP installation:  "Leave the current file system intact (no changes)" and use the existing Windows folder.  After maybe five minutes, the system rebooted and started me down that long road of Windows reinstallation.

A half-hour later, having shot the better part of a day on the efforts described above, I was looking at a "new" Windows installation.  The first question was, how bad was the damage to my previous drive C setup?  I mean, the fresh installation had apparently dealt only with the C:\Windows folder, including the registry.  I wanted an inventory of which programs were still operational and which would now have to be reinstalled.

To conduct that inventory, I decided to look at the Start Menu found in C:\Documents and Settings\All Users\Start Menu\Programs.  I figured that, if a program's icon was still good, that meant it was finding its target executable (usually an EXE file) somewhere; but if the icon had reverted to that plain white rectangle with the blue border, that meant the connection had been destroyed.

The first thing I saw was that my original Start Menu was gone.  I did have backup copy of my extensively customized Start Menu, however.  I was pleasantly surprised.  Most of the links still worked.  The primary exceptions were the Microsoft, Google, Corel, and Adobe products, which it seemed I would have to reinstall, along with QuickTime, and about ten utilities.  There would also be the issue that some programs were no longer installed to run on startup, but I felt those would be manageable.  All in all, it looked like a decent outcome.  After the hassle of reinstalling and configuring Windows and Microsoft Office programs and updates, along with the others just mentioned, it appeared that I would be up and running with my new motherboard.

Of course, this whole process was premised on the assumption that, once I did the installations, I would have a stable system.  The system seemed to be stable so far, in this first hour or so of fiddling around with it.  I proceeded to install my wireless connection and activate Windows.  Perhaps because of the reinstallation I had tried previously, I had to call Microsoft to activate.  Then I began downloading and installing Windows updates.

While that was underway, I began testing my other programs.  It was a blow to discover that the Firefox extensions and configuration would all have to be reinstalled.  As I looked further, the same appeared true for many other programs.  The links on my backup copy of the Start Menu had found their targets, all right; but without the registry modifications that had been made during the initial installation, the linked programs would not actually run.

There were no two ways about it:  I gained little if anything from using this semi-fresh install, and I risked the downside of having many small and large problems, down the line, if this was anything like an upgrade installation -- which, as I had learned years earlier and had seen mentioned repeatedly on webpages since, was not the recommended way to go.

I felt there was no choice but to abandon this attempt and return to a "real," full installation from scratch.  But when I inserted the WinXP CD and started down the installation path, I was reminded that there was no "fresher" way of doing an installation.  I could have wiped off the C drive and really started from scratch, but now I had second thoughts about doing all that.  Maybe I really had nothing to lose from continuing in the present vein.  So I decided to go ahead and try it out as it was.  Maybe it would still save me an hour or two.  Maybe there would be no feared complications.

Well, about three hours later, I had my answer on that.  I tried to install Symantec AntiVirus.  It wouldn't install.  Instead, it gave me an error message, "The System Administrator Has Set Policies to Prevent This Installation."  I looked online for an explanation.  Nobody seemed to have one.  One person said s/he had solved the problem by manually deleting all registry references to Symantec Antivirus.  I tried that.  It didn't solve the problem.  Microsoft had <a href="https://web.archive.org/web/20180904030808/http://support.microsoft.com/default.aspx?scid=kb;en-us;q322963">a tech support document</a> on it, but they said it was just a workaround that might reduce my system's defenses against viruses.  I used System Restore, in repeated tries, working my way back toward the start of my efforts to install and configure programs, and eventually I decided that the problem must be that there were still some lingering Symantec files or settings, somewhere on the drive; and if this could happen to their program, it could happen to others as well.  So I finally did bite the bullet, wipe the disk and start a completely new WinXP installation -- which, of course, would have been half-done by this point, if I had just gone directly to that undesirable solution.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

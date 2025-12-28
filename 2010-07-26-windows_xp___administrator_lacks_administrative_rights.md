---
layout: post
title: "Windows XP:  Administrator Lacks Administrative Rights?"
date: 2010-07-26
---

<div class="post-body">
<p>I had been using a Windows XP SP3 installation for months.  Suddenly, on booting up, I got this message from Kodak EasyShare:<br/>
<blockquote>You are running EasyShare software from a user account that does not have administrative privileges.  As a result, you may not have access to some of the pictures on your computer and some of the features of the software may not be available.  For more information please go to the EasyShare support web site at http://www.kodak.com/go/EasyShareSupport.</blockquote>They lost me at the first sentence.  According to Start &gt; Run &gt; control userpasswords2, the Ray Woodcock account was a member of the Administrators group, and no other, and that was the same for the Administrator.  That is, I should have had the same privileges, when logged in as Ray Woodcock, that I had if I would log in as Administrator.  But it was not simple an EasyShare problem.  Suddenly I was also unable to move or delete files in the My Documents folder.  Attempting to do so would give me this error message:<br/>
<blockquote>Error Deleting File or Folder<br/>
Cannot delete [filename]: Access is denied.<br/>
Make sure the disk is not full or write-protected and that the file is not currently in use.</blockquote>So it seemed to be a situation in which Ray Woodcock had administrative privileges, and yet did not have administrative privileges.  If it had been just a matter of deleting unwanted files that WinXP did not want to let me delete, I would have used one of the <a href="https://web.archive.org/web/20190906053659/http://winhlp.com/node/39">several methods</a> for working around that.  (My own favorite was to run Windows XP within a virtual machine, running on Ubuntu, and just drop out of WinXP and use Ubuntu to delete or move the files in question.)  But the simultaneous arrival of the Kodak EasyShare message, which I had not seen before, suggested that I had a bigger problem.<br/>
<br/>
I used Notepad to create a plain text file in a different folder, and then tried to delete it.  That worked.  I tried the same thing in the problematic folder, and that worked too.  So I could delete .txt files in that folder, but not .exe files.<br/>
<br/>
I noticed that Windows Explorer was not automatically updating or refreshing itself when I created or deleted those files; I had to hit F5 to refresh manually.  In Start &gt; Run &gt; regedit, I went to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Update and saw that, sure enough, the UpdateMode value was set to zero.  I changed that to 1 and rebooted.  That problem seemed to be fixed; but then it wasn't.  One or two reboots later, it was back.  More generally, Windows Explorer was not responsive when I tried to highlight something.<br/>
<br/>
Something else had changed, too:  my system was now defaulting to log into the Administrator account as well as the Ray Woodcock account (and, weirdly, even the Administrator login produced that EasyShare message about not having administrative privileges).  I logged off the Administrator account and, in the Ray Woodcock account, I went into regedit again, to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon and saw that the default user name was Administrator.  I changed that (and also AltDefaultUserName) to Ray Woodcock and rebooted.  Now at least the login part was fixed.  But I was still getting that EasyShare message.<br/>
<br/>
I decided to experiment with creating and deleting different file types in that folder.  It seemed odd that I could create and delete .txt files but not the .exe file that I had tried to delete, in that same folder.  I created a new .txt file and renamed it to be a .pdf file, and then I deleted it.  No problem.  I did the same as an .exe.  I could create the .exe, but I got the "Cannot delete" error when I tried to delete it.  Same thing in another folder.<br/>
<br/>
I tried exploring one of the routes mentioned in that list of deletion  methods (above).  This had to do with making sure that I had access rights to a particular folder.  But I did have access rights to the folder; I just didn't have access rights to .exe files.  And anyway, what about that other problem, involving the EasyShare message?<br/>
<br/>
I had just been tinkering with several antivirus and firewall programs, and also with PortableApps.  Since the system seemed to be somewhat screwed up, I decided to restore an Acronis image from several weeks earlier and then reinstall programs and see if I could narrow down the culprit.  As expected, the problem was not there after restoration.  I did not try to replicate the problem, and it did not crop up on its own in the near term.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

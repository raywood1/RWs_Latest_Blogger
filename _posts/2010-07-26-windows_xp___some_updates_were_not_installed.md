---
layout: post
title: "Windows XP:  Some Updates Were Not Installed"
date: 2010-07-26
---

<div class="post-body">
<p>I had experienced <a href="https://web.archive.org/web/20190906053706/http://raywoodcockslatest.blogspot.com/2010/03/problems-installing-updates-on-windows.html">occasional problems</a> when trying to install updates to Windows XP SP3.  At some point, those problems stopped being resolved and started accumulating.  At the time of writing this post, I faced a situation in which <a href="https://web.archive.org/web/20190906053706/http://www.update.microsoft.com/">the Microsoft Update webpage</a> told me that I had 47 "High Priority" updates to install, along with seven optional hardware and software updates; and yet, each time I tried to install those updates, I got the messages "Some updates were not installed" and "The following updates were not installed."  I was concerned that these updates might be important for system security and stability.<br/>
<br/>
On this particular day, I had once again <a href="https://web.archive.org/web/20190906053706/http://social.msdn.microsoft.com/forums/en-US/windowsdesktopsearchhelp/thread/c1d64ba5-aaa1-4eae-ad04-d7e85418199e/">sought out advice</a>.  The summary of the steps I took, all of which failed, is as follows:<br/>
<br/>
<div style="text-align: center;">*   *   *   *   * </div><br/>
*** FIRST TRY ***<br/>
<br/>
<br/>
6. Make a folder "C:\WUAGENT" (any location/name can be used). Download into it:<br/>
   - http://download.windowsupdate.com/v7/windowsupdate/redist/standalone/WindowsUpdateAgent30-x86.exe<br/>
   - better yet, read "http://support.microsoft.com/kb/949104" and get the proper file there.<br/>
7. Start -&gt; Run "C:\WUAGENT\WindowsUpdateAgent30-x86.exe /wuforce".<br/>
   - note: this failed for me if the "Automatic Updates" service was stopped.<br/>
   - I (RW) had to run it twice to get it to work.<br/>
8. In IE run "Tools -&gt; Windows Updates" - perhaps a few times as it rebuilds update stuff.<br/>
<br/>
*** SECOND TRY ***<br/>
<br/>
First, do this:<br/>
<br/>
1. Start -&gt; Run "services.msc" (in Vista, it's Start-&gt;All Programs-&gt;Accessories-&gt;Run)<br/>
2. Right "Automatic Updates" and select "stop".<br/>
3. Start -&gt; Run "%systemroot%"<br/>
4. Delete "SoftwareDistribution" folder and "WindowsUpdate.log"<br/>
5. Back in services, right-click "Automatic Updates" and select "start".<br/>
<br/>
Then run steps 6-8, above.<br/>
<br/>
*** THIRD TRY ***<br/>
<br/>
Start &gt; Run &gt; regsvr32 wups2.dll<br/>
Then try running Windows Updates.<br/>
<br/>
*** FOURTH TRY ***<br/>
<br/>
REGSVR32 WUAPI.DLL<br/>
REGSVR32 WUAUENG.DLL<br/>
REGSVR32 WUAUENG1.DLL<br/>
REGSVR32 ATL.DLL<br/>
REGSVR32 WUCLTUI.DLL<br/>
REGSVR32 WUPS.DLL<br/>
REGSVR32 WUPS2.DLL<br/>
REGSVR32 WUWEB.DLL<br/>
<br/>
*** FIFTH TRY ***<br/>
<br/>
net stop wuauserv<br/>
regsvr32 %windir%\system32\wups2.dll<br/>
net start wuauserv<br/>
<br/>
*** SIXTH TRY ***<br/>
<br/>
Look at the log file for one of the updates.  Example:<br/>
Security Update for Windows XP (KB979309)<br/>
<br/>
Then put that number into the following command:<br/>
<br/>
%windir%\KB979309.log<br/>
<br/>
In my case, the end of this log file gave me this information:<br/>
1,297: [PatchFilesFromResponseBlob] returning STATUS_READY_TO_INSTALL<br/>
1,313: KB979309 installation did not complete.<br/>
1,313: Update.exe extended error code = 0xf201<br/>
<br/>
For guidance on whether the update was installed or not, see:<br/>
http://support.microsoft.com/kb/910339/.  <br/>
<br/>
Following the advice on that webpage, look up that error code.  See:<br/>
http://support.microsoft.com/kb/906602/.<br/>
<br/>
That didn't work for me, possibly because I had already obliterated the evidence in previous steps.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
the articles solved my problem:http://support.microsoft.com/kb/910341


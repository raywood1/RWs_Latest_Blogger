---
layout: post
title: "Ubuntu 9.10, VMware Workstation 7: Failed to Open Sound Device (Workaround)"
date: 2010-02-10
---

<div class="post-body">
<p>In <a href="https://web.archive.org/web/20190906053746/http://raywoodcockslatest.blogspot.com/search?q=sound+device+%28continued%29">previous posts</a>, I tried fixing error messages that I was getting in a Windows XP virtual machine (VM) running on VMware Workstation 6.5.2 on Ubuntu Linux, version 9.04.  I didn't know, at that time, whether some of my problems stemmed from having done an upgrade rather than a clean install of Ubuntu.  Now I found myself facing the same problem again, after a clean install of both Ubuntu 9.10 (Jaunty Jackalope) and VMware Workstation 7.<br/>
<br/>
The problem was as follows:  if I checked the "Connect at power on" option, then audio would not run in the VM until (in full screen mode) I went into VM &gt; Removable Devices &gt; Sound Card &gt; Connect; but when I did that, I would get this error message:<br/>
<br/>
<blockquote>Failed to open sound device /dev/audio: Device or resource busy.  Failed to connect virtual device sound.</blockquote><br/>
<a href="https://web.archive.org/web/20190906053746/http://communities.vmware.com/thread/251750">One recent discussion</a> seemed to suggest that the problem was that Flash Player and/or Alsa audio.  I suspended my VMs and rebooted the computer.  When it rebooted, I made sure that Firefox was not running.  I resumed the VM and audio played OK in IrfanView.  I started Firefox inside the VM (i.e., in Windows XP) and played a YouTube video.  The audio was still OK in IrfanView.  I started a second session of Workstation and resumed a different VM in that session.  The manual sound card connection went OK; and there, too, I could play audio without stuttering.  The audio in the second VM was not as good; it had some static.<br/>
<br/>
With those two VMs open, I started Firefox in Ubuntu (i.e., not in a WinXP VM).  I played another YouTube video.  Now I got an error message, and audio would not play in IrfanView within the VM.  I tried the other VM; same thing.  The error message was "Failed to open sound device /dev/audio: Device or resource busy.  Sound will be disconnected."  I went back to Ubuntu and killed Firefox.  Now I was able to connect the sound card and play audio inside the two VMs, same as before, complete with mini-stutters in the second one.  I started Firefox again in Ubuntu.  The audio was still OK inside the VM.  If I was playing audio in IrfanView in the VM and then went into a YouTube page in Firefox, the audio would not play in the latter.  I had to restart Firefox to get its YouTube audio to play, and then, as before, I was not able to hear audio inside the VM.  It worked the same way if I played a YouTube video in Opera rather than in Firefox.  So it seemed that the problem (which has apparently been around for years) continued to be within VMware Workstation.<br/>
<br/>
For the time being, the solution seems to be either (a) to watch videos and other webpages that use Flash, do it in a browser session that is running inside your VM, not in a browser running in Ubuntu, or (b) after watching a video or otherwise using Flash in Ubuntu, kill the program that used it (e.g., Firefox) and manually reconnect with your sound card inside the VM.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

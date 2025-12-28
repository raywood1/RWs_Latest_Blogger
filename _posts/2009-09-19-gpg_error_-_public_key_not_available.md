---
layout: post
title: "GPG Error - Public Key Not Available"
date: 2009-09-19
---

<div class="post-body">
<p>In 64-bit Ubuntu 9.04 (Jaunty Jackalope), I received this message after clicking the Check button in (System &gt; Administration &gt;) Update Manager:
<blockquote>W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061</blockquote>The <a href="https://web.archive.org/web/20190906053745/https://answers.launchpad.net/ubuntu/+question/73171">recommended solution</a> was to type this into Terminal:
<blockquote>gpg --keyserver keyserver.ubuntu.com --recv [last 8 characters of code]; gpg --export --armor [last 8 characters of code] | sudo apt-key add</blockquote>In my case, as shown above, those last eight characters were 9D1A0061, so that's what I entered into the command just given.  This gave me a message, "gpg: requesting key 9D1A0061 from hkp server keyserver.ubuntu.com."  But then we went no further:  after several minutes, I got this message:
<blockquote>gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
[sudo] password for ray: gpg: WARNING: nothing exported</blockquote>and then it just seemed to hang there.  So I tried <a href="https://web.archive.org/web/20190906053745/http://kovyrin.net/2006/11/28/debian-problem-apt-get-update/">a different approach</a>.  Although "apt-key update" was supposed to work, it didn't; it gave me this:
<blockquote>gpg: can't access `/etc/apt/trustdb.gpg': Permission denied
gpg: fatal: can't init trustdb: trust database error
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768</blockquote>Continuing, then, with what looked like an earlier approach at that same webpage, I tried this:
<blockquote>gpg --keyserver wwwkeys.eu.pgp.net --recv-keys F9A2F76A9D1A0061

sudo apt-key add /root/.gnupg/pubring.gpg

apt-get update</blockquote>. . . using, in other words, the full key from the error message in the first of these three command line entries. This approach appeared to be working better:  the first line got me an indication that a key had been imported.  But the second line ("apt-key add ...") resulted in an error:  "gpg: can't open `/root/.gnupg/pubring.gpg': No such file or directory."  I was still getting the error when I clicked "Check" in Update Manager.  A comment added to the instructions cited above suggested using this:
<blockquote>sudo apt-get install debian-archive-keyring</blockquote>but I still got the same error in Update Manager.  Another comment said this would work:
<blockquote>apt-key list

apt-key del [last 8 digits of key shown as expired in the apt-key list output]
[repeat this del command for each such expired key]

dpkg –purge debian-archive-keyring

apt-get install debian-archive-keyring
</blockquote>I got tired of typing "sudo" in front of each line, so I just typed "sudo -i" and then started down this list.  I only got to the first command:  it appeared that I didn't have any expired keys.  So this wasn't the fix for me.  Still another suggestion from the comments in that same webpage:
<blockquote>sudo apt-get update -o Acquire::http::No-Cache=True</blockquote>This ran, and then advised me to run apt-get update.  I ran that twice, but still got that same message about the Opera key, and the same error message persisted when I ran Update Manager.  From <a href="https://web.archive.org/web/20190906053745/http://deb.opera.com/">a Debian page</a> that I located by doing <a href="//web.archive.org/web/20190906053745/https://www.google.com/search?hl=en&amp;q=%22NO_PUBKEY+F9A2F76A9D1A0061%22&amp;sourceid=navclient-ff&amp;rlz=1B3GGGL_enUS291US291&amp;ie=UTF-8">a search</a> for the specific NO_PUBKEY error message (above), I got this:
<blockquote>wget -O - http://deb.opera.com/archive.key | sudo apt-key add -</blockquote>and that seemed to solve the problem.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Benjamir**:
You probably want to put the solution that actually works up at the top of this article.... why bother posting the ones that don't work at all?anyways, thanks for the help, typingsudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -worked for me

**raywood**:
Benjamir - it's a good question.  I have several reasons for doing it this way:  (1) Often, in these long posts, I cover answers that did work for other people.  (2) Sometimes the steps that work are successful because, in the process, I have changed other settings, updated drivers, etc.  If people go directly to the bottom line, it may not work for them because they won't have done the intermediate stuff.  (3) There are usually a number of sites that do what you suggest.  My purpose is not just to state "the answer," but to log the process.

**Iphien**:
Perfect, it works for me with Ubuntu 9.04 Jaunty. Thanks.

**Tanjib**:
It didn't work for me. I typed the code and it came--2010-06-21 09:43:56--  http://deb.opera.com/archive.keyResolving deb.opera.com... 195.189.143.183Connecting to deb.opera.com|195.189.143.183|:80... connected.HTTP request sent, awaiting response... 200 OKLength: 2441 (2.4K) [application/pgp-keys]Saving to: `STDOUT'100%[======================================>] 2,441       12.2K/s   in 0.2s2010-06-21 09:43:58 (12.2 KB/s) - `-' saved [2441/2441]OKI still get the same error message from the Update Manager while clicking  Check. Can anyone help?


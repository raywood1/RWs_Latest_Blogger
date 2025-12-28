---
layout: post
title: "VMware Workstation 7.1 in Ubuntu 10.10 Host:  VMCI Sockets Problem"
date: 2010-11-12
---

<div class="post-body">
<p>I had installed VMware Workstation 7.1.2 on an Ubuntu 10.10 host.  Windows XP was not performing very well in it.  I wondered if the problem was that, when I started VMware Workstation 7.1.2, it said this:<br/>
<blockquote>Before you can run VMware, several modules must be compiled and loaded into the running kernel.</blockquote>It gave me that same message every time I started Workstation.  When I went ahead and clicked on Install, it showed me the list of things that it was doing.  Last on the list was "VMCI Sockets."  Every time, it would show green checkmarks for all the other items, but for that item I would get a red exclamation mark.  If I started Workstation by using the "sudo vmware" command, Terminal would show me a list of error messages just before starting Workstation.  A number of those messages said this:<br/>
<blockquote>error:  'struct sock' has no member named 'sk_sleep'</blockquote>Terminal also said that all of the other "Starting VMware services" processes went off OK, but "VM communication interface socket family" failed.<br/>
<br/>
<a href="//web.archive.org/web/20190906053706/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=iHw&amp;rlz=1R1GGLL_en___US404&amp;q=vmware+%22workstation+7%22+error+%22struct+sock%22+OR+%22VM+communication+interface+socket+family%22&amp;aq=f&amp;aqi&amp;aql&amp;oq&amp;gs_rfai">A search</a> led to <a href="https://web.archive.org/web/20190906053706/http://communities.vmware.com/message/1594839">the suggestion</a> to uninstall and reinstall Workstation, but one user there reported that that didn't help, though that appeared to be because s/he was using Xen Kernel.  <a href="https://web.archive.org/web/20190906053706/http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10">Another webpage</a> offered a patch to fix it.  I downloaded <a href="https://web.archive.org/web/20190906053706/http://www.debuntu.org/sites/www.debuntu.org/files/vmware-7.1-ubuntu10.10-patch-v2.tar_.gz">the patch</a>, navigated to my download folder (using "cd" to change directories and having set the download folder in Firefox, Edit &gt; Preferences &gt; General tab), and typed these commands, as suggested:<br/>
<blockquote>tar -xzvf [patchname]<br/>
<br/>
cd vmware-7.1-ubuntu10.10-patch<br/>
sudo sh ./apply_patch.sh </blockquote>I have written "[patchname]" here because the filename of the download had changed since the original webpage was written.  The first command created a folder named "vmware-7.1-ubuntu10.10-patch" and copied files into it.  The second command put me into that folder.  The third command ran the patch.  When I ran the patch in the form suggested on the webpage, I got "Permission denied."  I revised the third command to the form shown above, and that ran successfully.  When I typed "sudo vmware" now, I got a green checkmark at all items, including VMCI Sockets.  So it worked.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Kamal**:
Thanks, saved my day.

**Anonymous**:
I had to install patch. Then it worked like a chimp.T.Hanks

**Anonymous**:
It's WORKED !!!THANK YOU !!!

**Anonymous**:
Wonderful!!! thanks so much, it worked a charm =)

**Anonymous**:
Thanks, it worked :)

**Anonymous**:
thank you! great work!!


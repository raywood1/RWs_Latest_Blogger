---
layout: post
title: "rsync, USB Drive, Error 30:  'Read-Only File System'"
date: 2009-12-10
---

<div class="post-body">
<p>I was regularly copying a folder to a USB drive in Ubuntu using rsync.  Suddenly, for no apparent reason, the rsync process started producing these error messages:<br/>
<blockquote>rsync:  failed to set permissions on [USB drive/folder/filename]:  Read-only file system (30)<br/>
<br/>
rsync:  mkstemp [USB drive/folder/filename] failed: Read-only file system (30)<br/>
<br/>
rsync:  failed to set times on [USB drive/folder/filename]: Read-only file system (30)<br/>
<br/>
rsync:  delete_file:  unlink [USB drive/folder/filename] failed: Read-only file system (30)<br/>
<br/>
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]<br/>
</blockquote><br/>
The fix, for me, was to reformat the USB drive in Windows.  It would probably work even if Windows was not the cause of the problem.</p>
<div style="clear: both;"></div>
</div>

---
### Comments


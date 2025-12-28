---
layout: post
title: "Ubuntu 10.04:  Repositories"
date: 2010-09-08
---

<div class="post-body">
<p>In the process of <a href="https://web.archive.org/web/20190906053659/http://raywoodcockslatest.blogspot.com/2010/09/ubuntu-1004-installation-another-go.html">reinstalling Ubuntu 10.04</a>, it came time to install my software sources (i.e., repositories).  To start off, I visited <a href="https://web.archive.org/web/20190906053659/http://raywoodcockslatest.blogspot.com/2010/07/ubuntu-1004-problems-with-update.html">my most recent post</a> on that.  It told a tale of difficulty in getting my list of "repos" to work, and referred me to <a href="https://web.archive.org/web/20190906053659/http://raywoodcockslatest.blogspot.com/2010/05/ubuntu-1004-adjustments-software-source.html">one of my earlier posts</a>.<br/>
<br/>
I decided to start by simply copying the finalized list of repos that I had developed and posted in that earlier note.  This replaced my existing /etc/apt/sources.list.  I wasn't sure if I needed to reboot, but having done all those updates and such, I decided it couldn't hurt.  On reboot, I went into System &gt; Administration &gt; Software Sources to see what we had.  There were some items on the list that had to do with individual programs.  I found <a href="https://web.archive.org/web/20190906053659/http://ubuntulinuxhelp.com/the-best-ubuntu-linux-repository-list/">another such list</a> that was even longer.  I wasn't sure why I needed repositories for individual programs; I was under the impression that repositories were places where you could get a variety of programs.  So rather than add to the list (and increase the number of repositories that might report problems later on, as I had experienced previously), I pared down the list.  My final list, preserved in a backup copy of /etc/apt/sources.list, was as follows:<br/>
<br/>
<b>http://archive.canonical.com/ubuntu lucid</b> partner<br/>
<b>http://archive.canonical.com/ubuntu lucid</b> partner (Source Code)<br/>
<b>http://archive.getdeb.net/ubuntu lucid-getdeb</b> apps<br/>
<b>http://packages.medibuntu.org/ lucid</b> free non-free<br/>
<b>http://ppa.launchpad.net/tualatrix/ubuntu lucid </b>main<br/>
<b>http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid</b> main<br/>
<b>http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid </b>main<br/>
<br/>
I clicked Close.  It gave me a chance to Reload, which I took.  It said this:<br/>
<blockquote>Could not download all repository indexes<br/>
The repository may no longer be available or could not be contacted because of network problems ...</blockquote>I closed out of that and typed "sudo gedit /etc/apt/sources.list."  Sources.list still had some lines for repositories that I had deleted, so I deleted those surplus lines.  It also had commands I should run in connection with the rest, so I copied those lines into a separate file in gedit, saved it as RunForRepositories, made it executable ("sudo chmod +x RunForRepositories"), saved a copy for future use, and then ran it ("sh RunForRepositories).  I went back into Software Sources, changed one thing, closed, reloaded, and got the "Could not download all repository indexes" error again.  At this point, I rediscovered that you could add repositories via System &gt; Administration &gt; Synaptic Package Manager.  In Synaptic, I went to <a href="https://web.archive.org/web/20190906053659/http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Extra_Repositories">Settings &gt; Repositories</a>.  But this turned out to be the same thing as the Software Sources tool.  In Software Sources &gt; Other Software, I unclicked and then reclicked an item to trigger the Close &gt; Reload option.  Once again, I got the "Could not download all repository indexes" error.  The first item on the list was the Medibuntu repository, with this message:  "The following signatures could not be verified because the public key is not available."  Following advice, I closed out of that, went into Synaptic, searched for medibuntu-keyring, and applied that.  In Synaptic, I went again into Settings &gt; Repositories and retriggered the Reload.  But it didn't work -- no Reload option -- so I did it via System &gt; Administration &gt; Software Sources.  This time the Medibuntu error was gone, and the first error in the list had to do with the Ubuntu CD.  I decided I didn't want the Ubuntu CD to be a source, so in Software Sources I unchecked the CD on the Ubuntu Software tab, and then retriggered the Reload option again.  No more errors.<br/>
<br/>
For some reason, /etc/apt/sources.list did not show some of these changes.  Maybe I had it open in a separate window while I ws going through my paces.  So I edited it manually to reflect my current preference and resaved a copy on a separate partition.  Now that this was done, I ran System &gt; Administration &gt; Update Manager and installed the new updates they had for me there.  I clicked Check to repeat that step.  It said my system was up-to-date.  I concluded that the repository step was done.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

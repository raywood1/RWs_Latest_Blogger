---
layout: post
title: "Ubuntu:  Backup with Rsync"
date: 2009-12-29
---

<div class="post-body">
<p><div>In <a href="https://web.archive.org/web/20190906051053/http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-and-vmware-trying-again-on.html">a previous post</a>, I got as far as concluding that rsync was the tool of choice for backing up my computer in Ubuntu 9.04. I didn't pursue it because I was short on time and patience for writing scripts at that point. But eventually the need for a regular backup system became acute. So this post logs the steps I took to make rsync and cron work for me.<br/>
<br/>
First, here's <a href="https://web.archive.org/web/20190906051053/http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-and-vmware-multimedia.html">what I wrote previously</a>:<br/>
<blockquote>As an alternative to rdiff-backup, what people had actually mentioned more frequently was rsync. It did not have the incremental backup features of rdiff-backup, to my knowledge, but it seemed to be an established tool for backup purposes. So for now, at least, I thought I might try that instead. Once again, I did <a href="https://web.archive.org/web/20190906051053/http://www.google.com/search?q=rsync+hardy+OR+8.04+ubuntu&amp;sourceid=navclient-ff&amp;ie=UTF-8&amp;rlz=1B3GGGL_enUS286US286">a Google search</a> and got a <a href="https://web.archive.org/web/20190906051053/http://packages.ubuntu.com/hardy/rsync">package details page</a> with no apparent link to any help files. Eventually I found what looked like <a href="https://web.archive.org/web/20190906051053/http://samba.anu.edu.au/rsync/">the official rsync webpage</a> and, after looking at their FAQs and some other pages, landed on <a href="https://web.archive.org/web/20190906051053/http://samba.anu.edu.au/rsync/examples.html">their Examples page</a>. It was intimidating.<br/>
</blockquote>This time, I went to <a href="https://web.archive.org/web/20190906051053/http://samba.anu.edu.au/rsync/documentation.html">their Documentation page</a>. This gave me links to, among other things, <a href="https://web.archive.org/web/20190906051053/http://everythinglinux.org/rsync/">Michael Holve's rsync tutorial</a>. The tutorial said, "You must set up one machine or another of a pair to be an "rsync server" by running rsync in a daemon mode." I was curious, so <a href="https://web.archive.org/web/20190906051053/http://www.google.com/search?num=50&amp;hl=en&amp;rlz=1B3GGGL_enUS292US293&amp;q=%22what+is+daemon+mode%22+ubuntu&amp;btnG=Search">I did a Google search</a> for "what is daemon mode" and I got back, would you believe, exactly one page. One webpage in the entire known planet answered the question, "What is daemon mode?" Except it didn't really answer it. It just said, "It makes wget put standard output into a log file and not bug you while downloading." Accepting that as the best available answer (and ten points to the answerer!), I typed "rsync --daemon" in Ubuntu's Terminal and proceeded to the next step, "Setting Up a Server." After reading it, I decided it didn't seem to apply to me. It was for people who wanted to back up files between computers. I just wanted to back up to another drive.<br/>
<br/>
So I went on to the tutorial's "Using Rsync Itself" section. Since I wasn't sure what daemon mode did, or if it was necessary, I killed that Terminal session and started another. I didn't know if that would shut off daemon mode, or if doing so was what I should do. I read the section and then checked another source of documentation, <a href="https://web.archive.org/web/20190906051053/http://samba.anu.edu.au/ftp/rsync/rsync.html">the rsync man page</a> ("man" being short for "manual"). The man page would ordinarily be output in response to a Terminal command, but someone had put it here in html form, so that's what I used. It reminded me, first, to check Ubuntu's System &gt; Administration &gt; Synaptic Package Manager to make sure I had rsync already installed, here on my secondary computer. I searched Synaptic for rsync and got back a couple dozen listed programs; rsync was among them and was shown as being installed. I looked partway into the man page and got an answer to one question I had from the tutorial. So here's how I translated what the tutorial was telling me. First, the tutorial listed these lines:<br/>
<br/>
rsync --verbose --progress --stats --compress --rsh=/usr/local/bin/ssh --recursive --times --perms --links --delete \<br/>
--exclude "*bak" --exclude "*~" \<br/>
/www/* webserver:simple_path_name<br/>
<br/>
The first thing to know was that this all represented a single command line. It was too long to fit on one line, though, so apparently the trailing backslash said, "This line continues on the next line." The command would be typed into a file and saved as a script, not typed directly into Terminal. I didn't know why the first line didn't end with a backslash. I decided I would want to experiment with this in a relatively safe place -- with a junk directory on my secondary computer, perhaps -- to see what it was doing.<br/>
<br/>
So as the tutorial explained it, the first line of this example told rsync how to proceed: verbosely (i.e., with lots of information about what it was doing), showing a progress report, with statistics. The rsh part was for encryption, to be used optionally if you were sending your stuff online to another computer. I wasn't, so I decided to try leaving that off. I also didn't want to compress the output, because that made the process slower and required more attention from the CPU.<br/>
<br/>
The second line of the example, above, told rsync to recurse -- to work through all of my directories and subdirectories under the folder that I would be naming. It also told rsync to preserve file timestamps and file permissions -- so if, for example, a file was readable only by root on the source drive, it would be the same way on the target drive. The -- links command was an instruction to preserve symbolic links -- not sure what that meant -- and the --delete command, as I understood it, would tell rsync to delete anything on the target that wasn't on the source. So you'd have a mirror, and not just an accumulation of backups of files that you have deliberately trimmed out of your file collection.<br/>
<br/>
The third line of the example told rsync not to bother copying some kinds of files. I liked the sound of that at first, but then I decided I would rather be able to do a Properties comparison of source and target and verify that both had exactly the same number of files. So I decided to leave out this line when I used rsync.<br/>
<br/>
The fourth line of the example named the source and target locations. I wasn't going to be using it with a remote source or target, so mine was going to look somewhat different from this.<br/>
<br/>
On that basis, here's what I assembled as a test version of the rsync example from above:<br/>
<br/>
rsync --verbose --progress --stats \<br/>
--recursive --times --perms --links --delete \<br/>
/media/DATA/Source /media/DATA/Target<br/>
<br/>
I created a Source subfolder in my DATA folder and put a TestFile.txt file into it. I also created a Target subfolder in DATA. Then I copied those three rsync lines into a file in Ubuntu's Text Editor (gedit) and saved it to Desktop as TestRun. To make it executable, I went into Terminal, typed "cd /home/ray/Desktop" and then "chmod +x TestRun" and then double-clicked on TestRun and said Run. And, you know, it worked. Just like that. Not exactly as intended -- I had not only TestFile.txt but also the whole Source folder underneath my Target folder -- but, yeah, there it was. I deleted the Target folder and ran it again and, sure enough, it created the Target folder and then inserted a copy of the Source folder into it. Excellent!<br/>
<br/>
Now it was time to try something a little bolder. I wanted to see how it worked if I tried to copy the whole DATA folder to an external drive. This part was a little confusing. The external drive seemed to have two different names. If I looked in /media, its name was simply "disk." But if I hit the Computer icon in File Browser, it came up as "193.8 GB Media." I decided the latter sounded more specific, so I would try that first. So now the third line of my TestRun file read like this:<br/>
<br/>
/media/DATA "/media/193.8 GB Media"<br/>
<br/>
I used quotation marks because there were spaces in the name. I saved TestRun and double-clicked it again on the Desktop. It didn't seem to do anything. I realized that I had probably made a mistake in that line, and tried again like this:<br/>
<br/>
/media/DATA "/193.8 GB Media"<br/>
<br/>
That didn't do it either, so I tried again, without the leading slash:<br/>
<br/>
/media/DATA "193.8 GB Media"<br/>
<br/>
That still didn't work, so I tried the other approach:<br/>
<br/>
/media/DATA /media/disk<br/>
<br/>
Still nothing. I went into System &gt; Administration &gt; Partition Editor (GPartEd), wiped out the target partition, and recreated it as a FAT32 partition. Now the drive was totally invisible to Ubuntu. I went back into GPartEd and reformatted it as an ext3 partition. Then I realized: it was an IDE drive, so apparently it would not be recognized until I rebooted. I decided to reboot into Windows (I had a dual-boot system) and format it as NTFS. I named it 186GB (which seemed to be the net amount of space available in NTFS format) and rebooted into Ubuntu. I revised TestRun's last line again:<br/>
<br/>
/media/DATA /media/186GB<br/>
<br/>
and ran it again. This time, it seemed to be working -- the external 186GB drive was making noise -- but I wondered why I wasn't getting a verbose indication of what was going on. I guessed that, if I wanted the verbose information, I would have to execute rsync on the command line, not in an executable script. While I was rooting around for an answer to that question, I was reminded that I could also use the shorthand versions of these commands. So instead of typing --verbose into the script, I could just type -v and whatever other letters I needed. In this approach, the final contents of TestRun, which were as follows:<br/>
<br/>
rsync --verbose --progress --stats \<br/>
--recursive --times --perms --links --delete \<br/>
/media/DATA /media/186GB<br/>
<br/>
could instead be expressed like this, if I understood the man page's Options Summary section correctly:<br/>
<br/>
rsync -vshlEPtrip --del --delete-excluded --force \<br/>
--exclude RECYCLER \<br/>
--exclude "System Volume Information" \<br/>
/media/DATA /media/186GB<br/>
<br/>
In that version, I added a couple other options that seemed appropriate, and also told rsync to exclude (i.e., don't copy) those extra folders that Windows XP seemed to put on every drive. I revised TestRun along these lines and, when the external drive settled down and it looked like the foregoing TestRun process had ended, I ran it again. But it didn't seem to make any difference. The extra folders were still there. I had understood that it would delete them. Part of the problem seemed to be that I had not used the syntax correctly. I was supposed to use an equals sign: --exclude=RECYCLER. But another part of the problem was that it was not clear whether the "exclude" command was supposed to work with directories. It didn't seem so. The man page just referred to excluding files. I tried again with equals signs, but still no change. I <a href="https://web.archive.org/web/20190906051053/http://ubuntuforums.org/showthread.php?p=5954467#post5954467">posted a question</a> on it, but the kind response was unfortunately not able to resolve the issue.<br/>
<br/>
Next, I tried a modified version of TestRun on the primary computer. I went through several revisions and wound up with this version, which seemed to work:<br/>
<br/>
rsync -vchlEtrip --progress --del --ignore-errors --force /media/CURRENT/ "/media/OFFSITE/P4 CURRENT"<br/>
<br/>
The partition being backed up, in this case, was an ext3 partition named CURRENT, and the target to which it was being backed up was a USB external drive named OFFSITE. (Some weeks have passed since I started this post, so there may be some discontinuity in my writing at this point.)<br/>
<br/>
I did not run this command as a script within a file called TestRun that I would start by double-clicking on it, because I discovered that you would only get the detailed output if you entered the rsync command on the command line. I was able to enter all of the foregoing rsync command on one line. I did not need the "exclude" commands because this was not an NTFS drive formatted by Windows. I still had ext3 "lost+found" and Trash folders that got copied over in this way, but they were small, so it was OK.<br/>
<br/>
As I think I may have said before, I got the selected rsync parameters by typing "man rsync" at the command line. It did take some trial and error to get this particular set. The resulting backup, when checked by right-clicking and selecting Properties, seemed to be virtually identical.<br/>
<br/>
When I ran that rsync command, it showed me lots of detail on what it was doing. It concluded with this message:<br/>
<blockquote>rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]<br/>
</blockquote>Eventually, however, I did figure out how to do it.  Here is an example of an rsync command that worked for me:<br/>
<blockquote>rsync -qhlEtrip --progress --delete-after --ignore-errors --force --exclude=/.Trash-1000/ --exclude=/lost+found/ /media/CURRENT/ /media/CURRBACKUP<br/>
</blockquote><br/>
This one would back up what Windows sees as drive D (named CURRENT) to a partition that Windows sees as drive G (named CURRBACKUP).  Both partitions had to be mounted in Ubuntu before this would work.  I used a similar command to copy a folder on CURRENT to a USB jump drive named KINGSTON.  That gave me a portable copy of the current state of that folder, ready to take along.<br/>
<br/>
The next thing I needed to do was to back up my blogs.  I started by just wanting to be able to back up a webpage.  I had discovered that all of the posts on a Blogger (i.e., Blogspot) blog like this one could be <a href="https://web.archive.org/web/20190906051053/http://googlesystem.blogspot.com/2007/02/how-to-backup-blogger-blog.html">displayed in a single webpage</a>, at least if you had less than 1,000 posts.  To do that, you just needed to go to this URL:  http://blogname.blogspot.com/search?max-results=1000.  I wasn't sure what would happen if you entered a larger number than 1000.  So now that I had that webpage, I wanted to know how to save a copy of it automatically.  Strangely, at this point, Google searches for any of these sets of terms<br/>
<blockquote>ubuntu "back up a webpage"<br/>
rsync "back up a webpage"<br/>
rsync "copy a webpage"<br/>
</blockquote><br/>
<br/>
produced zero hits.  Eventually, it started to look like this was because I was barking up the wrong tree.  As described in <a href="https://web.archive.org/web/20190906051053/http://raywoodcockslatest.blogspot.com/2009/12/ubuntu-904-backing-up-and-copying.html">a separate post</a>, it seemed that what I wanted for this purpose might be wget, not rsync. <br/>
</div></p>
<div style="clear: both;"></div>
</div>

---
### Comments
**shohanali ali**:
GSCopy Pro v6.0 (RoboCopy Alternative) with Open File AgentGSCopyPro is a single command-line tool (CLI) that can copy, replicate and move files from one folder to another. This folder can be on the same machine/ server or another server elsewhere. What makes GSCopyPro stand out from other competitors is the fact it works on 32-bit as well as 64-bit systems and has no restrictions. It can easily be scheduled to run as a scheduled task and fully automated. GSCopyPro also comes with an open file agent which can copy files that are locked/ opened by other processes. This feature is supported in all windows vSCersions from widows XP/ 2003 and later.Go To:>> http://www.gurusquad.com/GOPYPRO


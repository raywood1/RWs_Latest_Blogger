---
layout: post
title: "Windows 7:  Choosing Partition Wizard to Resize Partitions"
date: 2011-01-10
---

<div class="post-body">
<p>In the process of installing Windows 7, I found that I needed to make some space on a drive.  In Windows 7, I ran Disk Management (Start button &gt; type "diskmgmt.msc" &gt; right-click on the partition to be shrunk &gt; Shrink Volume).  I got a  message:  "Querying volume for available shrink space, please wait ..."  Then it said that it could only shrink the volume by 5182MB.  This was absurd:  Disk Management itself showed that the volume had hundreds of gigabytes of free space.  The dialog said this:<br/>
<blockquote>You cannot shrink a volume beyond the point where any unmovable files are located.</blockquote>In that dialog, I clicked on the "Shrink a Basic Volume" link.  It offered advice on using the command-line DISKPART tool.<br/>
<br/>
I did <a href="https://web.archive.org/web/20150620064632/http://www.google.com/search?sourceid=chrome&amp;ie=UTF-8&amp;q=%22Windows+7%22+%22cannot+shrink+a+volume+beyond+the+point+where+any+unmovable+files+are+located%22&amp;qscrl=1">a search</a> and found references to various third-party programs for this purpose.  I had previously used GParted, which was available as either <a href="https://web.archive.org/web/20150620064632/http://www.google.com/search?aq=f&amp;sourceid=chrome&amp;ie=UTF-8&amp;q=GParted&amp;qscrl=1">a standalone</a> or as part of the <a href="https://web.archive.org/web/20150620064632/http://www.ubuntu.com/desktop/get-ubuntu/download">Ubuntu live CD</a>.  I was now seeing some indications that GParted was not the best Windows 7 partition manager.  I had already tried using it to shrink this partition, but it had not been able make much space either.  I also shared <a href="https://web.archive.org/web/20150620064632/http://www.wilderssecurity.com/showthread.php?t=261214">the complaint</a> that it was slow.  I preferred slowness over losing data, but it seemed that people were having good luck with alternatives.<br/>
<br/>
Among the various <a href="https://web.archive.org/web/20150620064632/http://www.filebuzz.com/findsoftware/Gparted_Partition_Manager/freeware-1.html">free and paid alternatives</a>, it seemed that the freeware program <a href="https://web.archive.org/web/20150620064632/http://www.partitionwizard.com/free-partition-manager.html">Partition Wizard</a> was getting <a href="https://web.archive.org/web/20150620064632/http://www.google.com/search?sourceid=chrome&amp;ie=UTF-8&amp;q=%22Partition+Wizard%22+OR+PartitionWizard+reviews&amp;qscrl=1">good reviews</a>.  I downloaded and installed it.  I also <a href="https://web.archive.org/web/20150620064632/http://www.partitionwizard.com/download.html">downloaded the .iso file</a> for its bootable CD, and burned that to a disc for standalone functionality, which would ordinarily be capable of doing more than a program could do <a href="https://web.archive.org/web/20150620064632/http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/">while Windows was running</a>.<br/>
<br/>
I burned the CD.  (In Windows 7, just right-click on the .iso and choose Burn Image.)  I used it to reboot the target computer.  My first usage, to move a large partition, was faster than a similar operation had been in GParted.  I proceeded to use the moved and resized partitions without problems.  Partition Wizard appeared likely to be my partition tool going forward.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Recently upgraded; new computer and windows 7.  The problem I encountered had to do with accidentally running my network cables parallel with power cables.Yes, that's enough (noise) to make your internet connections run amok.  Cable transmissions don't remain stable when run next to power cables.


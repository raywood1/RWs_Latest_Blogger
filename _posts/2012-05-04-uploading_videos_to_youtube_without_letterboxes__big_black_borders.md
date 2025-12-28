---
layout: post
title: "Uploading Videos to YouTube without Letterboxes (Big Black Borders)"
date: 2012-05-04
---

<div class="post-body">
<p>I was doing some occasional video editing, mostly using Adobe Premiere Elements.  Now and then, when I would upload a video to YouTube, it would have a letterbox.  That is, the video would be encased within a wide black rectangle.  This made the video smaller.  I didn't want it.  Getting rid of it was not easy.  This post presents a few notes in that direction.<br/>
<br/>
One suggestion I encountered in a few different discussion threads was to add a certain tag to the Tags field available for each YouTube video.  The recommended tag was yt:crop=16:9.  I was supposed to type that into the Tags field, presumably separated from other tags by a comma, and that was supposed to expand the video.  I did find that this worked with one video, where I inserted that tag while the video was still uploading.  I found that it did not work with two other videos that were previoulsy uploaded, where I added the tag after the fact.  An alternative was to use yt:stretch=16:9.  That, too, failed with the previously uploaded videos.<br/>
<br/>
I came across some Adobe suggestions on adjusting <a href="https://web.archive.org/web/20151210033357/http://help.adobe.com/en_US/PremiereElements/7.0/WS09e4b3c48f3a79fc19b622510385d4355c-7f90.html" target="_blank">pixel</a> and <a href="https://web.archive.org/web/20151210033357/http://help.adobe.com/en_US/PremiereElements/9.0/Using/WS09e4b3c48f3a79fc19b622510385d4355c-7f94.html" target="_blank">frame</a> aspect ratios.  They didn't look terribly technical, and at some point I realized I would probably benefit from understanding them.<br/>
<br/>
In the meantime, however, I found that I could sometimes resolve the issue by producing my video, in Premiere Elements, as an AVI, and then importing that AVI back into a new project.  Sometimes the re-importation would provoke Premiere Elements to ask if I wanted to correct my aspect ratio.  I didn't seem to lose any quality from this step, it didn't seem to require much additional time, and the MP4 that I would then output as my final project seemed to upload and display on YouTube without any letterbox problems.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
Forgot to mention:  I might have to crop the re-imported AVI in Premiere Elements to make it right.  Edit > Transform > Crop > Show Properties > Crop and Zoom.

**alex026**:
Finaly did you find a strong solution for this problem ?I'm using adobe premiere elements 10 and i have this strange problem "lettersboxe" in my youtube videosand i don't know how to resolve itthe origin size of my videos are always 1440x900 (size of my screen comptuter) because i used fraps to take a screencast of games(We must watch in full screen)http://youtu.be/ZRVmvuJR5TEI really do not know what to do ...

**raywood**:
I founda videothat did not help, but this advice following the video did the job (thanks toCebuLips9):"When making a new project, go to settings and select 16:9 project. Then import your video, apply crop, but set all the crop levels to zero and set the "zoom" box to checked, ad the export as you﻿ do in this video."I was able to make this work with an already-existing Premiere Elements project.  I saved the video as a widescreen AVI and then started a new project, using the settings recommended above, using the just-created AVI as the video being cropped.


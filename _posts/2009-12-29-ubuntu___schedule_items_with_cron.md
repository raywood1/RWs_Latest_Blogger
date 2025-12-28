---
layout: post
title: "Ubuntu:  Schedule Items with Cron"
date: 2009-12-29
---

<div class="post-body">
<p>I wanted to schedule regular backups in Ubuntu 9.10.  I had already worked out <a href="https://web.archive.org/web/20190906053752/http://raywoodcockslatest.blogspot.com/2009/12/ubuntu-backup-with-rsync.html">the rsync commands</a> I wanted to use; now it was a matter of running them automatically at certain times or on certain days.  I began by seeing what was already scheduled in my crontab (i.e., my chronological table).  Actually, I had two of them:  one for me, and one for the root (i.e., administrator).  I checked them with "crontab -l" (that's a small L) and "sudo crontab -l" and both say "no crontab."  This <a href="https://web.archive.org/web/20190906053752/http://ubuntuforums.org/showpost.php?p=5749808&amp;postcount=2">supposedly</a> meant that there were no crontab files in /var/spool/cron/crontabs.  I verified that via "sudo nautilus."  It seemed like that would apply to the root's cron, but I wasn't able to find any different location where the user's cron should be, so I just moved on to the next step.<br/>
<br/>
The next step was to edit the crontab by using "crontab -e."  This seemed to be creating a crontab for me, as distinct from root:  it said "no crontab for ray - using an empty one."  To confirm that, I tried in a separate Terminal session with "sudo crontab -e."  It seemed to flash the same choice as had appeared for me, showing a choice of editors; but then it went directly into nano, which the other Terminal session was describing as the "easiest" of the three available editors.  So, OK, since I ordinarily ran my rsync backups as me, user, not as root, I figured I would want to set up my own crontab, not a root crontab.  (Later, I found <a href="https://web.archive.org/web/20190906053752/http://swiss.ubuntuforums.org/showpost.php?p=7539892&amp;postcount=4">some statements</a> that it was a bad idea to edit root's crontab.)  So I killed that nano session and went back to the first Terminal session.  There, I chose no. 3, nano, as my editor.<br/>
<br/>
The top of the nano screen was showing me "# m h  dom mon dow   command."  This was my cue for <a href="https://web.archive.org/web/20190906053752/http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/">the things that I needed to enter</a> on a line, in order to schedule a cron job:  minute, hour, day of month, month, day of week, and command.  (The leading # was to indicate that this sample line was just a comment and should not be executed.) <br/>
<br/>
According to <a href="https://web.archive.org/web/20190906053752/http://linux.about.com/od/commands/l/blcmdl5_crontab.htm">About.com</a>, up through the week level, permissible values began at zero:  that is, minutes of the hour ran from 0 to 59, hours of the day ran from 0 to 23, and days of the week ran from 0 to 7 (where Sunday was both 0 and 7, as you prefer).  Beyond that, days of the month ran from 1 to 31, and months of the year ran from 1 to 12.  If they had names, you could use their first three letters (e.g., "Mon" and "Jul" but not "minute 23"). Cron uses the union (not the intersection) of the two day commands.  That is, if you specify a day of the week (e.g., Fri) and also a day of the month (e.g., 15), the command will run on both days (e.g., every Friday, and also the 15th of every month).  You could use an asterisk to indicate "every"; for example, * * * * * would indicate that you want to run the command every minute of every hour of every day of every month.<br/>
<br/>
There were additional options for numbers below the date level; that is, these wouldn't work on days of the week or of the month.  One of these options was to use fractions:  for instance, */4 would mean "every fourth" minute or hour or whatever.  You could also use a range:  40-45 would mean it should run every minute of the hour from 40 to 45 minutes (i.e., 12:40 AM, 12:41 AM, 12:42 AM . . . 12:45 AM, 1:40 AM . . . 11:45 PM).  You could use lists, separating items with commas, so that 40,41 would mean that it should run only on the 40th and 41st minutes of the hour. So designating the hour as 0-11/2 would mean that it should run every other hour, in the morning only.  You could use a list of ranges; for example, an hour designation of 0-1,10-11 would indicate that the command should run in the first two and also in the last two hours of the morning.  Range and list commands start on the first number; for instance, 2-6/2 runs at 2 AM, 4 AM, and 6 AM (at whatever minute you specify).<br/>
<br/>
There was one other category of entry:  <a href="https://web.archive.org/web/20190906053752/http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/">special words</a>.  These words would replace all five numbers.  In other words, if you wanted the precise control offered by the numbers for minute, hour, etc., use the numbers; but if you want the convenience of just entering one word without having to think much about what it means, use the word.  These special words were @reboot (run at reboot), @yearly or @annually (once a year), @monthly, @weekly, @daily or @midnight (run once a day), and @hourly.  These all run as soon as the time period starts (e.g., January 1, 12:00 midnight).  There was more to know about these commands, in the <a href="//web.archive.org/web/20190906053752/https://www.google.com/search?hl=en&amp;safe=off&amp;rlz=1B3GGGL_enUS318US318&amp;num=50&amp;newwindow=1&amp;q=cron+ubuntu&amp;btnG=Search">official documentation. </a><br/>
<br/>
I decided the first thing to schedule was a backup of my CURRENT partition to a backup internal hard drive.  I wanted this backup to run several times a day.  I hadn't set it up as a RAID array because I didn't want it to happen immediately; I wanted to allow some time in case I accidentally deleted something, or made some other stupid mistake.  The more frequently it ran, the more likely it would contain the most recent version of the relevant folder - which could mean it would be more likely to have the version that existed *after* my stupid mistake.  My compromise was to set it up to run every two hours.  The cron line I used, then, was this:<br/>
<br/>
0   */2   *   *   *   [<a href="https://web.archive.org/web/20190906053752/http://raywoodcockslatest.blogspot.com/2009/12/ubuntu-backup-with-rsync.html">rsync command</a>]<br/>
<br/>
In crontab, I put several spaces between the numbers for readability.  Here, in this blog posting, I had to use <a href="https://web.archive.org/web/20190906053752/http://webdesign.about.com/od/intermediatetutorials/qt/tiphtmltab.htm">nonbreaking spaces</a> for the display shown above, because plain old spaces tend to get ignored in HTML.  I haven't reproduced, here, the long command that I want executed, because I want to focus on the cron parts of the line.  (The rsync command of choice is shown in <a href="https://web.archive.org/web/20190906053752/http://raywoodcockslatest.blogspot.com/2009/12/ubuntu-backup-with-rsync.html">the previous post</a>.)<br/>
<br/>
Then it occurred to me that, instead of putting that long command in cron, where I would have to do some minor translation every time I wondered what it meant, I could probably write a basic Ubuntu shell script that would do the same thing and would allow me to add explanatory notes and other commands.  So I took a brief detour into <a href="https://web.archive.org/web/20190906053752/http://raywoodcockslatest.blogspot.com/2009/12/basic-ubuntu-bash-shell-scripts.html">the land of scripts</a>.  By the time I returned and finished my look at rsync, I had two scripts.  One was called backup-hour.sh, to be run every few hours.  The other was called backup-day.sh.  I put them into /home/ray/bin and wrote the following cron lines for them:<br/>
<br/>
0   */2   *   *   *   ./home/ray/bin/backup-hour.sh<br/>
<br/>
0   2   *   *   *   ./home/ray/bin/backup-day.sh<br/>
<br/>
The first one would hopefully run backup-hour.sh every two hours, all day and all night.  The second one was intended to run backup-day.sh every day at 2 AM.<br/>
<br/>
To put these lines into crontab, I typed crontab -e.  It all looked good.  But nothing was happening.  A couple of days went by, and cron didn't run.  The problem, I suspected, was with those periods I had put at the start of my path names.  I had thought that was part of a command, but nobody else was using them in their cron files.  So I deleted those and waited until the next even-numbered hour, to see if backup-hour.sh would run.<br/>
<br/>
Then I wondered whether I was saving crontab in the right place.  I noticed that nano, my default crontab editor, was saving it to /tmp/crontab.zfItNF/crontab.  Somehow, that didn't look right.  I did a <a href="//web.archive.org/web/20190906053752/https://www.google.com/search?hl=en&amp;q=%22where+is+crontab%22+ubuntu&amp;sourceid=navclient-ff&amp;rlz=1B3GGGL_enUS318US318&amp;ie=UTF-8">quick search</a> and found <a href="https://web.archive.org/web/20190906053752/http://www.linuxforums.org/forum/linux-applications/136875-where-crontab-located.html">a variety of theories</a> on where crontab should be, and none of them involved the /tmp folder.  Someone suggested typing "which crontab" at the prompt.  That came back with /usr/bin/crontab, which wasn't one of the options those other people had suggested.  I tried to save this crontab to /usr/bin/crontab and got a message that the file already existed.  I tried "gedit /usr/bin/crontab," but even with sudo I got a message that the file could not be opened.  I decided to pass on that one for the time being and, selecting a seemingly knowledgeable opinion, I thought about saving it in /var/spool/cron.  It turned out that there was a subdirectory there, and more specifically we had a file called /var/spool/cron/crontabs/ray.  When I looked in that, I saw a copy of my crontab file, the one that nano had been trying to save in a /tmp folder, except that it began with the line, "DO NOT EDIT THIS FILE - edit the master and reinstall."  So it seemed that maybe nano knew what it was doing after all.  So I let nano save crontab in that /tmp folder after all.  Then, following some advice, I decided to output the error messages, if any, to a crontab.log file.  So the first complete line in my crontab looked like this:<br/>
<br/>
0 */2 * * * /home/ray/bin/backup-hour.sh 2&gt;&gt; /Folder1/crontab-errors.log<br/>
<br/>
Unfortunately, at 4:00 PM, nothing happened.  I decided to follow <a href="https://web.archive.org/web/20190906053752/https://help.ubuntu.com/community/CronHowto">the suggestion</a> that it is much easier to use the <a href="https://web.archive.org/web/20190906053752/http://www.webupd8.org/2009/05/schedule-tasks-in-gnome-linux-using.html">gnome-schedule</a> package (though there were <a href="//web.archive.org/web/20190906053752/https://www.google.com/search?hl=en&amp;safe=off&amp;client=firefox-a&amp;rlz=1R1GGGL_en___US333&amp;hs=iXB&amp;num=50&amp;newwindow=1&amp;q=gnome-schedule+9.10+OR+karmic+bug&amp;btnG=Search">problems</a> for those who upgraded from Ubuntu 9.04 to 9.10 rather than doing a fresh install), so I installed that in Synaptic.  This gave me a new option at Applications &gt; System Tools &gt; Scheduled Tasks.  (Scheduled Tasks was apparently a simple front end for cron.)  But before Scheduled Tasks would work, I had to <a href="https://web.archive.org/web/20190906053752/http://gaute.vetsj.com/2009/02/20/how-to-figure-out-if-crontab-and-at-is-correctly-set-up/#more-138">make sure</a> that crontab and a program called At were installed.  Both were marked as installed in Synaptic.  Cron was for recurrent tasks, and At was for one-time jobs (e.g., run this "At" startup).<br/>
<br/>
The basic idea, <a href="https://web.archive.org/web/20190906053752/http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5562494&amp;postcount=5">it developed</a>, was that crontab -e would add scheduling files to the /var/spool/cron/crontabs folder, but it was apparently advisable to just let crontab -e do that, and not try to find and edit those files directly.  I tried typing "sudo /etc/init.d/cron restart," but that gave me a suggestion:  "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service cron restart."  So, OK, I tried that.  This gave me a long message that started with "restart: Rejected send message."  That didn't sound good, so I tried "ps -eaf | grep cron" and that gave me these three lines:<br/>
<br/>
ray       8381  8343  0 19:46 pts/0    00:00:00 man 5 crontab<br/>
root      8409     1  0 19:50 ?        00:00:00 cron<br/>
ray       8416  8343  0 19:52 pts/0    00:00:00 grep --color=auto cron<br/>
<br/>
When I had tried running that command previously, I had gotten only the second and third lines, not the first.  So perhaps the problem had been that my cron had not been running when I had tried to run it previously, and now it was running.  On that assumption, I could have just gone back to the command-line approach at this point, but I liked the added option of using At to schedule one-time events. But as I checked further, "crontab -l" said "no crontab for ray," so apparently crontab was *still* not running.  But no, <a href="https://web.archive.org/web/20190906053752/http://gaute.vetsj.com/2009/02/20/how-to-figure-out-if-crontab-and-at-is-correctly-set-up/#more-138">one source</a> said, "The output: no crontab for [username] means crontab is installed."<br/>
<br/>
I found <a href="https://web.archive.org/web/20190906053752/http://joeb454.ubuntuforums.org/showthread.php?t=102626">a long thread</a> that told me I could use gedit instead of nano, to edit crontab, by typing this:<br/>
<br/>
export EDITOR=gedit &amp;&amp; crontab -e<br/>
<br/>
(The "&amp;&amp;" part combined separate commands; apparently I could have achieved the same thing by typing these two on separate lines.)  Someone said I could make this permanent by putting the command in my .bashrc file, which <a href="https://web.archive.org/web/20190906053752/http://mail-index.netbsd.org/port-arm32/1997/09/19/0009.html">they said</a> I would find in /home/ray, which was true.  But if .bashrc hadn't been there, apparently I could have used gedit to create it, with something like this:<br/>
<br/>
# .bashrc - bash config file # <br/>
# export variables<br/>
export EDITOR=gedit<br/>
<br/>
Since .bashrc was already there, I just added those last two lines to the end of it.  But anyway, back at the cron issue, someone in that long thread said I could change my cron line to look like this:<br/>
<br/>
* * * * * export DISPLAY:=0 &amp;&amp; xterm [command]<br/>
<br/>
if I wanted to see something on the screen when the command was executing.  But this got me back to the realization that, for all of the flexibility I was seeing as I worked my way through page 9 of that very long thread, I would probably prefer, right now, to just get something working.  So I guessed that Scheduled Tasks would work just fine if plain old crontab was working.  So, as others had done, I wrote up a simple command to test crontab.  The entry looked like this:<br/>
<br/>
* * * * * export DISPLAY:=0 &amp;&amp; xterm dir<br/>
<br/>
Sadly, this did nothing.  I opened Scheduled Tasks, thinking I would try something similar there, and instead I saw that my crontab line was already there, albeit in ugly form: <br/>
<br/>
Recurrent    At every minute     export DISPLAY:=0 &amp;amp&amp;amp dir<br/>
<br/>
Anyway, that didn't seem to be running, so I deleted it, in Scheduled Tasks, and tried doing similar as a one-time task.  Here's what I ran:<br/>
<br/>
dir &gt; /home/ray/DIRDIRDIR<br/>
<br/>
and it worked!  I got a text file named DIRDIRDIR that contained a directory listing.  So it seemed the one-time part of Scheduled Tasks was working properly.  So I returned to the question of recurrent tasks.  I remembered that, in Ubuntu, we use "ls" rather than "dir."  So in Scheduled Tasks, I used more or less the same command to append updated directory listings each minute, showing the time when DIRDIRDIR had been last updated:<br/>
<br/>
ls -l &gt;&gt; /home/ray/DIRDIRDIR<br/>
<br/>
and that worked too.  So now I felt I should try again with the lines I had attempted earlier, as revised.  This time, I entered them into Scheduled Tasks rather than into crontab, so I didn't need the * * * * * parts of the entries.  So here are the commands I entered in Scheduled Tasks:<br/>
<br/>
/home/ray/bin/backup-hour.sh 2&gt;&gt; /Folder1/crontab-errors.log<br/>
/home/ray/bin/backup-day.sh 2&gt;&gt; /Folder1/crontab-errors.log<br/>
<br/>
I didn't actually enter them both right away; I started with the first one, and made it run just once, at nine minutes past the hour (which was about two minutes ahead of when I was working on it).  When the time came, it ran, or it seemed to:  there was now a file named "crontab-errors.log" with 0 bytes in Folder1.  That was good enough for now.  I tried another line, this time telling Scheduled Tasks to make it an "X application" rather than "Default behavior."  That didn't seem to do anything, but whatever.  It looked I had what I needed, and I could add more knowledge later.</p>
<div style="clear: both;"></div>
</div>

---
### Comments

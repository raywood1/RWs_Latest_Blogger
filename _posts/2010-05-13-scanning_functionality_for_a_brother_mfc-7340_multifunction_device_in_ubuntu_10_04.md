---
layout: post
title: "Scanning Functionality for a Brother MFC-7340 Multifunction Device in Ubuntu 10.04"
date: 2010-05-13
---

<div class="post-body">
<p>I had <a href="https://web.archive.org/web/20170208061106/http://raywoodcockslatest.blogspot.com/2010/05/installing-brother-mfc-7340-printer-in.html">installed the printing functionality</a> for a Brother MFC-7340 multifunction device in Ubuntu 10.04 (Lucid Lynx), including a Windows XP virtual machine running in VMware Workstation 7 on that Ubuntu installation.  Now I wanted to set up scanning functionality as well.  This post describes that effort.<br/>
<br/>
I first verified that the scanning functionality was not installed automatically as part of the printer driver.  I went into Ubuntu’s Applications &gt; Graphics &gt; XSane Image Scanner.  (I was not sure whether XSane came with Ubuntu or whether I installed it separately through Synaptic Package Manager.)  XSane said it was “scanning for devices” and then reported that there were “no devices available.”  It occurred to me that this could be because I had connected the printer to the virtual machine, which probably would have made it unavailable for Ubuntu itself.  I went into the virtual machine and selected VM &gt; Removable Devices &gt; Brother Printer &gt; Disconnect.  Then I went back out to Ubuntu and tried again in XSane.  I got the same result.  So it did seem that I would need to install scanner drivers separately.<br/>
<br/>
The <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html">Brother Drivers for Linux webpage</a> did have drivers and instructions for scanners.  I went to the <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html">driver download page</a>, where I found that the MFC-7340 was categorized as a “brscan3” model.  I selected the Debian driver for the <a href="https://web.archive.org/web/20170208061106/http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.9-1.i386.deb&amp;lang=English_sane">32-bit brscan3</a>.  There was also an option to download and install a scan-key-tool.  I wasn’t sure what that was, or if I would need it, so I held off.  The 32-bit brscan3 download gave me a file called brscan3-0.2.9-1.i386.deb.  There were <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html">different installation instructions</a> for USB and ethernet connections.  There was also <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html">a separate webpage</a> for Scanner Settings for Normal Users.  They had an Ubuntu 10.04 option there.  The steps I had to take there were, first, to type “sudo gedit /lib/udev/rules.d/40-libsane.rules” and then add two lines at the end of the, right before the line that began with “# The following rule will disable USB autosuspend for the device.”  The two lines I had to add were:<br/>
<blockquote># Brother scanners<br/>
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"</blockquote>Then I had to save that file and reboot the system.  When that was done, as with the printer configuration, I went through the <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq">Pre-required Procedures</a> that seemed to apply to all versions of Ubuntu generally or to this version (32-bit 10.04) particularly.  Those steps seemed to be as follows:<br/>
<blockquote>sudo -i<br/>
mkdir /var/spool/lpd<br/>
apt-get install sane-utils<br/>
apt-get install psutils</blockquote>I got an error for the mkdir command, as this was a step I had already done – I think when I installed the printer driver.  I already had sane-utils too, and got a message telling me to run “apt-get autoremove” to get rid of some packages that were no longer required, which I did.  I already had psutils as well.  With the Pre-Required Procedures out of the way, I was ready to follow the <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html">USB installation instructions</a> for the scanner driver.  Having already downloaded the driver and connected the MFC-7340’s USB cable, I navigated to the folder where I had put the download and then typed this:<br/>
<blockquote>dpkg -i --force-all brscan3-0.2.9-1.i386.deb<br/>
dpkg -l | grep Brother</blockquote>This all seemed good.  I started XSane, adjusted its settings, and scanned.  It worked with the automatic sheet feeder.  It saved in multiple formats, including JPG and PDF.  I tried scanning while standing at the scanner and punching the buttons on the MFC-7340.  That didn’t work.  That, then, was what the scan-key-tool driver was for.  From <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html">the download page</a>, I got the 32-bit Debian brscan3 <a href="https://web.archive.org/web/20170208061106/http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb&amp;lang=English_lpr">scan-key-tool driver</a> (brscan-skey-0.2.1-3.i386.deb) and looked at the <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html">installation instructions</a>.  They said I needed GIMP, which I already had installed (I think it came with Ubuntu), and that I also needed to have installed the scanner driver already, which I had done.  That took care of the Pre-Required Procedures.  Now, as above, I navigated to the folder where I had put the download and entered more or less the same commands as with the scanner driver, plus a couple of additional steps:<br/>
<blockquote>dpkg -i --force-all brscan-skey-0.2.1-3.i386.deb<br/>
dpkg -l | grep Brother<br/>
brscan-skey<br/>
brscan-skey -l</blockquote>Following <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html">their additional instructions</a>, I set the scan-key-tool to run automatically when I started the computer, by going into System &gt; Preferences &gt; Startup Applications &gt; Add (suggested name = Brother Scan Key, command = brscan-skey, comment = Scan from the MFC-7340 console).  I scanned from the console.  The resulting file was saved in /root/brscan, probably because I had run all of these commands as root (i.e., sudo).  I ran brscan-skey again from my normal user (i.e., not root) prompt.  This time, I saved to Image rather than to File.  This provoked GIMP to start up and display the scan.  I saw that, again, it was saving the scans to /root/brscan (though I could only see them when I went there as root).  I changed the file name and location to a PDF in my preferred folder for scans, but GIMP was not prepared to do PDFs, so that was apparently an advantage of saving as File rather than as Image.  I tried again with GIMP, this time as a JPG to my preferred folder.  That worked, but the scankey was still saving copies of them to /root/brscan too.  The instructions said I could type “brscan-skey -u” to change the target user, so I did that as root, and then typed brscan-skey as myself.  Unfortunately, that didn’t do it; it was still saving in /root.  I tried “sudo brscan-skey -t” to stop it altogether.  That worked.  Now it wouldn’t scan from the console.  I started it as myself again.  Now it was saving to /home/ray/brscan.<br/>
<br/>
The next step I wanted to take, following their additional instructions, was to modify the default script for scan-to-image so that it would save in my preferred folder as a JPG, and scan-to-file so that it would save there as a PDF.  Brother suggested changing this line in the default scantoimage script:<br/>
<blockquote>scanimage --device-name "$device" --resolution $resolution &gt; $output_file</blockquote>to this:<br/>
<blockquote>scanimage --device-name "$device" --resolution $resolution | pnmtops | gs -q -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=- - &gt; $output_file.pdf</blockquote>To edit the default script for the scanner's Image option, I typed this:<br/>
<blockquote>cd /usr/local/Brother/sane/script<br/>
ls<br/>
sudo gedit scantoimage-0.2.1-3.sh</blockquote>Once I was in the scantoimage script, I decided to change several things, including increasing the resolution to 300.  Now, unfortunately, the script didn’t work.  After I punched the Start button on the scanner, it just sat there for a moment, and then gave a long beep and a “sane_read: Error during device I/O,” and a tiny brscan.XXXXX file would appear in /home/ray; and when I opened that file, it was all black; or if I restored the line about echoing the output to gimp, it said this:<br/>
<blockquote>GIMP message<br/>
Opening ‘/home/ray/brscan/brscan.3bq3GA failed: PNM Image plug-in could not open image</blockquote>and then gave up.  Weird thing is, I couldn’t get it to function normally, even when I restored scantoimage-0.2.1-3.sh to what I thought was its original condition.  I stopped and restarted brscan-skey (i.e., stop with brscan-skey -t); still the same thing.  I restarted the computer and, at the same time, shut down and then restarted the printer.  Having set brscan-skey to start automatically with Ubuntu, I went right to the console and tried again.  Now it scanned.  Maybe I had needed to completely kill brscan-skey after a bad edit.  I edited scantoimage-0.2.1-3.sh again, this time making just one change and then testing it.  Everything was fine until I got to the part where I made <a href="https://web.archive.org/web/20170208061106/http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html#Inst7">the recommended change</a> to the actual scanimage line in the script.  Then, once again, the scanner just started the scan and then froze.  Eventually it reset itself.  I tried again, but now it was just waiting for a few seconds and then giving me that long beep and not even trying to scan.  I commented out their recommended change and restored the way it was originally, saved, and tried again.  Still just the long beep.  So I typed this<br/>
<blockquote>kill -9 `pidof brscan-skey-0.2.1-3`<br/>
brscan-skey</blockquote>(note:  those are backticks, not single quotation marks) and then tried scanning again, but still the long beep and the error.  Turning the printer off for 30 seconds and then back on after killing brscan-skey did the trick.  I played some more and got the long beep and error again.  This time, I didn’t turn the printer off; I just killed brscan-skey and waited for the printer to reset itself.  That worked too.  After more searching, I found what looked like it might be an answer in Stutz’s <a href="https://web.archive.org/web/20170208061106/http://www.scribd.com/doc/2205923/The-Debian-Linux-Cookbook-Tips-and-Techniques-for-Everyday-Use">Debian Linux Cookbook</a> (pp. 286-287), which said this:<br/>
<blockquote>scanimage outputs images in the PNM (“portable anymap”) formats, so make sure that you have the `netpbm’ package (installed on most Linux systems by default); it’s a useful collection of tools for converting and manipulating these formats.</blockquote>Well, Synaptic told me that I did not have netpbm installed.  I installed it, using Synaptic.  I observed that a list of devices (produced by “echo 'devicenames == ' | gs -q | tr " " "\n" | sort”) contained pnm but not the pnmtops device used in Brother’s command.  Pnmtops did appear to be <a href="https://web.archive.org/web/20170208061106/http://manpages.ubuntu.com/manpages/lucid/en/man1/pnmtops.1.html">in Ubuntu 10.04</a>; it just didn’t appear to be on my system.  So I changed that too.  About this time, I discovered that Ubuntu had probably been giving me error messages in Terminal after each try, but Terminal tended to be buried under other windows.  So now I got this error:<br/>
<blockquote>scanimage: sane_read: Error during device I/O<br/>
scanimage: received signal 13<br/>
scanimage: trying to stop scannerSegmentation fault</blockquote>So I changed it back to pnmtops.  This time, I got an additional error, after the “scanimage: sane_read: Error during device I/O” message:<br/>
<blockquote>pnmtops: warning, image too large for page, rescaling to 0.691703<br/>
pnmtops: writing color PostScript...<br/>
pnmtops: EOF/error reading 1 byte sample to file.</blockquote>It looked like <a href="https://web.archive.org/web/20170208061106/http://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;safe=off&amp;client=firefox-a&amp;rlz=1R1GGGL_en___US333&amp;q=pnmtops+%22error+reading+1+byte+sample+to+file%22+daterange%3A0-2455329&amp;btnG=Search">almost nobody</a> had gotten that EOF/error message.  Not a good sign!  The rescaling part <a href="https://web.archive.org/web/20170208061106/http://manpages.ubuntu.com/manpages/lucid/en/man1/pnmtops.1.html">did not seem</a> to be a problem.<br/>
<br/>
Around this point, I realized that I had been trying to set the scanner’s Image option to produce PDFs, when I had originally wanted to do that via the File option.  I didn’t know whether I would have any better luck editing scantofile-0.2.1-3.sh than I had had with scantoimage-0.2.1-3.sh, but I decided to try.  I was puzzled that <a href="https://web.archive.org/web/20170208061106/http://manpages.ubuntu.com/manpages/karmic/en/man3/mktemp.3.html">the Ubuntu Manual</a> said, “Never use mktemp().”  I tried their recommended alternative of mkstemp, but bash did not seem to recognize it.  After some additional playing around, I came up with this working script:<br/>
<blockquote>#! /bin/sh<br/>
<br/>
#   $1 = scanner device<br/>
#   $2 = friendly name<br/>
#   <br/>
#   Resolutions:  100,200,300,400,600<br/>
<br/>
resolution=300<br/>
device=$1<br/>
sleep 0.01<br/>
output_file="/media/DATA/Current/Scan_`date +%Y%m%d-%H%M%S`.pdf"<br/>
<br/>
scanimage --device-name "$device" --resolution $resolution | pnmtops | gs -q -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=- - &gt; $output_file<br/>
<br/>
chmod 644 $output_file</blockquote>This script would name each PDF by its date and time, so that they would sort in the correct order in Nautilus or in Windows Explorer.  I think netpbm had to be installed (above) for this to work.  This script changed a number of things in the Brother script, including notably the filename and location.<br/>
<br/>
I took these changes to the scantoimage script as well.  That script would normally output <a href="https://web.archive.org/web/20170208061106/http://en.wikipedia.org/wiki/Netpbm_format">a PPM file</a>, so I added a <a href="https://web.archive.org/web/20170208061106/http://netpbm.sourceforge.net/doc/pnmtojpeg.html">pnmtojpeg conversion line</a> to produce an output file in the better-known JPG format, for maximum compatibility with various browsers and other programs.  I set quality to 95 because, in a brief test, the resulting JPG was half the size of one set to 100.  I included a slight bit of smoothing to make the file slightly smaller and better-looking, without blurring sharp lines.  I put this JPG file into a Lossy folder, to distinguish it from a parallel process in which I used the scanner’s PPM output to create a <a href="https://web.archive.org/web/20170208061106/http://netpbm.sourceforge.net/doc/pnmtopng.html">lossless PNG version</a>, in case I needed maximum quality.  After the scanning session, I could then easily get rid of all unnecessary copies by deleting either the Lossy or the Lossless folder (or by mixing their contents as needed).  The resulting, working scantoimage script was as follows:<br/>
<blockquote>#! /bin/sh<br/>
#<br/>
#   $1 = scanner device<br/>
#   $2 = friendly name<br/>
#   <br/>
#   Resolution options:  100,200,300,400,600<br/>
<br/>
resolution=300<br/>
device=$1<br/>
sleep 0.01<br/>
dir_name="/media/DATA/Current/"<br/>
file_name="Scan_`date +%Y%m%d-%H%M%S`"<br/>
<br/>
ppm_file=$dir_name$file_name".ppm"<br/>
scanimage --device-name "$device" --resolution $resolution &gt; $ppm_file<br/>
<br/>
mkdir $dir_name"Lossy"<br/>
jpg_file=$dir_name"Lossy/"$file_name".jpg"<br/>
pnmtojpeg --quality=95 --smooth=10 $ppm_file &gt; $jpg_file<br/>
<br/>
mkdir $dir_name"Lossless"<br/>
png_file=$dir_name"Lossless/"$file_name".png"<br/>
pnmtopng $ppm_file &gt; $png_file<br/>
<br/>
# Change, comment, or delete the next line, depending on which<br/>
# file (if any) you want to open in GIMP<br/>
rm $ppm_file<br/>
<br/>
# Uncomment the next line if you want the file to open in GIMP<br/>
# echo gimp $output_file \;rm -f $output_file | sh &amp;</blockquote>As with the printer setup, the final question was whether I could use the MFC-7340 from within a Windows XP virtual machine on VMware Workstation 7.  I went into a virtual machine, opened Adobe Acrobat, and entered the commands to scan.  It did not see any scanning devices.  I cancelled out of that and went to VM &gt; Removable Devices &gt; Brother Printer.  I saw that there was no “Brother Scanner” option, so this did not look good.  I clicked on Connect anyway, to connect the printer, and went back to Acrobat.  But that made the difference:  now it saw both TW-Brother MFC-7340 and WIA-Brother MFC-7340.  I usually used the latter, so I went with that.  I went through all the other normal steps to make a scan.  Unfortunately, Acrobat crashed.  It had been doing that anyway in that virtual machine, so I couldn’t infer anything for sure from that.  I tried again.  This time, Acrobat sat there for several minutes with the “Transferring data...” dialog open and then finally said, “Scanning canceled.”  I tried again, this time using the Twain (TW-Brother MFC-7340) option.  It said, “Reading from the device.”  It got as far as 0% Completed, and it hung there.  After maybe 10-15 minutes, I canceled it.  Apparently scanning would not be happening from within the virtual machine.  Otherwise, though, it appeared the project was complete.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**zinc losangeles**:
Thanks Ray.I'm always having to revisit the Brother website, download software for my MFC-4800 after we upgrade or re-install Ubuntu.  Your write-up is very thorough and cuts through a lot of the information about Xsane.

**mikeferris**:
Ray - thanks for the thorough instructions.  I have the printer working,and am about to try to set up the scanner function.  In your instructions, you often say "navigate to the folder containing . . .".  As a novice terminal user, I have no idea what that means. Clearly, my downloads from the Brother website are in my Downloads folder.  I know how to get there in the GUI display, but how do I "navigate" there in terminal mode?

**raywood**:
Mike -- try these guides:http://www.google.com/search?sourceid=navclient&ie=UTF-8&rlz=1T4SKPB_enUS361&q=ubuntu+terminal+commands+navigate+folder+OR+directory

**mikeferris**:
Ray - thanks for the help.  I "navigated" to the Downloads folder where I had put the drivers, but here's what I got when trying to use the dpkg command:mike@mike-desktop:~$ cd Downloadsmike@mike-desktop:~/Downloads$ dpkg -i --force-all brscan3-0.2.11-2.i386.debdpkg: operation requires read/write access to dpkg status areamike@mike-desktop:~/Downloads$Don't know how to deal with "access to dpkg status area".  Any help would be appreciated.Thanks!

**raywood**:
Try this search:http://www.google.com/search?sourceid=navclient&ie=UTF-8&rlz=1T4SKPB_enUS361US393&q=ubuntu+privileges+sudoUbuntu privileges mystify me somewhat.  First time a command doesn't work, press the Up arrow (so you don't have to retype it) and then the Home key (to go to the start of the line) and prefix it with "sudo" -- like, in your example, the command should start with "sudo dpkg."  (I think "sudo" is short for "superuser do.")  See if that fixes it.

**mikeferris**:
Thanks, Ray.  The sudo prefix worked fine, and the scanner functions of my MFC-7340 are now all enabled.I'm a bit surprised that the XSane program doesn't do a better job of correctly sizing a scanned text document.  "Simple Scan" at least gets the size right.But most of my scanning work is going to be done with photos anyway.  I'll probably start in GIMP, call up xSane from there, which allows the scan to go directly into a GIMP layer ready for cropping.  Then I'll save the cropped photo to JPEG, and drag it into F-Stop. (Too bad the scanner can't be accessed directly from the photo manager.  F-Stop can recognize a camera . . . why not allow it to find a scanner?  Perhaps an idea for future development!)Anyway, thanks again for all your help.Mike

**raywood**:
Glad I could help.  Incidentally, you may want to consider IrfanView for some of your editing.  See http://raywoodcockslatest.blogspot.com/2009/07/installing-and-using-irfanview-for.htmlGood luck!

**Rick**:
Thanks for the very detailed and accurate directions.  You likely saved me many hours of work.  I followed your directions, and it worked THE FIRST TIME!

**Zane Jocelyn Chua**:
Thanks mate :) Great information you have here Needed some modifying to get your script to work but the general idea is still there. Love how i don't have that annoying GIMP pop up everytime now!

**Anonymous**:
I thought I'd mention a detail I discovered when setting up my own machine.  The -u option for brscan-skey is not meant for setuid() or to define the home folder that the daemon will scan to, but rather what name the daemon registers itself as to the printer.That is to say, what name shows up in the PC list when scanning using the device's console.It doesn't align with traditional flag meanings for Linux-based daemons, so it is understandable where this confusion would come from.


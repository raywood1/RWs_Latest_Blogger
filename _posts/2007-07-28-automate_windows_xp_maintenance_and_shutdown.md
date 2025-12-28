---
layout: post
title: "Automate Windows XP Maintenance and Shutdown"
date: 2007-07-28
---

<div class="post-body">
<p>Using Notepad, copy the following text and paste it into a file named PowerDown.bat.  Double-click on it to run it.  Better -- put it in a folder somewhere and create a shortcut to it.  If you like it, please post a kind comment on this webpage.

***************************************

:: PowerDown.bat
:: by Ray Woodcock

:: Please post a kind word on my blog:
::      Ray Woodcock's Latest
:: This item posted on July 28, 2007

echo off
cls
:Menu1
echo.
echo What would you prefer?
echo.
echo 1   Power Down
echo 2   Hibernate (if available on your computer)
echo 3   Restart
echo 4   Maintenance
echo 5   Nothing Further (Exit)   
echo.
echo.
echo Note:  Ctrl-Break provides an emergency exit.
echo.
echo.
echo.
echo Choose a number and hit Enter ...
echo.
echo.
echo.
set /p x1=
cls

set x1=%x1:~0,1%
if "%x1%"=="1" goto PowerDown
if "%x1%"=="2" goto Hibernate
if "%x1%"=="3" goto Restart
if "%x1%"=="4" goto Maint
if "%x1%"=="5" goto eof

echo.
echo Not a valid choice.
echo.
goto Menu1

:PowerDown
shutdown -s -f -t 15
goto Undoit

:Hibernate
shutdown -h -f -t 15
goto Undoit

:Restart
shutdown -r -f -t 15
goto Undoit

:Maint
echo.
echo What kind of maintenance would you like?
echo.
echo 1   Run System File Checker
echo 2   Fix file system errors (/f)
echo 3   Recover bad sectors (/r)
echo 4   Defragment all drives
echo 5   Previous Menu
echo.
echo Choose a number and hit Enter ...
set /p x1=
cls

set x1=%x1:~0,1%
if "%x1%"=="1" goto SFC
if "%x1%"=="2" goto FixErrors
if "%x1%"=="3" goto BadSectors
if "%x1%"=="4" goto Defrag
if "%x1%"=="5" goto Menu1

echo.
echo Not a valid choice.
echo.
goto Maint

:SFC
sfc /scannow
echo.
echo System File Checker is now running in a separate process.
echo Meanwhile, you are returning to the main menu in this program.
echo.
goto Menu1

:FixErrors
echo.
echo You will now choose the drives to check.
echo Some will be fixed now.  Most will require reboot.
echo.
pause
cls
echo.
echo Checking drive C ...
echo.
chkdsk c: /f
cls
echo.
echo Checking drive D ...
echo.
chkdsk d: /f
cls
echo.
echo Checking drive E ...
echo.
chkdsk e: /f
cls
echo.
echo Checking drive F ...
echo.
chkdsk f: /f
cls
echo.
echo Checking drive G ...
echo.
chkdsk g: /f
cls
echo.
echo Checking drive H ...
echo.
chkdsk h: /f
cls
echo.
echo Checking drive I ...
echo.
chkdsk i: /f
cls
echo.
echo Checking drive J ...
echo.
chkdsk j: /f
cls
echo.
echo Checking drive K ...
echo.
chkdsk k: /f
cls
echo.
echo Checking drive L ...
echo.
chkdsk l: /f
cls
echo.
echo Checking drive M ...
echo.
chkdsk m: /f
cls
echo.
echo Checking drive N ...
echo.
chkdsk n: /f
cls
echo.
echo Checking drive O ...
echo.
chkdsk o: /f
cls
echo.
echo Checking drive P ...
echo.
chkdsk p: /f
cls
echo.
echo Checking drive Q ...
echo.
chkdsk q: /f
cls
echo.
echo Checking drive R ...
echo.
chkdsk r: /f
cls
echo.
echo Checking drive S ...
echo.
chkdsk s: /f
cls
echo.
echo Checking drive T ...
echo.
chkdsk t: /f
cls
echo.
echo Checking drive U ...
echo.
chkdsk u: /f
cls
echo.
echo Checking drive V ...
echo.
chkdsk v: /f
cls
echo.
echo Checking drive W ...
echo.
chkdsk w: /f
cls
echo.
echo Checking drive X ...
echo.
chkdsk x: /f
cls
echo.
echo Checking drive Y ...
echo.
chkdsk y: /f
cls
echo.
echo Checking drive Z ...
echo.
chkdsk z: /f
cls
goto Summary

:BadSectors
echo.
echo This can be very time-consuming, especially on large drives.
echo Select only those drives that need this now.
echo.
pause
cls
echo.
echo Checking drive C ...
echo.
chkdsk c: /r
cls
echo.
echo Checking drive D ...
echo.
chkdsk d: /r
cls
echo.
echo Checking drive E ...
echo.
chkdsk e: /r
cls
echo.
echo Checking drive F ...
echo.
chkdsk f: /r
cls
echo.
echo Checking drive G ...
echo.
chkdsk g: /r
cls
echo.
echo Checking drive H ...
echo.
chkdsk h: /r
cls
echo.
echo Checking drive I ...
echo.
chkdsk i: /r
cls
echo.
echo Checking drive J ...
echo.
chkdsk j: /r
cls
echo.
echo Checking drive K ...
echo.
chkdsk k: /r
cls
echo.
echo Checking drive L ...
echo.
chkdsk l: /r
cls
echo.
echo Checking drive M ...
echo.
chkdsk m: /r
cls
echo.
echo Checking drive N ...
echo.
chkdsk n: /r
cls
echo.
echo Checking drive O ...
echo.
chkdsk o: /r
cls
echo.
echo Checking drive P ...
echo.
chkdsk p: /r
cls
echo.
echo Checking drive Q ...
echo.
chkdsk q: /r
cls
echo.
echo Checking drive R ...
echo.
chkdsk r: /r
cls
echo.
echo Checking drive S ...
echo.
chkdsk s: /r
cls
echo.
echo Checking drive T ...
echo.
chkdsk t: /r
cls
echo.
echo Checking drive U ...
echo.
chkdsk u: /r
cls
echo.
echo Checking drive V ...
echo.
chkdsk v: /r
cls
echo.
echo Checking drive W ...
echo.
chkdsk w: /r
cls
echo.
echo Checking drive X ...
echo.
chkdsk x: /r
cls
echo.
echo Checking drive Y ...
echo.
chkdsk y: /r
cls
echo.
echo Checking drive Z ...
echo.
chkdsk z: /r
cls
goto Summary

:Defrag
defrag c: /f
defrag d: /f
defrag e: /f
defrag f: /f
defrag g: /f
defrag h: /f
defrag i: /f
defrag j: /f
defrag k: /f
defrag l: /f
defrag m: /f
defrag n: /f
defrag o: /f
defrag p: /f
defrag q: /f
defrag r: /f
defrag s: /f
defrag t: /f
defrag u: /f
defrag v: /f
defrag w: /f
defrag x: /f
defrag y: /f
defrag z: /f
cls
goto Summary

:Summary
echo.
echo Your requested maintenance is complete.
echo If maintenance requires rebooting, you
echo will have that option now.
echo.
goto Menu1

:Undoit
cls
echo.
echo If you want to cancel the reboot/shutdown,
echo please hit Enter, quickly.
echo.
pause &gt; nul
shutdown -a
cls
goto Menu1</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Rahmanic**:
Thanks for the code now i can set the timer and peacefully sleep while listening to songs!!!!!Gr8 work dude

**santeriajack**:
gday mate been looking for one of these? nice. . . . But how do i set the timer??? I press 1 then enter and it shuts down in 10 secs. am i missing some thing? I wouldn't mind being able to set it for an hour or so.cheers

**raywood**:
Santeriajack -- I'm a little rusty.  As I look at it, I think you'll need to change the number after the -t.  Try altering that number and see what happens.

**owen**:
thats it! works a treat cheers.

**Anonymous**:
This code was exactly what I was looking for. Thanks a lot! Beats looking through tons of 30-day trial garbage apps on versiontrackers.com!

**Anonymous**:
really great....except it doesn't work!!!!shutdown never happens...just sits there...tried on several computers....thanks for nothing!

**Anonymous**:
WORKS PERFECT, thanks mate

**lifecycled**:
Nice one, worked first shot. Under XP anyone know how to suppress the System Shutdown window? I have the timer set for two hours but want to leave the screen free for use during that period.

**Anonymous**:
COOOOLLLLLL

**Bruce E. Baby**:
Nice one Ray.  Thanks

**Anonymous**:
Nice job, Ray!

**Anonymous**:
Very, very, useful. Thank you!


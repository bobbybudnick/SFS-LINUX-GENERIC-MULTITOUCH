# SFS-LINUX-GENERIC-MULTITOUCH
Summary
-----
Multitouch - even with support in the hardware and OS it may not function.
This is because developers must include support at the application level as well.
As of this writing support is not included in popular applications such as Retroarch.
This script adds on multitouch support to practically any X11 application.
A script to easily run Retroarch along with the main script is included.
The support script also disables and reenables Easystroke if it is used.

Update
-----
Now working on the current MID configuration.
There are some porting remarks as detailed in the next section.
Finally there is the hybrid script approach.

Proposed
-----
Currently optimized for the 5" waveshare screen at 720x1280 vertical
The script needs to be modified for other touchscreens
There are 3 hangup points
Search for "porting cue" in the script to find these points automatically
1 - automatic screen device detection as you have noted
It searches automatically now for keywords "Touch" and "Waveshare"
You may have to edit this as needed 
2 - screen resolution factor scaling  
Evtest uses a different internal resolution than the screen resolution sometimes
It may use the screen default edid resolution as the internal resolution  
I discovered this by watching the evtest output while touching the screen
You can then find and edit the multiplication factor of your touch vs screen resolution
3 - vertical resolution transformation
The zero zero coordinates are different between evtest and xdotool
So internal vertical resolution is subtracted from the current y point and abs found
You will need to edit the internal vertical replacing 800 with your own

Hybrid
-----
This implementation is more universal   
Allows for touching anywhere first and with the second touch sending a button press
Has the downside of 1 simultaneous button only


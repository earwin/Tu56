# Tu56

Simulation of TU56 DECtape, version 0.1

For the Raspberry Pi and other Linux systems

This unfinished version is operational, but supports only offline mode.
The connection to simh has not yet been implemented.

The TU 56 DECtape had a very fast tape transportation speed for reads and writes of
81-105 inches per second, and an average rotation speed of the reels of 500 rpm.

Start the program with

 ./tu56			    for a 960x464 decorated window
 
 ./tu56 -full		for a full screen window, scaled to your display size

All switches and lights are funktional. Click either in the upper or lower half of a switch.

The following keys can be used to exit from tu56 and close the corresponding window. These keys are
especially useful in full screen mode where no close window button is available.

 - ESC
 - ctrl-C
 - ctrl-Q

**Transport tape in offline mode**

 - The right switch must be in the "local" position.
 - Click and hold the center switch.
 
**Demo of tape copy**

There is a small demo program which demonstates a data transfer between drive 0 and drive1. It is also
a test for the communication between a simulated "host" (the demo program in this case) and tu56.

Start tu56 in background (with the &) using

 ./tu56 &
 
Make sure that both right switches are in the "remote" position (this is the default).
Then start the demo program with

 ./demo
 
There is currently no 2 way communication back from the panel to the "host", because I'm not yet sure
whether I can implement that in a simh DECtape or magtape driver. Therefore, at the moment the demo
just flips the left buttons in the write enable position if required. But the the right buttons needs
to be in the remote position. Otherwise the panel does not listen to a "host".

If you abort the demo program while it's running you might end up with reels spinning forever. Just use

 rm /tmp/tu56status
 
in this case, or start the demo program again and let it go through the complete demo taking
approx. 35 seconds.

"test.c" is easy to understand. If you have a real TU 56 you might want to modify it a bit to make it more
realistic. I would be very interested in a more realistic demo.

**Contributors**

The pictures used to make the animated screen have been provided by David Gesswein
[Online PDP-8 Home Page](https://www.pdp8.net/tu56/tu56.shtml) and Henk Gooijen. Jon Brase
had the idea to use rotational motion blurring for the rotating tape reels.


**The usual disclaimer**

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

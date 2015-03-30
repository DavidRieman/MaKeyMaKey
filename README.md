MaKey MaKey: Flexible
=====================

This is a version of the MaKey MaKey firmware which (will be) updated to include several optional alterations, in a manner which are configurable per input:
* __Key Combos__: Option for up to 3 keys being pressed per input (IE for easily triggering complex hotkeys from the MaKey MaKey).
* __Reverse Polarity__: Option for reverse polarity (IE to trigger keys when an input circuit is _broken_ instead of _grounded_).
* __Capacitive Touch__: Option for inputs to use Capacative Touch (IE so you don't need to be grounded to trigger the MaKey MaKey input).
* Any combination of the above (IE to trigger multiple keys while capacitive touch has been broken).

The goal is to improve the number and types of projects which can be achieved with a simple settings.h adjustment.

Note: Although I've forked the entire sparkfun MM repository, you are probably only interested in the code in the ["makey_makey" folder](./firmware/Arduino/makey_makey).

## Key Combos

Many times, users [have asked for](http://www.makeymakey.com/forums/index.php?topic=5621.0) a MaKey MaKey solution for triggering multiple keystrokes per input.
To use this feature, simply switch to settings.h, and adjust the first 3 columns to configure key combinations as desired.
For instance, setting the first three values in the table to KEY_LEFT_CTRL, KEY_LEFT_SHIFT, 's' means that Control+Shift+S will be sent when the "Up" pin is ungrounded.
One example of where this really helps is driving existing software with the MaKey MaKey, where established hotkeys frequently use those modifier keys.

Note that the 'release' of one pin will cause 'release' of all individual associated keys.
Consider settings where you have two pins bound to (KEY_LEFT_CTRL, KEY_LEFT_SHIFT, 's') and (KEY_LEFT_CTRL, 'o').
Then when you ground both inputs at the same time, you will be simulating 'held' keys of (KEY_LEFT_CTRL, KEY_LEFT_SHIFT, 's', and 'o').
When you release the second input, you will only be simulating hold of (KEY_LEFT_SHIFT, 's'). This is currently by design.

## Reverse Polarity

Sometimes you want to trigger a key or action when a ground is broken rather than acquired.
[One example](http://www.makeymakey.com/forums/index.php?topic=1282.0) would be to make a video game character jump when you physically jump, separating your feet from an input pad.
Turn this option on for the pins you desire.
Use sparingly though; for example, after you step off the input and try to use the computer the MaKey MaKey is attached to, it will still be pretending that key is held because the ground is broken.
If you find yourself in this situation, you can remedy it quickly by regrounding the input while you interact with the PC, or by simply disconnecting the MaKey MaKey.
Note that it will not automatically start with the key being held; you have to complete the circuit at least once first.
This is by design; it gives you time to reprogram the MaKey MaKey without having keys automatically spammed at you, etc.

## Capacitive Touch

TODO: Built this as a Capacitive Presentation Clicker project on CodePlex but will be migrating it into this code base as a simple settings option soon.

Another common request for MaKey MaKey is the ability to trigger it without being grounded.
This implementation is based on the technique described at: http://playground.arduino.cc/Code/CapacitiveSensor.
While this gets the job done, for some unknown reason it turns out to be extremely slow when applied to many inputs.
(I've raised this issue at [the MM forums](http://www.makeymakey.com/forums/index.php?topic=15304.msg17317#msg17317), but so far nobody has conveyed any insight.)
So for now, try to limit how many inputs you place in Capacitive Touch mode.

.

.

Everything that follows here is stock readme from the base repository (maintained for diffing and merging purposes).

.

.

.

MaKey MaKey
===========

[![MaKey MaKey](https://dlnmh9ip6v2uc.cloudfront.net/images/products/1/1/5/1/1/11511-01b_medium.jpg)  
*MaKey MaKey - Standard Kit (WIG-11511)*](https://www.sparkfun.com/products/11511)

Using the MaKey MaKey you can *make* anything into a *key* (get it?) just by connecting a few alligator clips. The MaKey MaKey is an invention kit that tricks your computer into thinking that almost anything is a keyboard. This allows you to hook up all kinds of fun things as an input.

The MaKey MaKey uses high resistance switching to detect when you've made a connection even through materials that aren't very conductive (like leaves, pasta or people). This technique attracts noise on the input, so a moving window averager is used to lowpass the noise. The on-board ATMega32u4 communicates with your computer using the Human Interface Device (HID) protocol which means that it can act like a keyboard or mouse.

Repository Contents
-------------------
* **/Firmware** - Example firmware files
* **/Hardware** - All Eagle design files (.brd, .sch)
* **/Production** - Test bed files and production panel files

Product Versions
----------------

**[WIG-11511](https://www.sparkfun.com/products/11511) - Standard kit, OEM packaging**  
The standard kit includes the MaKey MaKey HID board, alligator clips, jumper wires, and a Mini-USB cable in OEM packaging.

**[WIG-11519](https://www.sparkfun.com/products/11519) - Deluxe kit, OEM packaging**  
The deluxe kit includes everything found in the standard kit along with an additional pack of alligator clips and a roll of copper wire (all in OEM packaging).

**[RTL-11437](https://www.sparkfun.com/products/11437) - Standard kit, retail packaging**  
This kit contains everything found in the standard kit and comes in retail-ready plastic packaging.

License Information
-------------------
The hardware is released under [Creative Commons ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).
The code is beerware; if you see me (or any other SparkFun employee) at the local, and you've found our code helpful, please buy us a round!

Distributed as-is; no warranty is given.

->The MaKey MaKey is a collaboration with JAy Silver and Eric Rosenbaum. You can find more information about them [here](http://www.makeymakey.com/).<-

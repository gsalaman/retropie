# retropie

## Install Notes
Use raspberry pi imager rather than apple pi baker

## Spade connector tips and tricks
So outta the box, the spade connectors for buttons and joysticks are pretty loose.  You can tighten by squeezing with pliers, but this is an art, as if you go too far, you can't get the connector on at all, and then you have to try prying it back apart.

Once I got the feel for it, I did this:
* take the connector before crimping and slide it on to the post.  Confirm it's loose.  Take it back off.
* LIGHT squeeze with pliers towards the bottom
* Retest fit.  Should start going on easy, then stick at the end where you've squeezed it.  May need to squeeze it a little harder, may need to pry it.
* Then crimp to the wire.

## Trackball config
So for those using lr-mame2003, you can hit the tab menu, and then it saves, per game, analog sensitivy.  trying this over a power cycle...and yeah, it works.  Meaning it must be stored in that weird, non-text config file in `~/Retropie/roms/arcade/lr-mame2003/GAME.cfg`

If you are doing both spinner and trackball, one will be mouse 0 and one mouse 1.  I did my plug-in order so that spinner was 0 (for arkanoid and advmame), but then did a rom-specific config file for `input_player1_mouse_index = "1"` for the trackball games.

Finally got this working for at least star wars under FBneo.
Needed to launch from the arcade menu, select emulator FBNeo
Go into options from main manu, settings, input, and turn on "automatic mouse grab"
Next, go to quick menu, controls, port 1 controls and set device type to "mouse, ball only"

So although this works, setting analog sensitivity in star wars doesn't seem to do anything.  :(




## Advmame stuff:
https://retropie.org.uk/forum/topic/9172/advmame-support-for-hotkey-for-emulator-exit/2

By default, tab brings up the input menu, and escape brings up the menu for exiting.  Can use joystick to move up and down, and enter selects.

tab says it's the "config menu", enter "ui select", and esc "ui cancel".

advmame.rc is in /opt/retropie/configs/mame-advmame

format:  
http://www.advancemame.it/doc-advmame#8.9.6

I can get it going by picking a key, doing:
```input_map[ui_end] keyboard[0,q]```
Which would change the q key on keyboard 0 to hit ui_end.  Note that this is gonna be different whether I've got one or two keyboards plugged in, but I think can use the "or" command:
```input_map[ui_end] keyboard[0,q] or keyboard[1,q]```

Okay, the "or" didn't work....but keyboard 0 is the console, so I'm good.

In theory, you should be able to do "input_setting"...but that doesn't seem to work.

Per game binds also aren't happy...doing:
```gt3d/input_map[ui_pause] keyboard[0,space]```
Doesn't crash, but doesn't take...even when I comment out the global.


## PS4 dualshock instructions:
Did this.  Works kinda with one with ds4drv....but second controller not so much.  Gonna try undoing this...
https://retropie.org.uk/docs/PS4-Controller/

Yup...back to normal.  I think I need to be cabled.

## Daphne:
link here:
https://retropie.org.uk/forum/topic/30116/daphne-setup-tutorial-dragon-s-lair-space-ace-etc

https://retropie.org.uk/docs/Daphne/

downloads:  
https://archive.org/details/daphne-g2g


## Misc controls
### Spyhunter
Left stick does back and forth.
Right trigger is accellerator.
Right bumper shifts from L to H
Square does machine guns
O does "accessories"

Options is coins
Select does middle steering button

So, if I wanted to build this:  
Driving wheel, with triggers on fingers and buttons on thumbs.
Accel pedal
Middle button for "start"
"coin" button.

### Tempest
spinner, 2 buttons:  fire, and super-zapper.  Cabinet had spinner right, fire on left (top), super-zapper below.

### Arkanoid
Spinner, one button...fire...but this one has that fire on both left and right

### Star Trek
Spinner, 4 buttons on right.  thrust and fire top and together.  warp below, closer to spinner...and then photons below thrust.  
Start by mapping thrust to l trigger, phasers to r trigger, warp to l bumper, photons to r bumper

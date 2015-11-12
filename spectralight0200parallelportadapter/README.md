## Using a parallel port to drive a SpectraLight 0200 Controller Box.

## **WARNING**

The technique documented on this page works for me.  
  However it has not been extensively tested.  
  This is a "hobby" project that could well damage your mill, controller box and your PC.  
  In fact you might die, hurting the entire time, if you follow these instructions.  
  The author is not responsible for any damage or harm that results from attempting to replicate this project.

These plans are being published so that others can contribute and refine the techniques presented here.  
  The techniques should not be used for anything but research projects. Anyone using these plans does so at their own risk.

These plans should not be used in educational settings.  
  Important safety features of the mill are not implemented.

## Overview  

This adapter enables you to eliminate the need to use the controller card to operate your mill, provided your controller box and mill are operational.  
  Your controller box must be operational for this adapter to be of any use.  

Who might want to do this?  

*   Someone who doesn't have the ISA or PCI controller card but does have the controller box and a mill.  
      There is a good chance that a mill on e-bay does not include the controller card.  
      These cards are reported to cost around $1,000.00.  
      If you don't want to spend $1,000.00 on a card, this project is for you.
*   Someone who has a perfectly working mill, including the controller card, but would like to use alternative controller software such as EMC2, Mach3 or TurboCNC.  
      This adapter will allow you to retrofit your software.

###   
 ![](http://farm5.static.flickr.com/4076/4857275435_850507bf9f.jpg)

## Instructions

What you need:

*   25 pin Male Solder D-Sub connector, qty 1  
      [(link)](http://www.radioshack.com/product/index.jsp?productId=2103239)
*   25 pin Female Solder D-Sub connector, qty 1 [(link)](http://www.radioshack.com/product/index.jsp?productId=2103240)
*   6" lengths of wire suitable for serial communication, qty 10
*   Solder iron and solder supplies
*   30 minutes of time.

Connect the two connectors according to this chart:

Version 2.2

<table border="0">

<tbody>

<tr>

<td>Parallel port (Male)  
</td>

<td>Controller box cable (Female)</td>

<td>Notes  
</td>

</tr>

<tr>

<td>1</td>

<td>22</td>

<td>Enables the spindle</td>

</tr>

<tr>

<td>2</td>

<td>6</td>

<td>X Dir</td>

</tr>

<tr>

<td>3</td>

<td>21</td>

<td>X Step</td>

</tr>

<tr>

<td>4</td>

<td>18</td>

<td>Y Dir</td>

</tr>

<tr>

<td>5</td>

<td>20</td>

<td>Y Step</td>

</tr>

<tr>

<td>6</td>

<td>5</td>

<td>Z Dir</td>

</tr>

<tr>

<td>7</td>

<td>19</td>

<td>Z Step</td>

</tr>

<tr>

<td>8</td>

<td>4</td>

<td>Spindle on/off  
</td>

</tr>

<tr>

<td>13</td>

<td>23</td>

<td>ESTOP (May or may not work, if this causes EMC to stop thinking the button has been pressed at random times, disable it in the stepconf).  
  Placing a 10uf (and possibly much smaller) capacitor in parallel with this signal and grounding it acts as a filter.  
  Problems with this line were resolved using this technique.</td>

</tr>

<tr>

<td>14</td>

<td>17</td>

<td>Mill Amp on/off</td>

</tr>

<tr>

<td>25</td>

<td>7</td>

<td>GND</td>

</tr>

<tr>

<td>--</td>

<td>--</td>

<td>--</td>

</tr>

<tr>

<td>----------------------------------</td>

<td>--------------------------------------------</td>

<td>--------------------------------------------------------------------</td>

</tr>

</tbody>

</table>

 Version 2.1 -> Version 2.2 changes:

Fixed typo in the pin assignment.  
  Pin 24 on the parallel port should have been pin 14\.

Version 2.1  
  (Do not use)

<table border="0">

<tbody>

<tr>

<td>Parallel port (Male)  
</td>

<td>Controller box cable (Female)</td>

<td>Notes  
</td>

</tr>

<tr>

<td>1</td>

<td>22</td>

<td>Enables the spindle</td>

</tr>

<tr>

<td>2</td>

<td>6</td>

<td>X Dir</td>

</tr>

<tr>

<td>3</td>

<td>21</td>

<td>X Step</td>

</tr>

<tr>

<td>4</td>

<td>18</td>

<td>Y Dir</td>

</tr>

<tr>

<td>5</td>

<td>20</td>

<td>Y Step</td>

</tr>

<tr>

<td>6</td>

<td>5</td>

<td>Z Dir</td>

</tr>

<tr>

<td>7</td>

<td>19</td>

<td>Z Step</td>

</tr>

<tr>

<td>8</td>

<td>4</td>

<td>Spindle on/off  
</td>

</tr>

<tr>

<td>13</td>

<td>23</td>

<td>ESTOP (May or may not work, if this causes EMC to stop thinking the button has been pressed at random times, disable it in the stepconf).  
  Placing a 10uf (and possibly much smaller) capacitor in parallel with this signal and grounding it acts as a filter.  
  Problems with this line were resolved using this technique.</td>

</tr>

<tr>

<td>24</td>

<td>17</td>

<td>Mill Amp on/off</td>

</tr>

<tr>

<td>25</td>

<td>7</td>

<td>GND</td>

</tr>

<tr>

<td>--</td>

<td>--</td>

<td>--</td>

</tr>

<tr>

<td>----------------------------------</td>

<td>--------------------------------------------</td>

<td>--------------------------------------------------------------------</td>

</tr>

</tbody>

</table>

Version 2.0 -> 2.1 changes:

*   Prevents the "runaway spindle" situation on my mill.  
      Other users report that this configuration doesn't solve the problem on their mills.

*   Includes an input from the mill for the emergecy stop function.  
      However, the issue [documented here](../strangeplacetoputaclock/) may prevent reliable detection using EMC2.  
      At least one user had reported that it works for them.  
      My advice is to try it, if it works - great.  
      If it doesn't work, disable it in EMC2 and continue on your merry way.

Version 2.0

<table border="0">

<tbody>

<tr>

<td>Parallel port (Male)  
</td>

<td>Controller box cable (Female)</td>

<td>Notes  
</td>

</tr>

<tr>

<td>  
 1</td>

<td>  
 17</td>

<td>  
 Enables the spindle</td>

</tr>

<tr>

<td>  
 2</td>

<td>  
 6</td>

<td>  
 X Dir</td>

</tr>

<tr>

<td>  
 3</td>

<td>  
 21</td>

<td>  
 X Step</td>

</tr>

<tr>

<td>  
 4</td>

<td>  
 18</td>

<td>  
 Y Dir</td>

</tr>

<tr>

<td>  
 5</td>

<td>  
 20</td>

<td>  
 Y Step</td>

</tr>

<tr>

<td>  
 6</td>

<td>  
 5</td>

<td>  
 Z Dir</td>

</tr>

<tr>

<td>  
 7</td>

<td>  
 19</td>

<td>  
 Z Step</td>

</tr>

<tr>

<td>  
 8</td>

<td>  
 4</td>

<td>  
 Spindle on/off  
</td>

</tr>

<tr>

<td>  
 14</td>

<td>  
 7</td>

<td>  
 GND</td>

</tr>

<tr>

<td>  
 15</td>

<td>  
 17</td>

<td>  
 Mill Enable</td>

</tr>

<tr>

<td>  
 ----------------------------------</td>

<td>--------------------------------------------</td>

<td>--------------------------------------------------------------------</td>

</tr>

</tbody>

</table>

[EMC configuration is available here:  
 ](../emc2configuration/)  

Please leave a comment if you attempt this mod with your mill.

Feedback is essential, thanks!

<script type="text/javascript">// <![CDATA[ function deleteComment(id) { if (confirm("Really delete?")) { var f = document.forms["mcc_bottom"]; f.delId.value = id; f.submit(); } } function hideComment(id) { var f = document.forms["mcc_bottom"]; f.hideId.value = id; f.submit(); } function showComment(id) { var f = document.forms["mcc_bottom"]; f.showId.value = id; f.submit(); } function submitComment() { var f = document.forms["mcc_bottom"]; if (f.mcc_name.value == "") { alert("Name is empty"); f.mcc_name.focus(); return; } tinyMCE.triggerSave(); if (f.mcc_text.value == "") { alert("Text is empty"); f.mcc_text.focus(); return; } f.submit(); } tinyMCE.init({ mode : "exact", theme : "simple", elements : "mcc_text", language : "en" }); // ]]></script>

<form name="mcc_bottom" method="post" action=""><input type="hidden" name="post_modulecode" value="meshcmsmodule_bottom"> <input type="hidden" name="delId" value=""> <input type="hidden" name="showId" value=""> <input type="hidden" name="hideId" value="">

<div class="mailform">

<div class="includeitem">

<div class="includetitle">Lessons</div>

<div class="includetext">

Got my harness rigged up this morning, but ironing out some issues at the moment. Busted out the oscilloscope to verify my pinouts are the same as yours, and they are with one exception:

 My X step pin is 21 (vs. 20), and the Y step pin is 20 (vs. 21). This is easily fixed by swapping the outputs in EMC.

 I'm getting the proper direction outputs to the control box, but both X and Y are fixed in one direction, and move in that direction regardless of what direction you toggle it to go. Z works fine. Will update when I have a solution.

 Cheers,

Joel

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon</div>

<div class="includetext">I've changed the diagram to correct the error with the X and Y step pins.  Good catch.</div>

</div>

<div class="includeitem">

<div class="includetitle">Lessons</div>

<div class="includetext">

Got my harness working! Swapped around the 20/21 pins so that I can use the Sherline pinout without modification. This fixed my direction issue as well, since before it was swapping direction on the axis that wasn't running.

I took a different approach on the E-stop and mill enable pins. On my machine, pin 22 is the mill enable. I wired pin 1 on the male to pin 22 on the female, and assigned pin 1 as an amplifier enable pin in EMC. It works out that when you select the 'Toggle Machine On' button in EMC/Axis, the machine turns on; hitting the software e-stop turns the machine back off.

I also wired up the e-stop on the machine, from pin 10 on the male to pin 23 on the female, and assigning pin 10 in EMC as an e-stop in. Tried it out and seemed to work great for me. No issues with the clock pulsing (I had also noticed the clock pulse on pin 17 when Z was being jogged, didn't think much of it till I saw your post).

Only other change is my harness still uses pin 25 on the male to pin 7 on female for ground like your original one did.

Keep up the good work on this!

-Joel

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

<div class="includetext">

That is GREAT news. This mod is so simple that I can't believe we are the first to figure it out and publish it.  

I had actually wired the harness correctly, my documentation was wrong.  Which likely explains why mine worked, it was always wired using the Sherline convention.

Man, I wish my e-stop had worked.  I even put a cap and resister on the line thinking I might be able to filter it out.  No such luck for me.

I may re-adopt the 25 to 7 ground.  It "feels" like the correct configuration.

Ohhh, so THAT is what amplifier enable does.  I switched the configuration of pins 1 and 9 to amplifier enable.  Much better!

Next we will have to tackle spindle speed control.  I have no idea what to expect!

Thanks for all the feedback.

Shannon

</div>

</div>

</div>

<div class="includeitem">

<div class="includetitle">Lessons</div>

<div class="includetext">

SAFETY ISSUE:

If you wired your cable like me, with the mill enable pin wired to some output from the parallel port, there is a serious issue. When the computer is off or booting up, power is applied to the mill enable pin (and spindle) if the controller box is turned on.

From what I can tell,  pin 25 (gnd) shorts to all the pins when power is applied somewhere.

Be careful for now with this. Will post new info when I figure out a solution.

-Joel

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Joel,

I encountered this issue with my first harness.  In that harness I had tied pins 17 & 22 as well as 24 & 25 together.  As you have seen, this causes the mill to "come alive" when it shouldn't.  My solution is to run all signals from the PC to the controller, without any loopbacks.  This is incorporated in the design above (version 2.0).  

-- Shannon

</div>

</div>

<div class="includeitem">

<div class="includetitle">Lessons</div>

<div class="includetext">

Shannon,

I've got no loops in my harness... pin 1 becomes energized on the parallel port side when power is applied to one of the other ports (not sure which one). This only occurs when the computer is off, once linux is up and running the problem is solved.

Fairly confused at this point, so let me know if you've got any insight (some transistor is activated??).

-Joel

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Joel,

Very strange.  Evidently your parallel port ends up in a different state than mine does.  I may well end up making a PCB board to prevent this condition and enable reliable reading of the switches.  I went into this expecting to make a AVR based circuit to handle the stepper timing.  Couldn't believe my luck when the parallel port was up to the task.  How ironic that I may have to rely on a MPU to sort out the handshaking.  

If I design such a circuit I need to first crack control of the spindle speed.  Such a circuit would need to be conprehensive to be worth doing.

A back of the napkin drawing would include IO for the following:

1.  Cover open
2.  Emergency Stop
3.  X / Y / Z limits, one for each direction
4.  X / Y / Z home
5.  Manual / Computer spindle control

Ideally it would interface with three parallel ports, or scale back gracefully for two and one port configurations.  Thoughts on this?</div>

</div>

<div class="includeitem">

<div class="includetitle">Lessons</div>

<div class="includetext">

I've moved the cable to a newer computer, and my runaway mill issue is gone. The old parallel port seems to be the issue in that equation, like you said.

You future plans look good, but I think you might be able to implement it all with a single parallel port. If the X/Y/Z switches are all wired in parallel, you can minimize it down to a single input port. If the program hit a switch, the mill will stop as desired and the operator can then determine from where it stopped which axis was in question. For homing, I think EMC can run a simple homing script that moves one axis at a time until an input is tripped, in this case your single limit input. The safety stops such as cover open and e-stop could be combined into one as well if you were short on inputs.

That being said, additional parallel ports will definelty add additional capability for future items (5 axis plus a robot, anyone?).

Looks like a good project that not short on challenges. By the end you'll have a setup far superior to the initial setup, and for pennies on the dollar compared to what LMC would have charged you for it.

Cheers,

-Joel

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Joel,

I took your advice and wired combination limit + home switches on the mill.  Everything is working nearly perfectly.  The major unresolved issue is filtering out the pulses on estop and the cover open switches. 

I have advice on how to filter this out using a cap.  I had tried using a cap as a noise filter, but wired it in series.  I should have wired it parallel to ground.  

The other issue involves the "runaway spindle" when the computer is on, but EMC isn't running.  You saw this behavior on a paticular parallel port, and not another.  I have seen this issue once.  Last night my spindle came on when EMC wasn't running.  

All that should be needed is an XOR gate, the parallel port pins seem to all be at the same / nearly the same voltage.  The XOR gate will only work if two pins are NOT at the same voltage.  This should fix the problem.

Once I iron these remaining issues out I'll make a few PCB boards incorporating all of these features.  I'll also post the schematics here.  

If anyone wants a board, this is the time to let me know.

Email me: shannon dot haworth@gmail dot com.

</div>

</div>

<div class="includeitem">

<div class="includetitle">Rex O'Regan</div>

<div class="includetext">

I have now just got the mill working however I do not know the stepper timing, gearing, or any other info needed to operate the machine properly. The steppers seem to be taking a step but then waiting for a period. If anyone is prepared to share this information I can be contacted at [rexoregan20@yahoo](mailto:rexoregan20@yahoo) dot com dot au or on this thread [http://www.linuxcnc.org/component/option,com_kunena/Itemid,20/func,view/catid,16/id,3501/lang,english/](http://www.linuxcnc.org/component/option,com_kunena/Itemid,20/func,view/catid,16/id,3501/lang,english/).

Thanks Rex.

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Rex,

I will e-mail you.

Cheers,

Shannon

</div>

</div>

<div class="includeitem">

<div class="includetitle">Rex O'Regan</div>

<div class="includetext">

Ok now I have the steppers moving more reliably however they make a lot of noise and are not moving smoothly.

Any ideas?

Could the fact that I have just cut the cable be the problem? I have a spare so if it is that shouldn't be too hard to fix 

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Rex,

There are many reasons why you might not have smooth stepper movement.  Thse incldue:

* Trying to move the steppers too fast (I generally stick to 30 ipm or below).

* Mechanical resistance at the leadscrews.

* Check the wire connections on the stepper.  I had some pull loose and it wasn't obvious.

* Incorrect settings in emc.  (Note the sample settings are for inches, you may need to convert to metric).

Several users have reported success.  Others have used a cut-off cable as well.  I doubt this is the issue.

Keep us posted,

Shannon

</div>

</div>

<div class="includeitem">

<div class="includetitle">Rex O'Regan</div>

<div class="includetext">

What is the revision of the board inside your controller box? could that be the problem? mine have no guard on the fan at the back...

Cheers, Rex 

</div>

</div>

<div class="includeitem">

<div class="includetitle">Jim</div>

<div class="includetext">

Hey Shannon,

Thanks for posting this "GOLD" info.

One quick question, do you know if this cable will work with the spectralight lathe under this pin configuration?

It does in fact look to have the same control box as the mills.

As a Lightmachines newbie, any info on this matter would be most helpful

Thanks,

Jim jensen 

</div>

</div>

<div class="includeitem">

<div class="includetitle">jim</div>

<div class="includetext">wow, no input from anyone....what a world,what a world</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Jim,

Sorry.  There are not a lot of comments left here, so I hardly check.   These plans should work on the lathe also.  Have you tried it?

Shannon

</div>

</div>

<div class="includeitem">

<div class="includetitle">John VanderHeyden</div>

<div class="includetext">

I have the Spectralight driver box running from Mach3 and a Pentium 4 desktop parallel port.  My cable wiring is almost identical to Shannon's above.  I did add a 3-component charge-pump circuit in the cable so the enable signal to pin 22 would only be active when the program was running.  Made pin 1 a charge-pump output rather than an enable.

In order to get the Spectralight box to respond to the Mach3 5-15 microsecond-long step pulses, I had to add three pullup resistors to the opto-couplers inside the box.  I don't know if that is necessary on all of the Spectralight boxes, but it was on mine.  I also added a pullup to another pin to supply +5 to the charge-pump circuit.  I reverse-engineered almost all of the Spectralight box to a logic/wiring diagram.  The cable diagram is included.  My drawing is in MS Visio, but I can save and send it as a .jpg.  Email me at heyvan@verizon.net  I'd rather email it than post it, because it is still a work in progress

The Lathe will run just like the mill, but direction signal levels might be reversed.  For the Lathe, only the 15-pin and the spindle power get connected.  The 9-pin cable from the Lathe DOES NOT connect to the box - at least I don't believe so.  It is for spindle speed-control only, and it is intended to connect to the special Spectralight controller.  I intend to reverse-engineer spindle speed control on the Lathe eventually, but it might be a while.

My E-stop mushroom button works, but I don't have the door and limit switches working yet.

</div>

</div>

<div class="includeitem">

<div class="includetitle">jim</div>

<div class="includetext">

Thanks for your comments on the lathe s/u.

I went ahead and gave up after hours of frustration.

Iam going the hobby cnc route with driver board and stronger steppers.Far too much time lost on this adapter cable...hope it works for everyone else. 

Who needs a black control box??  

Thanks all,

 jim 

</div>

</div>

<div class="includeitem">

<div class="includetitle">jim</div>

<div class="includetext">might as well remove all my comments then...sorry to step on your feet, sissy.</div>

</div>

<div class="includeitem">

<div class="includetitle">Shannon Haworth</div>

<div class="includetext">

Jim,

Good luck with the hobby cnc board.  I've looked long and hard at that board and it looks like a great solution.  If I was going the upgrade route I would also upgrade the steppers while I was at it.  I can't justify the expense given that the mill is one of many hobbies.  I would love to know how the project turns out. 

Sorry the cable didn't work for you.  

Shannon

</div>

</div>

<div class="includeitem">

<div class="includetitle">Mike</div>

<div class="includetext">

Thank you for posting this info.  I have the Spectralight mill and even an old controller card box.  I built the harness and connected dirctely from the computer to the controller. I'm not sure what I'm doing wrong but it seems there isn't enough power for the steppers to work.  They groan a little and occasionaly turn in little jerks.  I know the steppers work because when I hotwire them from the spindle power to the steppers, they seem to work fine. I've tried two different computers and two different controllers with the same result each time.

Any suggestions? 

</div>

</div>

<div class="includeitem">

<div class="includetitle">willem</div>

<div class="includetext">Hey Jim,  
       I have used the hobby cnc boards. They work just fine however, they use chopper stepper drivers which can induce spurious signals if you do not plan your wiring carefully. Run your limit switches separately in shielded cables apart from your motor drivers. Keep your cables short use star wiring techniques. Oh thank you for the black box wiring diagram I will give it a try.  
Sincerely,  
         Willem</div>

</div>

<div class="includeitem">

<div class="includetitle">Michael Kobask</div>

<div class="includetext">Will the SpectraLight software milling programs still work using this new type of interface?</div>

</div>

<div class="includeitem">

<div class="includetitle">John R.</div>

<div class="includetext">

Hello,

 I am trying to help maintain three old ProLight machines for my stepson's Robotics class.  I believe these are relatives of the SpectraLight machines and use the same interface board and black box.  The school provides zero funding, so there is no chance of buying new hardware or software.  Recently the mill started acting up, so I may have a dying black box or ISA interface board.  If anyone out there has leftover boards, parts for a black box, schematics, anything we could use to troubleshoot and repair the old hardware, please let me know, email scooperman at vigproducts dot com. I can't afford to pay a lot.  In the meantime I am going to try collecting all of the cable/interface information posted here.  Thanks, John.

</div>

</div>

<div class="includeitem">

<div class="includetitle">Dave</div>

<div class="includetext">

I'm going to try this cable.  I'll be sure to post my results.

I also have a HobbyCNC board built for another project, and was all set to change out steppers to ones I have data on, but then stumbled onto this page.  I am interested, though, if my control box doesn't work, in what kind of current I need to set the HobbyCNC board for to use the steppers already on the machine.

Oh, and I hope y'all don't mind.  I will be emailing for the schematic/block diagram/whatever and other info that's been gathered. 

Dave

dave_m1974@yahoo.com

</div>

</div>

<div class="includeitem">

<div class="includetitle">Rajstennaj Barrabas</div>

<div class="includetext">

I've got a Spectralight controller & my parallel port doesn't have enough power to drive the optoisolators.

I'd like to try adding pullup resistors, as  per the post above.

Can I get a copy of the JPG of the controller schematic? You can E-mail me: John (at) OkianWarrior (dot) com

</div>

</div>

<div class="includeitem">

<div class="includetitle">John R.</div>

<div class="includetext">

Dave,  I did not reverse engineer the entire black box or the interface card.  When mine started giving problems, I did a little troubleshooting. I have traced out the 25-pin connector I/O circuitry, just a portion of the ISA card so that I could figure out what is (should be) happening.   I detailed this in Post #53 on this CNCZone thread

http://www.cnczone.com/forums/benchtop_machines/110393-anyone_here_use_have_prolight.html

The Intelitek freeware for the mill is powerful, but like a lot of stepper controllers the ISA interface uses a fire-and-forget control policy; the (Windows) software sends a command to the board and then assumes the machine actually did what it was told to do, apparently there is no checking or confirmation to see if it actually did what was commanded.  At a minimum, I would have expected the software to read back the data from the card before sending a blast of stepper pulses down the cable to the black box.  In my case, the machine first destroyed a part with a crazy Y move, then when everything was reset and we tried again it crashed an end mill through the part, into the table where it finally stalled the spindle and blew a fuse before we could hit the red button.  The black box will not do this, it will not invent thousands of stepper pulses, those pulses came down the cable from the ISA card. 

The ISA card has some hmmmm let's say compromises in its pcb layout.  Its an 80s design, two-sided, no ground or power plane.  Lots of Side1/Side2 crossover jumps with vias, and since there are no planes this means many 5V/Gnd jumps.  To minimize power layout jumps, I would use all of the available ISA edge finger connections to the power supply, but this pcb designer neglected some of the available pins.  I modified my board to pick up those 5V and Gnd connections, and then I did some trace cuts and hackwire additions to redistribute the ground current.  I also pulled and replaced the old electrolytic caps.  Since these changes,  I have had no crashes.  However, I am adding a G27 at the end of every NC file, and I am running shorter NC files so that I can check the homing frequently. So far so good.

</div>

</div>

<div class="includeitem">

<div class="includetitle">Shamus</div>

<div class="includetext">

First off, thanks for all the info! So I recently bought an used Spectralight CNC mill and followed your instructions for the harness to a tie. I even tested every pin from one side of the cable to the other using a multimeter. I plugged the cable harness from my parallel printer port on my computer to the black box of the Spectralight. I was setting up the configuration in LinuxCNC (formerly EMC2). I get to the configuration where I set up the X or Y or Z axis. There is a button to test out the axis. When I click the button, the machine will make a loud click, but it won't move if I jog the axis one way or the other. None of the axis's are moving. I also noticed that I have a 9-pin serial cable that has a label on it to go to the LMC card on my computer which I don't have. I believe I read on another site that this is spindle speed? Only 2 of the 9-pins are being used. 

Any ideas? 

Shamus

</div>

</div>

<div class="includeitem">

<div class="includetitle">Clockdoc</div>

<div class="includetext">

I am in the process of getting the spectralight mill I bought to run with the cable info I got from spaceopera.org.  I'd like to find a way to contact anyone who has been this route and is willing to help.

Thanks 

clockdoc@eaglecom.net

</div>

</div>

<div class="includeitem">

<div class="includetitle">John</div>

<div class="includetext">

Can anyone who has the spindle controls working correctly tell me what the configuration header settings are in the control box?

 I have X/Y/Z axis movement working well, but cannot get the spindle to turn on.

Thanks

John

jdejong@sentex.net

</div>

</div>


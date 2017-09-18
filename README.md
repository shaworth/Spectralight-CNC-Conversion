*Notice*
This repository contains a VERY hasty conversion of HTML to MarkDown.  Links and images are broken.  I had fully planned to abandon this site, however the demand for this information hasn't declined.  Therefor I've moved the information here.  Feel free to help clean this up!

**Update Summer of 2017**
Please consider using one of the inexpensive motion control solutions such as RAMPS that are now available (usually sold as 3D printer control boards).  I purchased a RAMPS board for less than $30.00USD as a complete alternative to the methods provided below.  I spent another $30.00 for a power supply.  The result is a silky smooth and self contained control system for the mill.  With a RAMPS board the mill does not require a dedicated PC to operate.  I simply load gcode into a SD card, and use the LCD on the RAMPS board to control the mill.



**Overview**

This document outlines how to run your SpectraLight CNC mill without using the computer card.<br/>  The impatient should follow [this link](spectralight0200parallelportadapter/) for plans detailing a $5.00 cable.<br/>  This cable enables control of your mill without requiring the computer card.<br/>  Better yet, using this adapter allows you to control your mill using any of the standard controller packages such as EMC2, Mach3, TurboCNC and many others.

* * *

* * *

**Background**

In the summer of 2009 I purchased a used SpectraLight 0200 CNC mil.<br/>  This mill is essentially a CNC retrofit of the Sherline 5400 desktop mill.<br/>  These mills were normally sold to schools.

I was lucky as my mill was complete and operational when I purchased it. <br/> <br/>  The auction included the PC, software, controller box and all cables.<br/>  The PC includes ISA card which is used to communicate with the mill.<br/>  I have since learned that it is very common for these mills to be sold without their controller cards.

At first I was completely satisified with the mill and the software that came bundled with it.<br/>  But that changed as I encountered the limitations of the bundled software.<br/>  The biggest source of frustration is that the standard software implements a tiny subset of the control codes that most CAD/CAM software generates.<br/>  This prevents the use of all but the simpliest CAD/CAM packages to create 3D models.<br/>  The controller software refused to execute most of the industry standard code that I attempted to use.

The more I learned about the mill the more frustrated I became.<br/>  The limitations are entirely due to the software.<br/>  The underlying Sherline 5400 is a very capable mill.<br/>  Something must be done.

Now the obvious solution is use more powerful controller software.<br/>  However this mill uses a proprietary ISA card that is evidently only supported by the bundled software.

I'm not the first person to purchase this mill used and encounter these issues.<br/>  Most users seem to replace the controller (and often the steppers and power supply) with hardware that interfaces with the parallel port of the computer.<br/>  This allows the mill to be controlled by industry standard software such as Mach3, TurboCNC or EMC2 (my choice). <br/> 

So, I started researching controller boards, stepper moters and power supplies with the intent of (re?)retrofitting the mill with something like a HobbyCNC controller / power supply / stepper motor combo.<br/>  The more I learned about the underlying technologies the more I realized that the only thing "wrong" with my current mill is that it requires the custom interface card.<br/> 

A less expensive solution would be to control the mill using a standard parallel port.<br/>  This approach would be inexpensive since it wouldn't be necessary to replace the controler box.<br/>  It would be more flexible since parallel port control of CNC mills is something of a standard and is supported by a wide variety of software packages.<br/>  The key would be to emulate the signals from the ISA card using the parallel port. Time to break out the scope and figure out how the ISA card and the mill talk to one another.<br/> <br/> 

![](http://farm5.static.flickr.com/4122/4767189938_294997bc5f_z.jpg)  
_Figure 1.<br/>  Getting nerdy on the kitchen table._

The ISA card has a pair of connectors.<br/>  A DB9 socket (female) connector and a DB25 socket connector.<br/>  Only two pins are exposed on the DB9 so I focused my efforts on the DB25\.

Decoding the signals between the card and the controller box proved to be much easier than I expected.<br/>  The only odd finding is that many of the signals were inverted from what I expected.<br/>  Stepper pulses are sent as zero volt pulses with the signal normally held at +5v.<br/>  Once I realized that fact, and knew to look for inverted logic, the work went quickly.<br/> 

The remainder of this site douments the communications interface between the controller and the card.<br/>  It also includes plans for a [parallel port interface cable](spectralight0200parallelportadapter/) that allows control of the mill using a the standard parallel port.



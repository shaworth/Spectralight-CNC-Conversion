<div id="container">

<div id="header">

# Adapter Board

## SpectraLight 0200 Parallel Port Control

</div>

<div id="navigation">

*   [Home](/site/)
*   [Adapter Cable](/site/spectralight0200parallelportadapter/)
*   [Adapter Board](/site/adapterboard/)
*   [control_box_internals](/site/controlboxinternals/)
*   [EMC2 Configuration](/site/emc2configuration/)
*   [Controller Pins](/site/reverseengineeringthecontroller/)
*   [Interface Card Pins](/site/spectralight0200protocol/)
*   [Unexpected clock](/site/strangeplacetoputaclock/)

</div>

<div id="content">

## Overview

An adapter board (PCB board really) will allow logic to be included in the adapter, which in turn can be used to ensure the mill does not run when control software such as EMC or Mach3 are not running.  
  This page is here to show the progress being made (or not) being made on the board.

The approach is to use a  
  microcontroller (ATMega8) to monitor the state of the various safety devices (cover switch, estop from the mill or the PC, and the "charge pump" (aka watchdog).  
  If any of these are activated then the board should disable the amp on the controller.  
  This will prevent any of the axis or the spindle from running or stop them if they are already running.  
  The secondary goal of this adapter is to provide easy access to attach limit switches or other imputs on the unused parallel port pins.  
  Finally, this design is a stepping stone to a version that will include spindle speed control.  

## Desired Features

*   Full X/Y/Z axis control of the mill.
*   Limit/home switch support for X and Y (using the factory Z axis).
*   Mill should default to a safe mode during boot and when emc isn't running.
*   Safety interlocks should operate fully, even when EMC isn't running.

## First Attempt

Here is a picture from the first attempt at building an adapter board.  
  It looks great.

![](http://farm5.static.flickr.com/4100/4857884645_00fb091cc5.jpg)

As you can see, this much less fragile than my [cross over cable](../spectralight0200parallelportadapter/).  
  However the advantages end there.  
  This board was supposed to be powered by one of the 5v pins from the controller.  
  However it draws too much current and the microcontroler doesn't boot.  
  In short the board doesn't even turn on.

The plan is to add a 5v power regulator and power connectors to this board.  
  Once this is complete we can identify the next roadblock.  

</div>

</div>

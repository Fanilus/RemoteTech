---
title: About
layout: content
---

{% include banner.html %}

**Oh shit son!** This page is still under development!
{: .alert .alert-danger}

* Table of Contents
{:toc}

##Introduction to RemoteTech
RemoteTech is a modification for Squad's 'Kerbal Space Program' (KSP) which overhauls the unmanned space program. It does this by requiring unmanned vessels have a connection to Kerbal Space Center (KSC) to be able to be controlled. This adds a new layer of difficulty that compensates for the lack of live crewmembers.

##First steps

* Like in stock KSP, you need to research Flight Control before you can build unmanned probes.
* You need to use an antenna that won't break in the atmosphere to be able to control an unmanned rocket during atmospheric flight. The Reflectron DP-10, unlocked along with the Stayputnik probe core, is the earliest such antenna available. Others can be found in the [parts listing](#).
* For farther flights, your probe should also have more powerful antennas, such as the Communotron 16 or the Comms DTS-M1. You will have to manually turn on these antennas once you get high enough that the airflow won't break them off, and if you are using the DTS-M1 you will also need to target it at the KSC. Both commands can be done by right-clicking on the antenna.
* Once you can place satellites in orbit, consider putting up some comsats to maintain a connection when out of sight of KSC. See the [comsat tutorial](#) for more details.
* As you expand farther out into the system, you may need to expand and/or upgrade your comsat network to allow for connections to probes orbiting other moons or planets. Plan ahead!

##Overview of mechanics

###Antennas
Using antennas, it is now possible to set up satellite networks to route your control input. Unlike in stock KSP,  antennas will no longer activate or deactivate automatically; you must order an antenna to activate by right-clicking on it. There are two classes of antennas: 'Dishes' and 'Omnidirectionals'.

####Dishes
Dishes are antennas that must be instructed what direction to point at. They do not physically point at something; it is as simple as selecting a target from a list. Dishes tend to be used for long range communication and come with a cone of vision (which is narrower for longer-range antennas). If the dish is pointed at a planet or moon, anything inside this cone can achieve a stable connection with the dish.

####Omnidirectionals
Omni antennas radiate in every direction equally, and as such do not require you to target them at anything. A consequence is that they are limited to shorter ranges.

###Signal Delay
To comply with Kerbal law, RemoteTech is required to delay your control input so that signalling does not exceed the 'speed of light' (pfft, what a silly law). If you are aware of the consequences of breaking the law (or like being a rebel), you are free to turn this off in the settings file.

###Connections
A 'working connection' is defined as a command center being able to send control input to its destination and back. Connections between neighbouring satellites are referred to as 'links'. To have a link between two satellites, it is required that *both* satellites can transmit a signal to the other independently. <!-- For point A to transmit with a dish, the dish would need to be set to target point B, point B would need to be within range of A's dish, and there would need to be no planets or moons blocking the line of sight between point A and point B. Since omni antennas are never targeted, they merely need to have point B within range and a clear line of sight. Note that point B also has to pass these criteria -->
You have a connection when there is a sequence of links between a command center and the destination.
<!-- -->
If there are multiple ways to get a working connection (relaying through different satellites), RemoteTech will automatically pick the shortest path with the smallest signal delay.

<!-- ![A relay sends a transmission from the far side of the Mun towards Kerbin](images/connectiondemo1.jpg "Mun polar relay"){.pairedimages}
![A comsat gets the transmission from the Mun and forwards it to KSC](images/connectiondemo2.jpg "Kerbin comsat"){.pairedimages}

**Example:** this probe in low Munar orbit can't link to KSC because the probe is on the far side of the Mun. However, it can link to a relay satellite in polar orbit. The relay also can't link to KSC, because KSC is on the other side of the planet. However, it can link to any of several communications satellites orbiting Kerbin (for clarity, only the best connection is shown). One of these satellites can link to KSC (shown by the red dot). Therefore, the probe has a working connection with KSC, as relayed by the two intermediate satellites, even though there are nearly 1600 km of solid rock blocking a direct transmission. -->

###Signal Processors
Signal Processors are any part that can recieve commands over a working connection, including all stock probe cores. You will only be able to control a signal processor as long as you have a working connection, and by default you will be subject to [signal delay](#signal_delay). Signal processors also include a *Flight Computer* that can be used to schedule actions ahead of time, for example to carry out basic tasks during a communications gap.

<!--**Beware**: if you do not have a working connection, you cannot send **any** commands to an unmanned probe, including commands to activate its antennas!-->

###Command Stations
For those extra long distance missions, it is possible to set up a team of Kerbals to act as a local command center. This Command Station can not process science, a connection to KSC will still be required for that. However, the Command Station allows you to work without the signal delay to Kerbin, which might otherwise climb up to several minutes. Command Stations require a special probe part and a minimum number of kerbals to operate. Consult your VAB technicians for more information.

###Science Transmissions
Transmitting science back to KSC now requires you have a working connection back to KSC. Any other source of control, such as a crew pod or a working connection to a command station, does not count.

##List of parts

###Modified stock parts

* All stock probe cores now have [signal processor capability](#signal_processors) so that they are affected by the communications network they are connected to.

* The three stock antennas have been modified to make them fit the rules of RemoteTech: the Communotron 16 is now the basic [omnidirectional antenna](#omnidirectionals), the Comms DTS-M1 a short-range [dish](#dishes), and the Communotron 88-88 a medium-range dish.

* The Launch Stability Enhancer now acts as a land line for the rocket, allowing the player to send pre-launch commands regardless of whether any antennas are active.

###Modified third-party mod parts

* The MechJeb AR202 can act as a signal processor, just like the stock probe cores.

Neither other third-party probe cores, nor any third-party antennas, are supported at this time.

###New parts

RemoteTech 2 includes seven new antennas.
* The Reflectron DP-10 is a short-range omnidirectional antenna intended for launch and landing.
* The CommTech EXP-VR-2T and Communotron 32 are enhanced omnidirectional antennas.
* The Reflectron KR-7 and KR-14 are short- and medium-range dishes, respectively.
* The CommTech-1 and Reflectron GX-128 are long-range dishes designed for missions to the outer planets.

<!--
###Probe Cores

All stock probe cores serve as [signal processors](#signal_processors). In addition, the RC-L01 Remote Guidance Unit can serve as a [command station](#command_stations), provided a crew of 6 or more kerbals is available to split the jobs of running the ship and sending instructions to nearby probes.

###Omnidirectional Antennas

Yes, the non-breaking spaces are necessary; the table won't set column widths sensibly without them
Part                | Cost | Mass            | Drag | Range          | Power Drain   | Notes
Reflectron DP-10    | 80   | 0.005&nbsp;tons | 0.2  |    500&nbsp;km | 0.01&nbsp;e/s | Activated on mission start. Not damaged by atmospheric flight
Communotron 16      | 150  | 0.005&nbsp;tons | 0.2  |   2500&nbsp;km | 0.13&nbsp;e/s | 
CommTech EXP-VR-2T  | 550  | 0.02&nbsp;tons  | 0.0  |   3000&nbsp;km | 0.18&nbsp;e/s | 
Communotron 32      | 150  | 0.01&nbsp;tons  | 0.2  |   5000&nbsp;km | 0.6&nbsp;e/s  | 
KSC Mission Control |      |                 |      | 75,000&nbsp;km |               | Command Station

All science transmissions with stock or RemoteTech antennas cost 7.5 charge per Mit, and they all drain 50 charge per second while transmitting science. This is in addition to the power drain listed in the table, which is for keeping the antenna active and searching for links.

###Dish Antennas

Yes, the non-breaking spaces are necessary; the table won't set column widths sensibly without them
Antenna           | Cost | Mass            | Drag | Cone Angle | Range          | Power Drain   | Notes
Comms DTS-M1      | 100  | 0.3&nbsp;tons   | 0.2  | 45&deg;    | 50,000&nbsp;km | 0.82&nbsp;e/s | 
Reflectron KR-7   | 100  | 0.5&nbsp;tons   | 0.2  | 25&deg;    | 90,000&nbsp;km | 0.82&nbsp;e/s | Not damaged by atmospheric flight
Communotron 88-88 | 900  | 0.025&nbsp;tons | 0.2  | 0.06&deg;  | 40M&nbsp;km    | 0.93&nbsp;e/s | 
Reflectron KR-14  | 100  | 1.0&nbsp;tons   | 0.2  | 0.04&deg;  | 60M&nbsp;km    | 0.93&nbsp;e/s | Not damaged by atmospheric flight
CommTech-1        | 800  | 1.0&nbsp;tons   | 0.2  | 0.006&deg; | 350M&nbsp;km   | 2.6&nbsp;e/s  | Not damaged by atmospheric flight
Reflectron GX-128 | 800  | 0.5&nbsp;tons   | 0.2  | 0.005&deg; | 400M&nbsp;km   | 2.8&nbsp;e/s  | 

All science transmissions with stock or RemoteTech antennas cost 7.5 charge per Mit, and they all drain 50 charge per second while transmitting science. This is in addition to the power drain listed in the table, which is for keeping the antenna active and searching for links.
-->

##Credits
* The_Duck, for the precursor to this mod.
* JDP, for RemoteTech 1.x.
* -
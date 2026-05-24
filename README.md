# AETHERSDR-Advanced-USB-Relay-Integration    

# Version

00.01.05 May 24th, 2026 by Richard VE2DX 

References; 
AETHERSDR Vers.: 26.5.2.1, Mai 2026
FlexRadio SmartSDR Vers.: 4.2.18, Mai 2026
"USB Cables Interface Guide for the FLEX-6000" Version 1.6.1, 26 July 2019

## Introduction

Proposed changes in **AETHERSDR** of USB Relay integration for a more **advanced integration** offering more **flexibility** and better **SO2R integration**.

## 1- The Author

**Richard G. Desaulniers Sr.**, **VE2DX**, was the Owner, President, and Lead designer at **VE2DX Electronics Design Inc.**
A Canadian-based Ham Radio Electronics company founded in 2020 and closed in late 2025 following worldwide economic instability.

## 2- Context

This project will be submitted to the **AETHERSDR team** of the USB relay interfacing as a possible advanced evolution, and added SO2R support

While the **FlexRadio** integration of the 8-bit USB Relay PCB offers a great, low-cost, simple interface, the USB-based relay integration for antenna and other automated control, it lacks some badly needed improvements. Among those;

#### - The possibility to assign multiple bands or frequency ranges to a single relay output to address multiband antennas like a common 80/40 dipole or the very common tribander yagi.

#### - A better SO2R integration, where two remote antenna switching boxes or an SO2R remote antenna box can be managed TOGETHER to prevent radio damage from improper antenna selection, better BanPass Filter support, and better integration of multiple USB Relay PCB.

#### - Adding CH340/341 chip sets to the Flexradio Radio OS, to be able to support, at the radio end, more advanced hardware like 16 relay USB PCBs, the WinKeyer, etc...

#### - And VE2DX Electronics Design Inc. Software Defined Interlock(c) (SDI(c)) to prevent two radios from transmitting or receiving on the same antenna or band.

As noted in above this project is not only to help in the evolution of **AETHERSDR**, but also in the evolution of FlexRadio radios to get better USB chipset support to expand the possibilities of the platform.

## 3- Technical Information.

### 3.1- FlexRadio present approach.

<img width="1146" height="798" alt="image" src="https://github.com/user-attachments/assets/2f2c3f9d-eaeb-423b-bdd3-3299f9379149" />

The present approach by **FlexRadio** in the latest version, as of this document's publication, is flawed in a couple of different ways. It does not address the specific requirements of SO2R. It lacks flexibility and does not address the specific requirements for multiband antennas, etc.

#### 3.1.1- The _SOURCE_ is always output oriented, this is ok and gives the user some flexibility, but in SO2R you need to be able to manage a group of output. Thus offering an SO2R mode in the top of this window, moving the Source pull down in that same upper area and SO2R mode again in that same area would address this concern (item 1 in the image).

#### 3.1.2- The band select or frequency range selection is limited to ONE band or frequency range; this should be replaced by a pull-down where, in the band mode, it would list all the possible bands. And in frequency range mode this pull down would look like the following image.

<img width="472" height="381" alt="image" src="https://github.com/user-attachments/assets/0317f9a2-b919-44ce-8e38-092fe5832ca1" />

#### 3.1.3- The present support of USB chipsets in the radios OS is very limited. Only 


### 3.2- AETHERSDR present approach.

_Insert Image here_

At present the **AETHERSDR** implementation of the 8-BIT USB Relay PCB is at its begining being in the early days of the project. it has a couple of bugs that will be pointed out in this document that are probably related to the fact that this portion of the project is not finished.

### BUGS:

**Bug 1:** The Band/Frequency field (last column) does not work.
**Bug 2:** If enter is keyed at anytime within the window, the USB Cables window crashes and can only be recalled if the AETHERSDR is closed and restarted.
**Bug 3:** The **EN (Enable)** selection can not be selected from the Keyboard (Only from the mouse).

#### 3.2.1- In the present AETHERSDR USB popup screen shown above, the _BIT_ column indicating the relay being used, is way to wide this should be only three characters wide.

**Todo**: Change the **_BIT_** column to 3 characters wide.

#### 3.2.2- In the present AETHERSDR USB popup screen shown above, the _EN_ (Enable) column indicating the relay being used, is way to wide this should be only three characters wide.

**Todo**: Change the **_EN_ (Enable)** column to 3 characters wide.

#### 3.2.3- In the present AETHERSDR USB popup screen shown above, the _EN_ (Enable) column indicating the relay being used, does not have any clear indicator to the position of the BOX, this box should be framed.

**Todo**: Frame the **_EN_ (Enable)** boxes to make their presence more obvious.

#### 3.2.4- Add to the _Cable Setting_ area a new pulldown menu titled _MODE_, this should trigger a pulldown menu with the following options; Manual, SO2R

**Todo**: Add to the **Cable Setting** area a new pulldown menu titled **MODE**, this should trigger a pulldown menu with the following options; Manual, SO2R.  By default the Manual should be shown, once changed the new selection should always be shown and remembered.

#### 3.2.5- Add to the _Cable Setting_ area a new pulldown menu titled _MODE_, this should trigger a pulldown menu with the following options; Manual, SO2R

**Todo**: Add to the **Cable Setting** area a new pulldown menu titled **MODE**, this should trigger a pulldown menu with the following options; Manual, SO2R.  By default the MANUAL should be shown, once changed the new selection should always be shown and remembered.

#### 3.2.6- Add to the _Cable Setting_ area a new pulldown menu titled _SO2R Mode_, this should ONLY show up if the _MODE_ option fro, 3.2.5 is set to SO2R. It should trigger a pulldown menu with the following options; Antenna, Band Pass Filter (BPF)

**Todo**: Add to the **Cable Setting** area a new pulldown menu titled **SO2R MODE**, this should this should ONLY show up if the _MODE_ option fro, 3.2.5 is set to SO2R. It should trigger a pulldown menu with the following options; Antenna, Band Pass Filter (BPF). By default the ANTENNA should be shown, once changed the new selection should always be shown and remembered.


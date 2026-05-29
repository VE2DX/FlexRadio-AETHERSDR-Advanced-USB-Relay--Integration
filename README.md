# AETHERSDR-Advanced-USB-Relay-Integration    

## Copyright

**Copyright (c)2020-2026 Richard G. Desaulniers Sr., VE2DX, All Rights Reserved.**

## Version

00.01.35 May 29th, 2026 by Richard VE2DX 

## References;

**AETHERSDR** Vers.: 26.5.2.1, Mai 2026

**FlexRadio SmartSDR** Vers.: 4.2.18, Mai 2026

**"USB Cables Interface Guide for the FLEX-6000"** Version 1.6.1, 26 July 2019

## Author

**Richard G. Desaulniers Sr.**, **VE2DX**, was the Owner, President, and Lead designer at **VE2DX Electronics Design Inc.**
A Canadian-based Ham Radio Electronics company founded in 2020 and closed in late 2025 following worldwide economic instability.

## 1- Introduction

Proposed changes in **AETHERSDR** of USB Relay integration for a more **advanced integration** offering more **flexibility** and adds **SO2R integration** and **Software Defined Interlock(c) SDI(c)**.

## 2- Context

This project is for an advanced evolution in **AETHERSDR** of the USB relay interface, and adds SO2R and SDI(c) support. It will be submitted to the **AETHERSDR team**.

While the **FlexRadio** integration of the 8-bit USB Relay PCB offers a great, low-cost, simple interface for integrating antenna and other automated controls, it lacks some badly needed improvements and flexibility. Among those;

#### - The possibility to assign multiple bands or frequency ranges to a single relay output to address multiband antennas like a common 80/40 dipole or the very common tribander yagi.
#### - A better SO2R integration, where two remote antenna switching boxes or a "Two By" SO2R remote antenna box can be managed.
#### - Better Band Pass Filter (BPF) support.
#### - Better integration of multiple USB Relay PCBs.
#### - VE2DX Electronics Design Inc. Software Defined Interlock(c) (SDI(c)) to prevent two radios from transmitting or receiving on the same antenna or band.
#### - And adding support of CH340/341 chip sets to the Flexradio Radio OS, to be able to support, at the radio end, more advanced hardware like 16 relay USB PCBs, the WinKeyer, etc...

As noted above, this project is not only about advancing **AETHERSDR** but also about improving USB chipset support for FlexRadio radios to expand the platform's capabilities.

## 3- Technical Information.
### 3.1- FlexRadio present approach.

<img width="1146" height="798" alt="image" src="https://github.com/user-attachments/assets/2f2c3f9d-eaeb-423b-bdd3-3299f9379149" />

The present approach by **FlexRadio** in the latest version, as of this document's publication, is flawed in a couple of different ways; 
- does not address the specific requirements for multiband antennas.
- It does not address the specific requirements of SO2R.
- It does not address the specific requirements of BPF.
- It lacks flexibility.

#### 3.1.1- (1) The _SOURCE_ is always output-oriented; this is ok and gives the user some flexibility, but in SO2R, you need to be able to manage a group of outputs. Thus, offering an SO2R mode at the top of this window, moving the Source pull-down in that same upper area, and SO2R mode again in that same area would address this concern.

#### 3.1.2- (2) The band select or frequency range selection is limited to ONE band or frequency range; this should be replaced by a pull-down where, in the band mode, it would list all the possible bands. And in frequency range mode, this pull-down would look like the following image.

<img width="472" height="381" alt="image" src="https://github.com/user-attachments/assets/0317f9a2-b919-44ce-8e38-092fe5832ca1" />

#### 3.1.3- The present support of USB chipsets in the radio's OS is very limited. Only some FTDI chip sets are supported, which limits what users can do.

### 3.2- AETHERSDR present approach.

<img width="1014" height="786" alt="image" src="https://github.com/user-attachments/assets/a27d1011-b9d4-4152-8076-1f35f67eb917" />

At present, the **AETHERSDR** implementation of the 8-BIT USB Relay PCB is in its early days. This has a couple of bugs that will be documented here, likely related to the fact that this portion of the project is not finished.

### BUGS:
- **Bug 1:** The Band/Frequency field (last column) does not work.
- **Bug 2:** If enter is keyed at any time within the window, the USB Cables window crashes and can only be recalled if the AETHERSDR is closed and restarted.
- **Bug 3:** The **EN (Enable)** selection can not be selected from the Keyboard (Only from the mouse).

#### 3.2.1- (1) In the present AETHERSDR USB popup screen shown above, the _BIT_ column indicating the relay being used, is way too wide; this should be only three characters wide.

**Todo**: 
- Change the **_BIT_** column to 3 characters wide.

#### 3.2.2- (2) In the present AETHERSDR USB popup screen shown above, the _EN_ (Enable) column indicating the relay being used, is way too wide; this should be only three characters wide.

**Todo**: 
- Change the **_EN_ (Enable)** column to 3 characters wide.

#### 3.2.3- (3) In the present AETHERSDR USB popup screen shown above, the _EN_ (Enable) column indicating the relay being used does not have any clear indicator of the position of the BOX; this box should be framed.

**Todo**: 
- Frame the **_EN_ (Enable)** boxes to make their presence more obvious.

#### 3.2.4- (6) Add to the _Cable Setting_ area a new pulldown menu titled _MODE_, this should trigger a pulldown menu with the following options; Manual, SO2R

**Todo**: 
- Add to the **Cable Setting** area a new pulldown menu titled **MODE**.
- This should trigger a pulldown menu with the following options: **Manual**, **SO2R**.
- By default, the **Manual** should be shown.
- Once changed, the new selection should always be shown and remembered.

#### 3.2.5- (6) If in the _Cable Setting_ area a new pulldown menu titled _MODE_ is in SO2R mode, the SOURCE column (4) should be removed and replaced by 3.2.8. The SOURCE column (4) should only be displayed if the THE _MODE_ setting is set to Manual.

**Todo**: 
- Remove the SOURCE column (4) and replace it with 3.2.8 in the **Cable Setting** new pulldown menu titled **MODE** 3.2.4, is set to SO2R.
- Display the SOURCE column (4) and replace it with 3.2.8 in the **Cable Setting** new pulldown menu titled **MODE** 3.2.4, is set to Manual.
- By default, the **Manual** should be shown.
- Once changed, the new selection should always be shown and remembered.

#### 3.2.6- Add to the _Cable Setting_ area a new pulldown menu titled _MODE_, this should trigger a pulldown menu with the following options; Manual, SO2R

**Todo**: 

- Add to the **Cable Setting** area a new pulldown menu titled **MODE**.
- This should trigger a pulldown menu with the following options: **Manual**, **SO2R**.
- By default, the **MANUAL** should be shown.
- Once changed, the new selection should always be shown and remembered.

#### 3.2.7- Add to the _Cable Setting_ area a new pulldown menu titled _SO2R Mode_, this should ONLY show up if the _MODE_ option fro, 3.2.5 is set to SO2R. It should trigger a pulldown menu with the following options: Antenna, Band Pass Filter (BPF)

**Todo**: 
- Add to the **Cable Setting** area a new pulldown menu titled **SO2R MODE**.
- This should this should ONLY show up if the **MODE** option fro, 3.2.5 is set to **SO2R**.
- It should trigger a pulldown menu with the following options: Antenna, Band Pass Filter (BPF).
- By default, the **ANTENNA** should be shown.
- Once changed, the new selection should always be shown and remembered.

#### 3.2.8- Add to the _Cable Setting_ area a new pulldown menu titled _source_, this should ONLY show up if the _MODE_ option fro, 3.2.5 is set to SO2R. It should trigger a pulldown menu with the following options: (See 3.2.9)

**Todo**: 
- Add to the **Cable Setting** area a new pulldown menu titled **SOURCE**
- this should ONLY show up if the **MODE** option fro, 3.2.5 is set to **SO2R**
- It should trigger a pulldown menu with the following options: (See 3.2.9)

#### 3.2.9- The present list of sources in _AETHERSDR_ is limited; it should be changed to match the FlexRadio present list.

**Todo**: 
Change the sources to match the **FlexRadio** reference:
  - **TX Slice:** The cable will report the slice receiver frequency that holds the Transmit Indicator.
  - **Active Slice:** The cable will report the frequency of the active slice receiver (the slice that has the yellow cursor).
  - **TX Panadapter:** The cable will report the center frequency of the panadapter that contains the transmit slice.
  - **Specific Slice:** The cable will report the frequency of the specified slice (A, B, C, D, E, F, G, H).
  - **RX Antenna:** The cable will report the frequency of the specified receive antenna (ANT1, ANT2, XVTR, RXA, RXB).
Note: If multiple slices are on the same RX Antenna, then the frequency of the last tuned slice will be reported.
  - **TX Antenna:** The cable will report the frequency of the specified transmit antenna (ANT1, ANT2, XVTR). Note: This frequency is only changed/reported when the TX Slice is connected to the specified antenna.

#### 3.2.10- The present _AETHERSDR_ version does not support PTT functions in the USB relay PCB (See (3) on Flexradio image 3.1). This is important for some setups. 

As per FlexRadio reference, "When set, the wire will become active only when the radio is in transmit, and the source frequency is within the output band/frequency range. Individual wire PTT and TX Delays can be set and will be used by the radio when keyed."

Like with the **Source**, this option should be adapted to the Manual or SO2R operations, while in manual mode, this PTT setting should appear as the last column to the right side and be output-oriented; while in SO2R mode, this column should be removed and the PTT Option should be moved to the **Cable Setting** area as a single setting for the group.  

**Todo**: 
if the _MODE_ option fro, 3.2.5 is set to SO2R.
  
  - Add to the **Cable Setting** area a new pulldown menu titled **SO2R PTT**
    - this should ONLY show up if the **MODE** option fro, 3.2.5 is set to **SO2R**
    - When the SO2R PTT is clicked on, a pull-down should show Manual, Grouped.

<img width="596" height="118" alt="image" src="https://github.com/user-attachments/assets/6efd4a54-ac1f-4b00-afa9-2891f5b5c96c" />
 
    - When the **SO2R PTT** is in manual:
      - Add a new column to the right side of the existing ones with the TX options.
      - For each output, these are controlled separately.


<img width="199" height="508" alt="image" src="https://github.com/user-attachments/assets/b301b560-473a-4755-8308-1ebc970130d0" />
 
    - When the **SO2R PTT** is in Grouped:
      - TAdd a new column to the right side of the existing ones with the TX options.
      - For each output, these are controlled separately.  

# AETHERSDR-Advanced-USB-Relay-Integration

# Version

00.01.05 May 24th, 2026 by Richard VE2DX

# Introduction

Proposed changes in AETHERSDR of USB Relay integration for a more advanced integration offering more flexibility and better SO2R integration.

# 1- The Author

Richard G. Desaulniers Sr., VE2DX, was the Owner, President, and Lead designer at VE2DX Electronics Design Inc.
A Canadian-based Ham Radio Electronics company founded in 2020 and closed in late 2025 following worldwide economic instability.

This project will be submitted to the AETHERSDR team as a possible evolution of the USB relay interfacing.

# 2- Context

This project will be submitted to the AETHERSDR team of the USB relay interfacing as a possible advanced evolution, and added SO2R support

While the FlexRadio integration of the 8-bit USB Relay PCB offers a great, low-cost, simple interface, the USB-based relay integration for antenna and other automated control, it lacks some badly needed improvements. Among those;

- The possibility to assign multiple bands or frequency ranges to a single relay output to address multiband antennas like a common 80/40 dipole or the very common tribander yagi.

- A better SO2R integration, where two remote antenna switching boxes or an SO2R remote antenna box can be managed TOGETHER to prevent radio damage from improper antenna selection, better BanPass Filter support, and better integration of multiple USB Relay PCB.

- Adding CH340/341 chip sets to the Flexradio Radio OS, to be able to support, at the radio end, more advanced hardware like 16 relay USB PCBs, the WinKeyer, etc...

- And VE2DX Electronics Design Inc. Software Defined Interlock(c) (SDI(c)) to prevent two radios from transmitting or receiving on the same antenna or band.

# 3- Technical Information.

# 3.1- FlexRadio present approach.

<img width="1146" height="798" alt="image" src="https://github.com/user-attachments/assets/2f2c3f9d-eaeb-423b-bdd3-3299f9379149" />

The present approach by FlexRadio in the latest version, as of this document's publication, is flawed in a couple of different ways. It does not address the specific requirements of SO2R. It lacks flexibility and does not address the specific requirements for multiband antennas, etc.

3.1.1- The SOURCE is always output oriented, this is ok and gives the user some flexibility, but in SO2R you need to be able to manage a group of output, thus offering an SO2R mode in the top of this window, with added Source pull down in that same upper area and SO2R mode again in that same area would address this concern (item 1 in the image).

3.1.2- The band select or frequency range selection is limited to ONE item; this should be replaced by a pull-down where, in the band mode, it would list all the possible bands. And in frequency range mode this pull down would look like the following image.

<img width="472" height="381" alt="image" src="https://github.com/user-attachments/assets/0317f9a2-b919-44ce-8e38-092fe5832ca1" />





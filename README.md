This is a printed circuit board to breakout an 8-lane PCI Express socket into
8x SATA channels, which we have used with Terasic DE4 FPGA boards.

THIS IS NOT A SATA CONTROLLER, it merely uses SATA sockets for the physical
connections as the sockets and cables are cheap, and have good signal integrity.
What you put down the PCIe lanes is up to your FPGA configuration.

Images (the first version with a few hand bugfixes):
![Front board image](http://www.cl.cam.ac.uk/research/comparch/opensource/pcie-sata/PCIeSATA-front-scaled.jpg)
![Rear board image](http://www.cl.cam.ac.uk/research/comparch/opensource/pcie-sata/PCIeSATA-reverse-scaled.jpg)

The design was created using Eagle PCB, but the gerber files should be
usable even if you don't have Eagle.

The 4-layer board was fabricated by rak.co.uk using a standard-ish stackup:  
0.2mm double sided  
2 pre-pregs (0.15mm)  
0.8mm unclad board  
2 pre-pregs (0.15mm)  
0.2mm double sided  
Total 1.5-1.6mm  

They don't provide controlled impedance boards but our design is sized to
have the correct impedances according to this stackup.

In addition ports are provided for:  
SATA power (3.3V and 12V)  
Altera USB Blaster-compatible JTAG port  

Since we couldn't source SATA power connectors without data, the data part
of the SATA power connector is connected to some I/Os on the PCIe connector. 
This can be used for low-speed signalling from the FPGA.

If you connect a USB Blaster to the JTAG port you need to fit components to
VREF_SRC to supply the correct VREF.  The DE4 uses 2.5V - we fit resistors
68R from 3V3 to VREF and 220R from VREF to ground.

R1/R2/R3 provide access to the unused lines on the JTAG cable, or means to
ground them to reduce noise.

Computer Architecture Group, University of Cambridge Computer Laboratory  
May 2013  
http://www.cl.cam.ac.uk/research/comparch/  




Copyright (c) 2013, Simon Moore  
All rights reserved.  

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

 1. Redistributions of source code must retain the above copyright notice, this
    list of conditions and the following disclaimer.

 2. Redistributions in binary form must reproduce the above copyright
    notice, this list of conditions and the following disclaimer in the
    documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

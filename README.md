This is a printed circuit board to breakout an 8-lane PCI Express socket into
8x SATA channels, which we have used with Terasic DE4 FPGA boards.

THIS IS NOT A SATA CONTROLLER, it merely uses SATA sockets for the physical
connections as the sockets and cables are cheap, and have good signal integrity.
What you put down the PCIe lanes is up to your FPGA configuration.

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

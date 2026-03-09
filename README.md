# Serial Communication System
Project developed during University courses.

## General Description of the Functionality

The project implements a serial communication system using VHDL. 
The system transmits information in the form of data packets.
Each packet contains:
-a start segment (with a start bit and a start code)

-a data segment (formed by 4 words encoded in BCD)

-a checksum calculated using the XOR operation.
  
The system includes two logical blocks: 
-a generator, which emits the packets

-a detector, which validates the received content.

## System Architecture

The system is composed of several modules:

-ROM: used to store the components of the data packet.

-UNITATE_CONTROL: finite state machine(FSM) controlling the system.

-UNITATE_EXECUTIE: performs operations on the received data.

-date_serial: extracts packet bits in the correct order.

-nr_ss, nr_sm, nr_sc: counters for the start, data and checksum segments.

-MPG: filters the push-button signal.

-final.vhd: top-level module integrating all components.

## Operating Principle

The system processes packets in several stages:

1. Initialization
   The system starts in a waiting state. The transmission begins when the run signal is activated.
2. Start Bit Detection
   The System monitors the data line to detect the first bit of the packet.
3. Start Segment Validation (SS)
   The FSM verifies the start code to confirm the beginning of a valid packet.
4. Data Segment Processing (SM)
   The system receives the 16 data bits (4 BCD word), while the SM counter tracks the position inside the packet.
5. Checksum Calculation (SC)
   The system computes the XOR checksum for the received data.
6. Verification
   The calculated checksum is compared with the transmitted one. If they match, the led_final signal is activated, confirming a valid packet.


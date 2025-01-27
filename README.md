# Chip_Design
## Introduction to Chip
In this project, let's go over all the fundamentals: from designing a chip to (fill it in later) 
We have all seen an aurdino board somewhere or somehow. In this project we will be talking about the industry that lies within its chip. 
![aurdino](https://github.com/user-attachments/assets/82672ee3-3fd6-4f87-a3df-453ea3a69706)

In general when we want to create our own board, the below image is the typical board template.
![board](https://github.com/user-attachments/assets/f3ef0874-e3c8-455b-b366-8b5f4aea96ec)
When we open up this processor, it will look like this:
![opened_processor](https://github.com/user-attachments/assets/0a1903e6-49f9-435b-927a-fe0faa0e7cbf)
We generally know this image as a '*chip*' but a better term for it would be '*package*'. An example for a package in the real world is *QFN-48*. We have many more as well though. The locations of the pins of this package are all driven by the board. 
The chip generally sits in the center of the package.
![bond_wires](https://github.com/user-attachments/assets/e4e49d26-a777-48e5-a13f-33f71cdb0142)
As we can see, the pins of the chip are connected to the pins of the package using *bond wires*. And in this way are able to transfer all the signals that are coming from the outside world to the interiors of the chip.
Important Componants of a Chip:
![chip_parts](https://github.com/user-attachments/assets/33351714-bcab-4e99-9d64-40feb9676018)
Pads: Pads help us send signals inside/outside the chip
Core: A place where all the digital logic sits (and-gate, or-gate, etc.)
Die: Size of the entire chip
Let's take an RISCV chip as an example and observe the parts it contains in its core.
![RISVC](https://github.com/user-attachments/assets/8b105cad-eb10-41c3-ad34-5d6e4cd230c4)

The parts marked with the arrows to the right are called *Foundry IPs*. 

What is a Foundry?
A foundry is a factory where chips get manufactured.

What is an IP?
IP stands for Intellectual Property.
It requires intelligence to build the blocks in the chip.

The parts marked with the arrows to the right are called *Macros*. 
Macros: They are pure digital logic.

## RISC-V Instruction Set Architecture(ISA)
This is a language of computers and a way we talk to computers.

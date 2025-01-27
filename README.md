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
![code](https://github.com/user-attachments/assets/5d3348a7-c7dc-4ffe-a00f-0a71a071be64)

For example we have a C-program as we can see in the picture to the left. We can also see the interior of a chip present inside a laptop in the picture to the right. If this C-program needs to be run on this particular layout, then we need to pass the information(code) to the harwarde in certain terms. 

Steps that are followed to achive this:
1. C-program is complied to its assembly langauge program (RISC-V Assembly Language Program in this case)
2. Assembly language program is converted into Machine-Readable Programe (a.k.a, Binary Language Program which is the logic of 1s and 0s. In the code it is currently present in a hexa-decimal format.)
3. The bits get excecuted in the hardware and we get the required output.

To convert the RISC-V Arcitecture into hardware  
There is another interface that needs to be present between RISC-V Arcitecture and the hardware, it is nothing but the hardware description langauge(picture to the bottom).
We need to implement the RISC-V specificationd using some RTL(picorv32 cpu core is used here). This RTL implements the specifications of the RISCV architecture.
Finally to convert the RTL and PDK to GDS, we use an EDA tool. GDS is the required file to send to the foundry for the manufacturing of the chip.

What is RTL(Registered Transfer Level)?
It is code written to describe the physical logic present in the chip at a high level (it is written in the high level for it to be easily understanable when engineers work with this code).

What is GDS(Graphic Data System)?
It is the detailed information about the position, dimension and the connections between the components of the chip.
![gds](https://github.com/user-attachments/assets/dbd8c700-7852-4219-9428-b190df072dbb)
<sub>Example of GDS</sub>

What is PDK(Process Design Kit)?
It is the interface between the foundry and the designers.
A PDK consits of the following:
1. Proccess design rules
2. Device models (eg: NMOS, PMOS, Ressistors, Capacitors)
3. Digital standard cell libraries (eg: OR gate, AND gate, D-FlipFlop)
4. Input/Ouput libraries
5. Process control parameters (eg: speed, voltage levels, temperature ranges, variability of the components, etc.)

What is EDA(Electronic Design Automation)?
EDA is a set of sowtware tools that helps automate the design process of a chip. (In this project we will using *OpenLANE*)
![EDA](https://github.com/user-attachments/assets/2cb8a1d2-9cb6-4261-a0a7-fe799515aece)
<sub>Various Tasks Perfomed by EDA Tools</sub>


## What is the connection between hardware and software?
Now let's understand how the computer, which works only based on 1s and 0s, understand the various types of data we feed into the applications present in our computers.
For this to happen, the data present in the various applications we use in our computer has to get conververted to binary bits. This is done by the *system software*. The system software comprises of the OS(Operating System), compiler, assembler.
The overall sequence goes like this:
1. Application Software
2. System Software
3. Hardware
![system_software](https://github.com/user-attachments/assets/1196657a-0420-4fd0-b0b5-9bc38d9cdb73)

Steps followed in the System Software:
1. OS: It has a programes that manage the hardware.
2. Compiler: Take the information of the application in the form of a high level code and converts it into instruction sets that are appropriate for the hardware system it works with.
3. Assembler: Converts the code in the compiler into binary form.

Steps followed to create the chip:
1. RTL is written.
2. Foundry provides details (in the form of a PDK) about the component capabilites used to build the chip.
3. RTL and PDK are given to EDA tools.
   The steps performed by the EDA are:
   i) Synthesis of RTL into a netlist of gates.
        ![netlist](https://github.com/user-attachments/assets/ada98132-5232-4d72-b2e4-ff263b08177f)
   ii) Placement and Routing of the gates.
4. GDS is generated and sent to a foundry where the chip is fabricated.





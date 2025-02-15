# Chip Design for High School Course Documentation
<p align="center">
  <img src="https://github.com/user-attachments/assets/75a9573a-0fd2-46ee-8bff-d7d02f78477a" width="1200" height="300"/>
</p>

## Let's learn the fundamentals! 🦾
<details>
	<summary>𝙸𝚗𝚝𝚛𝚘𝚍𝚞𝚌𝚝𝚒𝚘𝚗 𝚝𝚘 '𝙲𝚑𝚒𝚙'</summary>	
	
In this project, let's go over all the fundamentals: from designing a chip to (fill it in later)  
We have all seen an Arduino board somewhere or somehow. In this project, we will be talking about the industry that lies within its chip. <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/82672ee3-3fd6-4f87-a3df-453ea3a69706" width="400" height="250"/>
</p>

In general when we want to create our own board, the below image is the typical board template.
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/f3ef0874-e3c8-455b-b366-8b5f4aea96ec" width="600" height="340"/>
</p>

When we open up this processor, it will look like this:
<p align="center">
  <img src="https://github.com/user-attachments/assets/0a1903e6-49f9-435b-927a-fe0faa0e7cbf" width="600" height="440"/>
</p>

We generally know this image as a '*chip*' but a better term for it would be '*package*'. An example for a package in the real world is *QFN-48*. We have many more as well though. The locations of the pins of this package are all driven by the board. 
The chip generally sits in the center of the package.
<p align="center">
  <img src="https://github.com/user-attachments/assets/e4e49d26-a777-48e5-a13f-33f71cdb0142" width="600" height="440"/>
</p>

As we can see, the pins of the chip are connected to the pins of the package using *bond wires*. And in this way are able to transfer all the signals that are coming from the outside world to the interiors of the chip.
Important Componants of a Chip:
<p align="center">
  <img src="https://github.com/user-attachments/assets/33351714-bcab-4e99-9d64-40feb9676018" width="600" height="420"/>
</p>

Pads: Pads help us send signals inside/outside the chip
Core: A place where all the digital logic sits (and-gate, or-gate, etc.)
Die: Size of the entire chip
Let's take an RISCV chip as an example and observe the parts it contains in its core.
<p align="center">
  <img src="https://github.com/user-attachments/assets/8b105cad-eb10-41c3-ad34-5d6e4cd230c4" width="600" height="400"/>
</p>

The parts marked with the arrows to the right are called *Foundry IPs*. 

What is a Foundry?
A foundry is a factory where chips get manufactured.

What is an IP?
IP stands for Intellectual Property.
It requires intelligence to build the blocks in the chip.

The parts marked with the arrows to the right are called *Macros*. 
Macros: They are pure digital logic.
</details>

<details>
<summary>𝚂𝚝𝚎𝚙𝚜 𝚘𝚏 𝙵𝚊𝚋𝚛𝚒𝚌𝚊𝚝𝚒𝚗𝚐 𝚊 𝙲𝚑𝚒𝚙</summary>

## Chip Fabrication Steps:
### #1 Creating an Isolation Region

![image](https://github.com/user-attachments/assets/b26ab5db-74d0-49b9-ac57-141a6e153db1)
1. First a layer of thin Silicon Oxide is placed. (brown in img)
2. On top of that Silicon Nitrate is placed. (blue in img)
3. A layer of Photoresist is placed. (white in img)
4. A mask is placed over the places we want to preserve/protect. (red in img)
5. UV light is shone on the entire thing to remove the Photoresist in the parts that are not protected by the mask.
   ![image](https://github.com/user-attachments/assets/16d7b912-3e93-4f0c-be9a-dc0c29f70340)
6. We remove the masks and then etch off the Silicon Nitrate. It will be etched off in the places where the Photoresist is not present.
  ![image](https://github.com/user-attachments/assets/c63eeae9-fb8c-43d8-81fa-866073feebc7)
7. The Photoresist is removed. Then we place the entire thing in an oxidation furnace. The parts where the Silicon Nitrate is not present will grow. This process is called *LOCOS[Local Oxidation of Silicon]*. The places where the bulge growth starts from are known as the *Bird's Beak*.
   ![image](https://github.com/user-attachments/assets/ba2a61a5-ecad-4cd5-bd1c-6f6d60bf9430)
8. The Silicon Nitrate is removed and we get a surface such that transistors are not in direct contact with each other. We have created an electrical isolation.
   ![image](https://github.com/user-attachments/assets/d670d272-45e4-485c-b8dc-2a9af0b8dea8)

### #2 N-Well and P-Well Formation
1. The same procedure is followed to protect the left side.
  ![image](https://github.com/user-attachments/assets/d735c796-a514-49ac-89f4-3207886bbda9)
2. After the Photoresist has been removed on the right, atoms of Boron are hit with high force to diffuse into the P-Substrate. A P-well is formed.
   ![image](https://github.com/user-attachments/assets/74864098-f67f-4bb0-a2ca-9b16cdb3fe23)
3. Similarly atoms of Phosphorus are hit with high force to diffuse into the P-Substrate. A N-well is formed.
  ![image](https://github.com/user-attachments/assets/2b552100-4ace-438f-a5c8-a12c43abc098)
4. The entire Substrate in heated in a high temperature furnace for a long time. This will drive in the the atoms into the P-Subrates, forming clear visible wells. This process is called *twin tub process*.
   ![image](https://github.com/user-attachments/assets/9c1c13e6-d5cb-4dee-ac43-9315eb39b9b4)

### #3 Formation of Gate Terminal
1. Just like before, we hit Boron atoms on the right side, but this time at a low energy so that is only lies on the surface.
   ![image](https://github.com/user-attachments/assets/2b2493a5-c5d6-405b-a00d-2d26602097f4)
2. The same is done on the left side. We can either use Phosphorus or Arsenic atoms. [Arsenic atoms will not penertate deep into the Substrate]
   ![image](https://github.com/user-attachments/assets/1423c48f-f9a3-4412-a024-25d3ad620bcf)
3. But when this doping is done, damages occur in the Slicone Oxide layer. To fix this, the damaged oxide is stripped off using dilute hydrofluric acid.
  ![image](https://github.com/user-attachments/assets/dedef78c-1680-4059-9aaf-03f46f8d60e1)
  And then the oxide layer is re-grown again.
  ![image](https://github.com/user-attachments/assets/f4a3738d-ef6c-4081-bfc8-5e8c7d557dd4)
4. We grow a thick polysilicon layer on it. The gate area is supossed to be of low ressistance, so we top it with N-type impurities.
   ![image](https://github.com/user-attachments/assets/7cc0dd89-ee58-4e7c-9cac-a609a94cd4fb)
5. We make the following structure.
   ![image](https://github.com/user-attachments/assets/19a0f089-d3e5-4077-b52e-107e530ecc2a)
6. Only the area under the Photoresist remains and we obtain our gates.
   ![image](https://github.com/user-attachments/assets/60d67641-a640-4b2a-ae31-f0a062870eb9)

### #4 Lightly Doped Drain Formation(LDD)
 Two reasons for doing this are to prevent: → Hot electron effect
				            → Short channel effect
1. Phosphorus is very lightly doped at the surface level of the P-well.
   ![image](https://github.com/user-attachments/assets/ada24080-f6af-4b46-928c-b9b6a25993c1)
2. SImilarly Boron is also very lightly doped on the surface of the N-well.
   ![image](https://github.com/user-attachments/assets/6fdcd325-e14a-4845-aef9-4248df0bc64b)
3. Since these layer are very thin, we need to protect them. To do this, *Plsama Anisotropic Etching* is done using Silicon Nitrate.
   ![image](https://github.com/user-attachments/assets/228f98c7-c4b5-4bc3-afb9-8fb6d409ca32)
   The Silicon Nitrate sticks to the ends of the gates and rest gets washed away.
   ![image](https://github.com/user-attachments/assets/4bdd65a3-e171-49eb-b50b-6f6b5b34ec99)
   Thus, the doped atoms under the Silicon Nitrate are protected.
   
### #5 Source and Drain Formation
1. A thin screen oxide is added to to prevent the doped ions from directly going to the substrate without hitting anywhere. By adding this, we randomize the direction of the ions.
   ![image](https://github.com/user-attachments/assets/d38c72ec-f23c-43a0-a8d1-20d030faabe9)
2. Arsenic is then doped. And we obtain P+,P- as required.
   ![image](https://github.com/user-attachments/assets/b801d5a3-c9dc-4a59-a673-59140c113d5a)
3. Boron is then doped. And we obtani the N+,N- as required.
   ![image](https://github.com/user-attachments/assets/6f16f4ce-073f-41f6-8f24-cfa9be45b084)
4. After high temperature furnace heating, followed by etching of the oxide, Titanium is deposited using sputtering
   ![image](https://github.com/user-attachments/assets/3e3bc1c8-6ca1-42c6-84d0-5b7fbf12b59f)
### #5 Local Interconnect Formation
1. A layer of Silicon is formed above Titanium to get low resistance TiSi. Then the source/drain regions are exposed using a mask as shown. The mask preserves the TiN underneath to later form the local interconnects.
   ![image](https://github.com/user-attachments/assets/866371d6-f3e1-4282-94fe-07fd4b2ebd9e)
2. Next, a thick SiO2 layer is deposited and then polished as shown.
   ![image](https://github.com/user-attachments/assets/fdfad821-0a6a-4219-900d-2005f046e327)
3. Repeating again with another mask for the gate and source/drain contacts, we deposit Tungsten and once again do CMP to obtain planar surface.
   ![image](https://github.com/user-attachments/assets/d78b5797-8aff-4530-b730-d1ab6b0f9b4c)
### #5 Metal Routing Layer Formation
1. For metal layer, we use a new mask and etch Aluminum where not required.
   ![image](https://github.com/user-attachments/assets/3a3d476c-6204-4980-9113-6f2bf5dbe1e5)
2. Repeating for second metal layer, we get two stacks of metal for routing. Then the top of metal is covered with Si3N4 to protect the chip.
    ![image](https://github.com/user-attachments/assets/9e417316-39a9-404a-83a9-59b9b1dac989)
3. Finally, we get the complete chip fabricated with all the required interconnects and terminals as shown:
    ![image](https://github.com/user-attachments/assets/c780729f-2f25-4455-8e3b-733fbe809433)


</details>	


## RISC-V and OpenLANE 🖳
<details>
<summary>𝚁𝙸𝚂𝙲-𝚅 𝙸𝚗𝚜𝚝𝚛𝚞𝚌𝚝𝚒𝚘𝚗 𝚂𝚎𝚝 𝙰𝚛𝚌𝚑𝚒𝚝𝚎𝚌𝚝𝚞𝚛𝚎(𝙸𝚂𝙰)</summary>
This is a language of computers and a way we talk to computers.
<p align="center">
  <img src="https://github.com/user-attachments/assets/5d3348a7-c7dc-4ffe-a00f-0a71a071be64" width="700" height="400"/>
</p>


For example we have a C-program as we can see in the picture to the left. We can also see the interior of a chip present inside a laptop in the picture to the right. If this C-program needs to be run on this particular layout, then we need to pass the information(code) to the harwarde in certain terms. 

Steps that are followed to achive this:
1. C-program is complied to its assembly language program (RISC-V Assembly Language Program in this case)
2. Assembly language program is converted into Machine-Readable Program (a.k.a, Binary Language Program which is the logic of 1s and 0s. In the code it is currently present in a hexa-decimal format.)
3. The bits get excecuted in the hardware and we get the required output.

To convert the RISC-V Arcitecture into hardware  
There is another interface that needs to be present between RISC-V Arcitecture and the hardware, it is nothing but the hardware description langauge(picture to the bottom).
We need to implement the RISC-V specificationd using some RTL(picorv32 cpu core is used here). This RTL implements the specifications of the RISCV architecture.
Finally to convert the RTL and PDK to GDS, we use an EDA tool. GDS is the required file to send to the foundry for the manufacturing of the chip.

What is RTL(Registered Transfer Level)?
It is code written to describe the physical logic present in the chip at a high level (it is written in the high level for it to be easily understanable when engineers work with this code).

What is GDS(Graphic Data System)?
It is the detailed information about the position, dimension and the connections between the components of the chip.
<p align="center">
  <img src="https://github.com/user-attachments/assets/dbd8c700-7852-4219-9428-b190df072dbb" width="700" height="550"/>
</p>

<p align="center">
	<sub>Example of GDS</sub>
</p>

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
<p align="center">
  <img src="https://github.com/user-attachments/assets/2cb8a1d2-9cb6-4261-a0a7-fe799515aece" width="700" height="500"/>
</p>

<p align="center">
  <sub>Various Tasks Perfomed by EDA Tools</sub>
</p>
</details>

<details>
<summary>𝚆𝚑𝚊𝚝 𝚒𝚜 𝚝𝚑𝚎 𝚌𝚘𝚗𝚗𝚎𝚌𝚝𝚒𝚘𝚗 𝚋𝚎𝚝𝚠𝚎𝚎𝚗 𝚑𝚊𝚛𝚍𝚠𝚊𝚛𝚎 𝚊𝚗𝚍 𝚜𝚘𝚏𝚝𝚠𝚊𝚛𝚎?</summary>
Now let's understand how the computer, which works only based on 1s and 0s, understand the various types of data we feed into the applications present in our computers.
For this to happen, the data present in the various applications we use in our computer has to get conververted to binary bits. This is done by the *system software*. The system software comprises of the OS(Operating System), compiler, assembler.
The overall sequence goes like this:
1. Application Software
2. System Software
3. Hardware
<p align="center">
  <img src="https://github.com/user-attachments/assets/1196657a-0420-4fd0-b0b5-9bc38d9cdb73" width="750" height="450"/>
</p>

Steps followed in the System Software:
1. OS: It has a programes that manage the hardware.
2. Compiler: Take the information of the application in the form of a high level code and converts it into instruction sets that are appropriate for the hardware system it works with.
3. Assembler: Converts the code in the compiler into binary form.

Steps followed to create the chip:
<p align="center">
  <img src="https://github.com/user-attachments/assets/1d25b21a-d61e-4f9b-a2f0-1ff4688b85df" width="650" height="300"/>
</p>

1. RTL is written.
2. Foundry provides details (in the form of a PDK) about the component capabilites used to build the chip.
3. RTL and PDK are given to EDA tools.
   The steps performed by the EDA are:
   
<p></p>
   
   i) Synthesis of RTL into a netlist of gates.
        <p align="center">
          <img src="https://github.com/user-attachments/assets/ada98132-5232-4d72-b2e4-ff263b08177f" width="750" height="300"/>
        </p> 
  
   ii) Floor Planning: Deciding where all the major blocks(macros) are placed within the chip.
         <p align="center">
          <img src="https://github.com/user-attachments/assets/adfc534e-6704-4256-8dc8-b9ca097afa22" width="300" height="300"/>
        </p> 
      
   
   iii) Power Planning: Planning how the supply and ground connections are routed to all the logic gates.
         <p align="center">
          <img src="https://github.com/user-attachments/assets/b67d226e-920d-4df4-bfc5-8ef660d96e39" width="400" height="300"/>
        </p> 
       
   iv) Placement: Relative placement of gates for optimal routing and to minimize signal delays.
         <p align="center">
          <img src="https://github.com/user-attachments/assets/acfa5190-187a-4825-a024-dfc7af097d37" width="400" height="300"/>
        </p> 
      
   v) Clock Tree Synthesis
         <p align="center">
          <img src="https://github.com/user-attachments/assets/2cdf7227-7601-45ea-bf28-f0e67122306b" width="400" height="300"/>
        </p> 
     
   vi) Routing
        <p align="center">
             <img src="https://github.com/user-attachments/assets/cd5d704f-8ca6-415e-9a9d-f2512e857644" width="400" height="300"/>
         </p> 
       
   vii) Sign off: It consists of DRC(Design Rules Check), LVS(Layout Vs Schematic) and STA(Atatic Timing Analyisis).
   
5. GDS is generated and sent to a foundry where the chip is fabricated.
</details>
  

<details>
<summary>𝙾𝚙𝚎𝚗𝙻𝙰𝙽𝙴</summary>
Main goal: To produce a clean GDS with no human intervention (no-human-in-the-loop)
Here clean means: 1. No LVS Violations
                  2. No DRC Violations
                  3. No Timing Violations
                  
OpenLANE can be used to hardern Macros and Chips. (Harden means to generate the GDS to implement Macros or Chips)

It has two modes of opperation:
   1. Autonomous: We configure the flow, then push button to get the final GDS.
   2. Interactive: We can run commands one by one so that we can expirement and look at the immediate results for each step.

It has a very nice feature called *Design Space Exploration*. It is used to find the best set of flow configurations.

OpenLANE also has a large number of design examples - it has 43 designs with thier best configurations as of now.
</details>
  

<details>
<summary>𝙾𝚙𝚎𝚗𝙻𝙰𝙽𝙴 𝙰𝚂𝙸𝙲 𝙵𝙻𝚘𝚠</summary>
Note: ASIC → Application Specific IC
 <p align="center">
             <img src="https://github.com/user-attachments/assets/3367bf33-a3e0-43e7-9bfc-590cf1a2fa25" width="700" height="450"/>
  </p> 


1. RTL Synthesis [Tool → Yosys & abc]: The RTL is fed to the Yosys with the design contraints. Yosys traslates the RTL into circuits using engineering componants. This circuit can be optimized and then mapped into cells from the library using abc. 'abc' has to be guided during the omptimization. And this comes in the form of 'abc' scripts.

2. Static Timing Analysis [Tool → OpenSTA]: Sometimes the logic from a gate will go through different paths and come together in the end to combine and give some output. If the different paths have different delays then the momentary output would be incorrect. The flip flops in the circuit may accidentally store the momentarily changed value instead of correct final value and this can create logic errors. This tool checks for such timing issues created due to the logic taking different paths. If there are such errors, we have to give inputs to the tool to avoid such timing violations.
   
3. Design for Test: Additional circuits added in the design that help in testing the chips after fabrication.
    <p align="center">
             <img src="https://github.com/user-attachments/assets/c39c9f37-37d9-44dc-a60e-bc094f76f7f9" width="700" height="450"/>
    </p>
                    It has a few steps:
                     i) Scan Insertion
                     ii) Automatic Test Pattern Generation(ATPG)
                     iii) Fault Coverage
                     iv) Fault Simulation
   
5. Physical Implementation [Tool → OPENROAD]:
    <p align="center">
             <img src="https://github.com/user-attachments/assets/aac7dfb0-eeef-4754-bf59-495299b30e63" width="300" height="350"/>
    </p>
                     Steps:
                     i) Floor Planning
                     ii) Power Planning
                     iii) Placement
                     iv) Clock Tree Synthesis
                     v) Post Placemet-Optimization
                     vi) Antenna Diode Insertion
                     vii) Routing: Global and Detailed

7. Logic Equivalance Check(LEC) [Tool → Yosys]: Since some of the previous steps such as *clock tree synthesis* and *post-placement       
   optimization* would have edited the *netlist*, we now have to make sure that the final design is still equivalent to the original netlist we 
   generated at the synthesis stage.

8. Detailed Routing [Tool → TritonRoute]
   
9. Post-Layout RC Extraction and STA and Physical Verification [Tool → OpenSTA, magic, netgen]
   
10. GDS generation for fabrication
</details>

## Course Implementation Overview ⚙️
<details>
<summary>𝙾𝚙𝚎𝚗𝙻𝙰𝙽𝙴 𝚊𝚗𝚍 𝙿𝙳𝙺 𝙳𝚒𝚛𝚎𝚌𝚝𝚘𝚛𝚢 𝚂𝚝𝚛𝚞𝚌𝚝𝚞𝚛𝚎</summary>

### Now let's understand the directory structure of openLANE.
	
   → *Folder: openlane → configuration* - All settings related to how openlane will execute each of its tools within it are setup in this folder in the form of tcl scripts.
  
   → *Folder: openlane → designs → picorv32a* - This is our design folder. Anything related to the design is stored in this folder
  
   → *Folder: openlane → designs → picorv32a  → src* - This contains the RTL code that design engineers create (Tool: Verilog)
 
   → *Folder: openlane → designs → picorv32a  → runs* - This contains the *results*, *reports*, and *logs* folder of the EDA tool output at various steps. Everytime we start 								openlane, a new run folder is created using date time info. This helps to keep history of the EDA outputs.

Inside each of the *results*, *reports*, and *logs* folder, there will be multiple sub folders for each major activity such as *synthesis*, *floorplan*, *placement*,*routing* etc.

### Let's understand the directory structure of openPDK

Folder: openlane_working_dir  → pdks  → [*open_pdks*, *skywater-pdk*, *sky130A*]
		
These are the three folders we find inside the pdks folder. 

*open_pdk*: This folder contains scripts that acts as a bridge between what the Foundry provides and what the open EDA tools expect. This takes in the raw PDK data from foundry (skywater-pdk) and converts them to a format that is suitable for open source tools (sky130A) to use.

*skywater-pdk*: Contains Raw Process files. This is provided by SkyWater foundry. This provides the original data from Fab as to how to use their technology.

*sky130A*: This contains processed information that is more suitable for the opensource EDA tools to use in terms of the format and configuration. This is what is loaded into the EDA tools.

</details>


<details>
<summary>𝙾𝚙𝚎𝚗𝙻𝙰𝙽𝙴 𝙲𝚘𝚖𝚖𝚊𝚗𝚍 𝙵𝚕𝚘𝚠</summary>
<p></p>
Commands to Start OpenLANE EDA Tool
<p></p>
	
```python
#docker
$./flow.tcl -interactive

%package require openlane 0.9

%prep -design picorv32a 
```
*Above commands will be used every time we setup the openLANE EDA tool.*

The major steps we follow to take in the RTL and PDK information and generate a GDS file for Foundry fabrication are executed using the following sequence of commands.

1. **% run_synthesis**
This command executes yosys, the synthesis tool along with ABC, the technology mapping tool to generate a verilog netlist that contains the gate level description of circuit that is equivalent to the RTL we provided. 

*Input:* RTL and PDK

*Output:* verilog netlist (gate level details and their connectivity) that is equivalent to our behavior RTL description of the logic.

*Reports:* Die Area estimate, list of cells used, Timing information (and any violations present)

*An important question to address: What do we do if there are timing violations?
→ We will later see how we address the timing violations. We will now focus on the main flow of the tool but let us keep this in mind so we can revisit this later.*

2. **% run_floorplan**
This step takes in our verilog netlist and also any macros used in our design (such as Memory, IP, macros etc) and places the macros along with decoupling capacitors, the input and output pins of our design and also dumps all the cells used in our verilog design. 

*Input:* Verilog netlist, the library of standard cells 

*Output:* *.def* file (Design Exchange Format) → describes the placement details of the cells.

*An important question to address: Where do library cells come from? These are telling the tool what gates are available, how its layout looks like and how its electrical behavior will be (delays). If we want to create our own library cell, what is the way to do it?*

We will also answer this question at a later time when we discuss Standard Library Cell design and Characterization.

**Note:** Sometimes, we get error when executing run_floorplan. In such cases, we can run the following commands in sequence which is equivalent to running the run_floorplan command.
<p></p>

```python

%init_floorplan

%place_io

%tap_decap_or

```
<p></p>

3. **%run_placement**
This command does the actual placement of all the logic cells used in our design. The placement is optimized based on the connectivity of the various cells in order to minimize delays.

*Input:* Takes in the **.def** file from floorplan and updates the cell locations that were previously dumped by properly arranging them optimally within the core region of the die.

*Output:* **.def** file 

4. **% run_cts**
Once the placement of all cells are done, we now know where all the flipflops are located. These flip flops require a clock signal. At every rising or falling edge of the clock signal, all the flip flops will run. The input of the flops come from combinational logic outputs. The output of the flop goes through another combinational logic before reaching the input of another flop. This the Flops are connected through combinational logic paths. A clock acts like a heart beat for a chip. All flops have to work simultaneously to take action on the combinational inputs they receive. For this to happen, the clock signal transitions should reach all the flops at the same instant. To achieve this, the clock is fed through many buffers (two inverters in series) which balances the clock signal propagation delays such that all flops get the clock transitions at around the same time.

*Input:* *.def* file from run_placement output, *.lef* file for standard cells, *.lib* file for timing information

*Output:* Modified verilog netlist that now includes these clock buffer cells as well as the updated *.def* file with clock buffer placement.

5. **%gen_pdn**
This step generates the power distribution network. This is a grid of supply and ground routing that covers the entire core region so that all logic cells have easy and local access to the power supply lines. This helps reduce voltage drop in power and ground routings and ensures correct operation of the logic cells.

*Input:* *.def* file from run_cts output, *.lef* file for the cells 

*Output:* *.def* file that now includes the power and ground grid mesh, and *.lef* file.

6. **%run_routing**
This is an iterative process where all the logic cells’ input and output pins are routing in metal as per the netlist connectivity. There are several routing strategies and algorithms to perform this automation and is an interesting field of research, especially with AI technology. 

*Input:* *.def* file from gen_pdn output

*Output:* *.def* file, the final layout and *.lef* file. It also generates .spef file for parasitic extraction. SPEF is a standard parasitic extraction format to include routing resistance and capacitance in the verilog netlist so that it can be used to find timing information post layout and check for any timing violations.

7. **The final steps to send GDS to Foundry**
Using MAGIC tool, we execute some final checks and generate the GDS file. We are not executing these final steps as part of this Course. But the details of these final checks are summarized below.

**Final Checks:**

#1 **STA:** Run one final Static Timing Analysis using the SPEF file and make sure that there are no TIMING Violations.

#2 **LVS:** We noted that the verilog netlist generated by synthesis tool is repeatedly edited by other tools such as CTS, SPEF extractor etc. Sometimes, engineers can also edit the verilog netlist manually (called ECO, Engineering Change Order) to manually fix any timing violations by replacing a logic gate with a faster version of the same logic gate. So we need to verify whether the final netlist is still representing the logic equivalence to the original RTL.

#3 **DRC:** Since the library cells are locally created by engineers, they may have some Design rule violations. Also, during routing phase, the tool might have violated some design rules. So a final DRC check is run to ensure all design rules suggested by Foundry are still met in our final design.

#4 **Antenna Diode check:** During fabrication, the metal layers are fabricated layer by layer. So if there is a long metal route, the metal will be hanging on one end as the next metal layer is yet to be fabricated. During this time, any stray electric signals can be picked by the long metal trace acting as antenna and that could potentially harm the underlying components connected to that metal trace. To protect the circuits, antenna diodes are added which acts as an alternative safe path for the stray charges picked up by the metal to reach ground or supply terminals. These are verified at this final stage and any necessary changes are automatically done by the EDA tool to protect circuits during fabrication steps.

#5 **Final GDS generation:** MAGIC creates the required GDS format from the *.def* and *.lef* files and it can be sent electronically to foundry and we wait for the chip to be sent back to use from the foundry.
</details>
<details>
<summary>𝙻𝚊𝚋 𝙴𝚡𝚎𝚛𝚌𝚒𝚜𝚎𝚜 𝙾𝚟𝚎𝚛𝚟𝚒𝚎𝚠:</summary>
	<details>
		<summary>OpenLane Flow:</summary>
		We will now go through the process of synthesizing, floorplanning and placement of our design and look at the timing reports as well as the def file showing the placement of cells. 
</details>
	
<details>
<summary>Custom Cell Design:</summary>
<p></p>
Next, we learn how to make our own custom library cell and include that in the openlane flow.
Let’s say we want to build a standard library cell such as an inverter. How do we go about creating a cell ourselves from scratch and how do we make the EDA tool use it in its flow?
<p></p> 
	
**What we need to know:**

**Step #1** *→ DRC Rules provided by the Foundry:* We need good understanding of what DRC rules are, how to read them and understand them.

**Step #2** *→ MAGIC tool:* We need to know how to use MAGIC layout tool and how to draw the various layers that go to form the components that are present inside logic cells.

**Step #3** *→ Standard Cell Format:* We need to follow certain requirements for the standard cell so that a tool can automate the placement and routing of these cells:
i) The height of the cell should be a certain even multiple of the track dimensions of the process technology so that the tool can have a standardized way of placing and routing.
<p></p>
ii) The width of the cell should be a certain odd multiple of the track dimensions of the process technology so that the tool can have a standardized way of placing and routing.
<p></p>
iii) The input and output pins must be at the intersection of the horizontal and vertical track lines so that metal can be easily routed to those pins of the standard cell during routing stage.

**Step #4** *→ Creating .lib file that contains the timing characterization data:* We need to learn how to characterize a standard layout cell for its timing behavior. This is done by extracting the netlist from the layout and using a circuit simulator like *ngspice* along with *spice model files* we get from Foundry to run a circuit simulation and measure the timing delays of the cell. These timing details are then captured in a file called liberty file (*.lib* extension) which is then used by the EDA tool to calculate overall timing for the entire design.

**Step #5** *→ Make the openLANE tool accept our inverter in its synthesis and placement:* After creating our own standard library cell (inverter), we make openlane accept our inverter into its design and wherever it needs to use an inverter; it will now use our newly designed inverter instead of using the already existing inverter cell from the standard library.
</details>

<details>
<summary>STA and Timing Violations Fix and GDS Generation with Custom Library Cells</summary>
Finally, we learn how to fix the timing violations by restarting the openlane flow and using a few methods to fix the timing violations.
Timing analysis shows violations in meeting the required timing for the flops. This needs to be fixed before we proceed with GDS generation. To fix timing violations we have the following options:
<p></p>
i) Slow down the clock frequency so there is more time for the signals to reach from one point to another. But this reduces the speed of the processor which is not the best option.
ii) Ask synthesis tool to optimize timing even at the expense of chip size. This can be done through configurations settings where the env variables can be changed to favour delays over chip size. But this is also not very optimal as the tool may then use larger size gates even where not really needed. But this is an easier solution as the tool takes care of it.
iii) Review the timing report and find out where there is maximum delay and check the logic cell output drive capability and how many gates it is conected to and replace weaker logic gates with stronger logic gates to improve specific delay paths. This is an iterative manual process but gives the best results.
<p></p>
In our design, we will try both option ii) and iii) to fix our timing violations.
<p></p>
We then proceed with floorplanning, placement, clock tree synthesis, routing, final timing analysis, power delivery network generation and parasitic extraction(SPEF) and post extraction timing analysis. 
<p></p>
Our design is then fully ready for fabrication!
	</details>
</details>

## Course Implementation Results 📄
<details>
<summary>𝙾𝚙𝚎𝚗𝙻𝙰𝙽𝙴 𝙵𝚕𝚘𝚠 𝚁𝚎𝚜𝚞𝚕𝚝𝚜 𝚄𝚗𝚝𝚒𝚕 𝙿𝚕𝚊𝚌𝚎𝚖𝚎𝚗𝚝</summary>	
	We execute a sequence of commands from openLANE starting from design preparation till placement of cells.
	<details>
	<summary>Lab Exercise:OpenLane Synthesis</summary>

The verilog code of picorv32a design that we are going to implement in this course is shown below. This is a behavioral RTL code of the RISC-V processor.

<p align="center">
             <img src="https://github.com/user-attachments/assets/e84a0593-9b9e-4d96-aca5-0991c8688f2b" width="650"/>
</p>

The openLANE is invoked using the startup commands and the results are shown below.
<p align="center">
             <img src="https://github.com/user-attachments/assets/e75176ae-bdc0-459c-b7cb-e3e6d9328201" width="650"/>
</p>
	<p align="center">
             <img src="https://github.com/user-attachments/assets/d8d18fb6-6117-4d88-9e4a-e4bedd3559e6" width="800"/>
	</p>
	<p align="center">
             <img src="https://github.com/user-attachments/assets/25c6f6e3-1d62-464b-9e6b-1117fc4c27b4" width="800"/>
	</p>
	<p align="center">
             <img src="https://github.com/user-attachments/assets/5e9168ae-4232-4d3d-a549-c3a4ce095eaf" width="800"/>
	</p>
	The *config.tcl* file here summarizes all the parameters that are finally used in the execution. Using this file we know what all parameters are set for this run.

Synthesis also runs ABC - what is it? It does the technology mapping so that the logic gates required to implement the design are picked from what is available in the technology library.

*run_synthesis* is the command that gives the successful output shown below.

<p align="center">
             <img src="https://github.com/user-attachments/assets/f2b45552-ab03-40af-b1a9-8d33171742a4" width="800"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/915736c6-82d4-41cf-b5a3-9baf85b065f0" width="500"/>
</p>

<p align="center">
             𝐅𝐥𝐨𝐩 𝐫𝐚𝐭𝐢𝐨 = 𝟏𝟔𝟏𝟑/𝟏𝟒𝟖𝟕𝟔 =𝟏𝟎.𝟖𝟒%
</p>

Now we open the synthesized netlist (a verilog file). As expected it shows logic gates along with their connectivity using wires.
<p align="center">
             <img src="https://github.com/user-attachments/assets/2a03431d-1b89-45b4-9971-da7316ae2034" width="800"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/7dcf6d3c-05f4-4b46-aa1c-2b93ae7af128" width="400"/>
</p>
We now open the synthesis timing report file and observe that timing violations are reported.

<p align="center">
             <img src="https://github.com/user-attachments/assets/96d30830-5321-4111-9a70-f59c8cf01373" width="800"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/502fdeca-faa8-49e7-bc9e-733cf14fb884" width="700"/>
</p>

<p align="center">
             *Slack violated*
</p> 
 
 </details>	
	<details>
	<summary>Lab Exercise:OpenLane floorplan</summary>

We now run the command to start floorplanning. The command outputs are shown below.	
<p align="center">
             <img src="https://github.com/user-attachments/assets/ad0cdae7-7790-4fb8-8ab6-25d7663aec79"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/90b49af7-caf1-473c-81b1-04d01e7d1dc9"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/481187fd-f560-48a4-8e92-4a611f026a86"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/153ba737-a10a-48fb-9892-464cb3e53c19"/>
</p>
We can now use the MAGIC layout tool to open the *.def* file generated by floorplan and view the current status of the layout.	
Here is the *.def* file generated by floorplan execution.
 <p align="center">
             <img src="https://github.com/user-attachments/assets/0371b203-b668-49e9-b851-e47d6c56ae21"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/8ba5f9d4-3a36-4464-b26c-8d63e0c512fe"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/baecead9-3c3a-4a80-b096-f6782127d017"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/783850d8-625b-4920-8307-e014dc8abebd"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/b6973a95-4f19-4880-9435-0b84c6b32596"/>
</p>

It is hard to see where the cells are placed in the layout. This is because floorplan simply dumps all the gates used in the design but not actually place them in non-overlapping fashion. This is because the main task of floorplan is to place the macros and decoupling capacitors and the pin placements. It will only bring in all the logic cells used in our design but not place them yet. Proper placement of our design cells will happen only during placement execution which is the next step.
 </details>	
	<details>
	<summary>Lab Exercise:OpenLane placement</summary>

The run_placement command outputs are shown below. The generated *.def* file and *.lef* file are passed to magic tool to see the final placement results.
<p align="center">
             <img src="https://github.com/user-attachments/assets/d5c8d201-4d34-4f50-add0-63639e7f5586"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/307c9530-6239-4253-8b39-0890a99cd996"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/9cdac5f1-7afc-4336-9f3a-3b0ff3db8580"/>
</p>


The 'expand' command in magic *tkcon window* shows the actual d-flipflop layout containing mosfets. But routing of the d-flipflop to other gates is not done yet, because this happens only later when we do *run_routing* command execution.

<p align="center">
             <img src="https://github.com/user-attachments/assets/22f06bda-5b10-41a8-8cdc-4a9139f6fe1a"/>
</p>

We have now successfully completed the openLANE execution flow until placement. We will now take a small detour to understand how to build custom Cell and how to use such custom library cells in openLANE flow. We will then learn how to fix timing violations and then we will return back to openLANE flow and execute the complete flow till GDS creation.
	</details>	 

</details>
<details>
<summary>𝙲𝚞𝚜𝚝𝚘𝚖 𝙲𝚎𝚕𝚕 𝙳𝚎𝚜𝚒𝚐𝚗 𝚁𝚎𝚜𝚞𝚕𝚝𝚜</summary>	
	For this exercise, we clone a github repository as shown below.

```python
# cd to openlane
cd Desktop/work/tools/openlane_working_dir/openlane
# Clone the repository
git clone https://github.com/nickson-jose/vsdstdcelldesign
# cd into repository directory
cd vsdstdcelldesign
# Copy magic tech file to this folder so we can locally edit it for this exercise 
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .
# magic command to open the inverter layout cell pre-built in this repository.
magic -T sky130A.tech sky130_inv.mag &
```
The results of the command execution are shown below:
<p align="center">
             <img src="https://github.com/user-attachments/assets/74858ac2-3699-479f-b2e3-3ba480358ca3"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/08be97c9-604e-4501-bff1-f27c15d1d2df"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/3f4c123f-0025-4f2f-918c-517372479215"/>
</p>
Next we will learn how to fix DRC errors in this inverter cell and get it DRC clean.

<details>
<summary>Lab Exercise:Custom Cell Design usign Magic Layout</summary>
Command “drc check” shows drc errors (highlighted as white dotted regions in layout)
<p align="center">
             <img src="https://github.com/user-attachments/assets/f138321c-9c8d-4ae0-a52d-4bbe95d3e370" width="300"/>
</p>


Command “drc why” shows drc error reason that transistor width is insufficient
<p align="center">
             <img src="https://github.com/user-attachments/assets/d29f2556-55db-4d13-8d0c-ed2cc2a6a67b" width="300"/>
</p>

```python
#Select nwell region
erase nwell
#Click a region to expand the pdiff to remove drc violation 
paint pdiff
#Click a region to expand the ndiff to remove drc violation
paint ndiff
```
<p></p>
With above commands, the DRC violation is fixed

[Above commands are learnt from http://opencircuitdesign.com/magic/index.html]

<p align="center">
             <img src="https://github.com/user-attachments/assets/7c91a171-f29d-4e4e-8d1a-180103348fd4" width="300"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/ab440c08-a441-461c-92c7-bc54071c967e" width="300"/>
</p>

Next we explore more of MAGIC and learn how to interpret DRC rules and how to add missing DRC rules into the technology files and how to fix DRC errors in MAGIC.
</details>	

<details>
<summary>𝙻𝚊𝚋 𝙴𝚡𝚎𝚛𝚌𝚒𝚜𝚎: 𝙲𝚞𝚜𝚝𝚘𝚖 𝙲𝚎𝚕𝚕 𝙳𝚎𝚜𝚒𝚐𝚗 𝙳𝚁𝙲 𝙴𝚡𝚙𝚎𝚛𝚒𝚖𝚎𝚗𝚝𝚜</summary>
DRC Error Fixing Lab
<p align="center">
             <img src="https://github.com/user-attachments/assets/8c41e57b-d096-48a6-a280-f4220e25217d"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/fd88b91d-e2c5-4a73-bfd3-3ba821742347"/>
</p>


Open the poly.mag file
<p align="center">
             <img src="https://github.com/user-attachments/assets/72eba9d5-4a6c-4e2f-bf7c-8601768b1717"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/8ac331ff-dd26-4e23-a6ea-75298e6719c0"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/adcf0a10-f1e2-4ab5-b251-5d149b4afd8f"/>
</p>


Polyres to poly spacing is only 0.21um but it should be atleast 0.48um.
This DRC error is not encoded in the tech file so it is not showing as error but fab cannot fabricate this without issues.

Hence we need to fix the tech file to include this rule and then fix the layout to meet that rule.
<p align="center">
             <img src="https://github.com/user-attachments/assets/2430630c-ef9f-4a5a-8a7c-a83580f6d806"/>
</p>


Before editing techfile
<p align="center">
             <img src="https://github.com/user-attachments/assets/2a4c1431-a51d-44f5-a354-0b558c946f2d"/>
</p>

After editing techfile
<p align="center">
             <img src="https://github.com/user-attachments/assets/fd6526d1-c6e3-4a3b-9318-6bfb3c4f0a9e"/>
</p>


Before editing techfile
<p align="center">
             <img src="https://github.com/user-attachments/assets/d4e28f7a-c425-4849-a96a-98192da9ff25"/>
</p>

After editing techfile
<p align="center">
             <img src="https://github.com/user-attachments/assets/9195d3a4-4e5c-4816-9343-3f82f124a7b0"/>
</p>


In tkcon window we enter the following comands:
<p></p>

```python
tech load sky130A.tech
drc check
```
Now we see a white dotted region showing DRC error for polyres to poly spacing violation.
<p align="center">
             <img src="https://github.com/user-attachments/assets/1b5304f8-f88f-4db6-aef2-864623ba8f68"/>
</p>


Our newly added DRC error message shows up for the *drc why* command after selecting the region of interest in the layout.
<p align="center">
             <img src="https://github.com/user-attachments/assets/001f08e2-bb76-4d91-b5a5-829e712696b4"/>
</p>


We click to make a bounding box around the poly region that we want to copy, then go to Edit and click 'Select Area'.
We then move the cursor to the location where we want to copy and press 'c'.

<p align="center">
             <img src="https://github.com/user-attachments/assets/898381d8-c403-4f39-b01d-02007f6525a8"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/885e9fef-30a4-40d0-84b0-791a618d03dd"/>
</p>



Before editing:
<p align="center">
             <img src="https://github.com/user-attachments/assets/bc91438c-a346-4d43-a2da-3ea64aa08540"/>
</p>

After editing:
<p align="center">
             <img src="https://github.com/user-attachments/assets/f7e980e0-453e-40b4-9daf-b3fd92c2b67c"/>
</p>


After loading updated techfile, we can now see the drc errors for the poly to ndiff and pdiff regions.
<p align="center">
             <img src="https://github.com/user-attachments/assets/bebcd48b-a729-46b5-8b33-9d223f1f5be8"/>
</p>


Fixing errors in difftap.2 rules:
<p align="center">
             <img src="https://github.com/user-attachments/assets/db00e45e-1b3e-4ada-b2a7-e37611f3c338"/>
</p>


difftap.2 rule shows no violation. 
<p align="center">
             <img src="https://github.com/user-attachments/assets/24c2b9fc-0218-46af-aa0f-0b44bd141593"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/271cc3cf-8552-489a-9920-65056dccf013"/>
</p>


These lines are added to the tech file to catch the difftap.2 rule violation.
<p align="center">
             <img src="https://github.com/user-attachments/assets/16d55e84-e5f5-4933-aa13-0964c780d64a"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/ec58add8-5037-4739-b22b-2c237051bc69"/>
</p>


NWELL DRC rule fix:
<p align="center">
             <img src="https://github.com/user-attachments/assets/b766cee1-07dd-4350-9553-0e4e1bebd376"/>
</p>


We open nwell.mag file in magic. The selected region is filled with deep nwell
<p align="center">
             <img src="https://github.com/user-attachments/assets/f053bdaf-d49c-486c-8d1c-f6b97570d78e"/>
</p>

The nwell is drawn as four rectangular regions as highlighted individually above. These 4 regions together form a square nwell region with a hole in the middle without nwell.
<p align="center">
             <img src="https://github.com/user-attachments/assets/c2221106-796f-433e-94bf-33c726954da5"/>
</p>


Deepnwell to nwell width is only 0.56um.
<p align="center">
             <img src="https://github.com/user-attachments/assets/ea2d8782-f178-45f4-b765-67dfdf881f0f"/>
</p>

The drc error region (white dotted region) correctly points out that it should be 1.03um at the least.
<p align="center">
             <img src="https://github.com/user-attachments/assets/66f30e45-1d93-478e-9e9f-81524a6d85ad"/>
</p>


How magic is able to find the inside edge of dnwell not covered with nwell?
It uses a templayer *nwell_missing* where it makes dnwell grow by 0.4um and *and_not* with dnwell shrink of 1.03um and *and-not* with nwell region. If anything remains, then it is a DRC error.
This complicated rule is compute intensive. But in some cases this is the only way to catch DRC errors.
<p align="center">
             <img src="https://github.com/user-attachments/assets/9e17243f-df4b-45d8-860c-f786dec5692d"/>
</p>


Nwell.4 not implemented:
<p align="center">
             <img src="https://github.com/user-attachments/assets/c785b1b1-ddba-4c66-a924-0b15f7a7236b"/>
</p>


Hence there is no DRC error even though no contact is placed on this nwell.
<p align="center">
             <img src="https://github.com/user-attachments/assets/d1d8fc0a-5872-4903-b4fd-5e1cb7f685cd"/>
</p>


These lines are added to the tech file to catch the missing tap contact.
<p align="center">
             <img src="https://github.com/user-attachments/assets/a74d4a83-4fa2-42cd-a7ed-f460b750f388"/>
</p>

The techfile is once again loaded in tkcon window and the drc style is set to full and drc is executed. Now the missing rule is implemented and we get the drc errors as expected.
<p align="center">
             <img src="https://github.com/user-attachments/assets/0625030f-1fd6-4ff5-9a9a-c70de28ec598"/>
</p>


</details>	
<details>
<summary>Lab Exercise:Custom Cell Design SPICE simulation Results</summary>
<p></p>
Extracting spice netlist from layout:
<p align="center">
             <img src="https://github.com/user-attachments/assets/88e3f8d1-3815-4937-9c5d-9e5c6fc6be09"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/f0da9528-fc3e-4154-83bf-5ccc63b1ce33"/>
</p>


File edited for stand-alone simulation in ngspice:
<p align="center">
             <img src="https://github.com/user-attachments/assets/793aed13-5c80-4a5b-897c-45696f569454"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/63d9c07c-754e-497e-bcd9-c8ca8881a0c0"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/33e7eab4-fc2c-4b76-a28b-384318829297"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/b30c3953-47aa-46de-b88e-41490bd497d5"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/0a5b53b9-fdde-4197-86a1-9bf772d2c6da"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/00ec5217-8876-415b-b0a3-29a60f8660a2"/>
</p>

</details>	

<details>
<summary>Lab Exercise:Custom Cell Design Standard Cell Format Results</summary>
<p></p>
For Place and Route, we dont need all layout info (the one available in .mag file). We only need LEF file (the boundary of the cell, the pin locations). Also this way, we can also protect our layout IP.
<p align="center">
             <img src="https://github.com/user-attachments/assets/cde2c1b0-0bbc-4e51-acb6-cd5fb2cfd247"/>
</p>


For us to be able to use a custom layout file for a standard cell and use it in openlane flow, we have to meet certain criteria so that it plays along well with other such standard cells and can be used by the tool for auto placement and routing.
<p></p>
Requirements:
1. The input and output pins of any standard cell should lie on the intersection of the vertical and horizontal tracks.
2. The width of standard cell should be odd multiple of horizontal track pitch.
3. The height of the standard cell should be even multiple of vertical track pitch.


Input and output pins are on li1 layer. So we look for li1 track info. 
<p align="center">
             <img src="https://github.com/user-attachments/assets/06b45147-3803-47f7-9f74-79c7491888ae"/>
</p>
This information is used to set grid size in magic.


This positioning enables the Routing tool to get a metal routing to these pins correctly.
<p align="center">
             <img src="https://github.com/user-attachments/assets/e03c2d84-67a8-4e3d-a488-6d3b11bf5752"/>
</p>


Horizontal pitch matches with the odd multiple of track pitch requirement.
<p align="center">
Width of standard cell = 1.38um = 3 × 0.46um
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/51b203d4-4cc4-4551-b8ad-66d080adfa17"/>
</p>


Vertical pitch matches with the even multiple of track vertical pitch requirement.
<p align="center">
Height of standard cell = 2.72um = 0.34um × 8
</p>

All three requirements are satisfied by our custom standard cell.
<p align="center">
             <img src="https://github.com/user-attachments/assets/dcb9d084-1723-4e55-9d31-c39def0cd7dc"/>
</p>


File is saved as sky130_inv_newdesign.mag
LEF file is generated using the command “lef write” in tkcon window.
<p align="center">
             <img src="https://github.com/user-attachments/assets/3edd6717-03e2-4c57-88a6-55481fcb1eb1"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/938037bc-bc4a-4f95-be2d-dd9e2d8e2c18"/>
</p>


LEF file is generated as shown:
<p align="center">
             <img src="https://github.com/user-attachments/assets/20ab4f59-92ab-4511-989d-727ca961aa7c"/>
</p>

The LEF file and the technology files are copied over to picorv32a src directory:
<p align="center">
             <img src="https://github.com/user-attachments/assets/726f6948-f843-4958-bb29-a6f085dee1ab"/>
</p>

The files are copied and correctly getting listed in the src folder as shown below:
<p align="center">
             <img src="https://github.com/user-attachments/assets/193fa530-91f0-45cb-b2e8-332c521e50e3"/>
</p>


The following highlighted lines are added to the design config.tcl file:
<p align="center">
             <img src="https://github.com/user-attachments/assets/d24b33e2-b11e-4582-866a-df408ab9ae7b"/>
</p>


</details>	
</details>
<details>
<summary>𝚂𝚃𝙰 𝚊𝚗𝚍 𝚃𝚒𝚖𝚒𝚗𝚐 𝚅𝚒𝚘𝚕𝚊𝚝𝚒𝚘𝚗𝚜 𝙵𝚒𝚡 𝚊𝚗𝚍 𝙶𝙳𝚂 𝙶𝚎𝚗𝚎𝚛𝚊𝚝𝚒𝚘𝚗 𝚠𝚒𝚝𝚑 𝙲𝚞𝚜𝚝𝚘𝚖 𝙻𝚒𝚋𝚛𝚊𝚛𝚢 𝙲𝚎𝚕𝚕</summary>	
Starting openlane all over from docker setup.
<p align="center">
             <img src="https://github.com/user-attachments/assets/e6486fbd-d37b-44fe-9d05-9edfaaead14d"/>
</p>

The commands below sets up the new LEF we created into OPENLANE flow.
<p align="center">
             <img src="https://github.com/user-attachments/assets/205b89e6-f521-4fba-857b-0c6d56023f8c"/>
</p>

Run_synthesis command is then executed and the output is shown below:
<p align="center">
             <img src="https://github.com/user-attachments/assets/6533d664-a1ac-49d4-b19b-fe91e20cf479"/>
</p>

Synthesis report file has been opened to note down the total chip area and timing details. We are not getting the correct cell name sky130_inv_newdesign.
This is an issue.

Since we used a new name for the inverter, it seems to have created a problem. 
<p align="center">
             <img src="https://github.com/user-attachments/assets/c4973704-3c49-424e-b378-138565aba69d"/>
</p>

To get the correct cell name we need to edit the characterization library files.
This cell name is changed from *sky130_vsdinv* to *sky130_inv_newdesign*
<p align="center">
             <img src="https://github.com/user-attachments/assets/2d9d8484-c5b5-4b8a-a01a-65c7a265ccae"/>
</p>

This cell name is changed from *sky130_vsdinv* to *sky130_inv_newdesign*
<p align="center">
             <img src="https://github.com/user-attachments/assets/bb64b0d9-19ef-4b95-9da2-ed04b1c366f4"/>
</p>

This cell name is changed from *sky130_vsdinv* to *sky130_inv_newdesign*
<p align="center">
             <img src="https://github.com/user-attachments/assets/bb64b0d9-19ef-4b95-9da2-ed04b1c366f4"/>
</p>

After fixing the library files, we now start over and enter the following commands:
<p></p>

```python
cd Desktop/work/tools/openlane_working_dir/openlane

docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/**.lef*]
add_lefs -src $lefs

run_synthesis
```
<p align="center">
             <img src="https://github.com/user-attachments/assets/66b72b76-c031-41d4-be8c-e51aaf9a9162"/>
</p>

Now the synthesis report is correctly pointing to the new inverter cell name we created!
<p align="center">
             <img src="https://github.com/user-attachments/assets/ca70bea9-bfc8-4109-b28b-5823d00fdc69"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/8272af55-74ba-4001-a646-7abf1249346d"/>
</p>

We reconfigure the settings to improve timing by letting the tool use stronger buffers and allowing for more size but reduce delays in the logic. 
<p align="center">
             <img src="https://github.com/user-attachments/assets/d29de27c-b32f-4ab1-ae06-c2097b0d6c54"/>
</p>

Worst case negative slack is now zero. And the chip area has increased as expected.
<p align="center">
             <img src="https://github.com/user-attachments/assets/5d1faf0d-8735-4698-92f6-77263ded46f8"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/4db717ce-61b7-48a0-9715-a17db5406697"/>
</p>


The flow has failed.
<p align="center">
             <img src="https://github.com/user-attachments/assets/f2f8c917-ef21-4f9f-839b-9a47ba642ae6"/>
</p>

Hence we now try running individual commands that are collectively run by *run_floorplan* tcl file.
<p align="center">
             <img src="https://github.com/user-attachments/assets/b7ae0cfc-e275-474c-b57d-d919fea6a447"/>
</p>
<p align="center">
             <img src="https://github.com/user-attachments/assets/3ddb9dc8-5cd4-4221-92fb-77604342a5eb"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/0b766bc9-0357-44f5-ab75-fb6bb1437dad"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/ae37c34b-9964-488e-bce7-c383e233d8a2"/>
</p>


Placement is completed.
<p align="center">
             <img src="https://github.com/user-attachments/assets/b672b9de-9e62-4f1e-943b-5ce21d284922"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/0d7e2189-6083-4e1f-9b07-febfc48176ed"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/e6f2b23e-bf29-47b9-a7bc-094af80e3db0"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/79454407-3b5a-4586-bc97-bbeab7172301"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/6701f682-0a46-4c7a-aad1-80e175961733"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/88b2aa84-5b61-414a-aef4-177ddb1fdd89"/>
</p>


Let's run STA with *pre-sta.conf*:
<p align="center">
             <img src="https://github.com/user-attachments/assets/90a5d44e-89dd-4aab-8dcd-07d96821063a"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/73297090-a671-44e4-98da-c37a8cf8c0a9"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/7cf1b89e-cf40-4110-b797-79a931b6f4cd"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/9beb4b24-73a1-4eb5-9218-c66eb7f1533a"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/5cb6bfd8-0776-4e9a-bf8c-fadca562fe50"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/d73a01dc-2819-4b9f-939e-fa34215cc4a8"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/ff09c9a7-9005-46f5-b499-e8c3b54cad21"/>
</p>

Let's start over again but this time by trying some configuration settings.
![image](https://github.com/user-attachments/assets/d32ce484-9ac5-4a98-8462-4d6b7dcd9976)
<p align="center">
             <img src="https://github.com/user-attachments/assets/d32ce484-9ac5-4a98-8462-4d6b7dcd9976"/>
</p>

Trying new configuration settings:
<p align="center">
             <img src="https://github.com/user-attachments/assets/64313b23-b526-46f0-93a1-d533c83c1c5d"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/0a0b3572-58bc-406f-8686-877fb27945e8"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/a6196ee5-e74f-4e6b-957f-3ab0770ae675"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/527c5760-19e2-4cd7-8789-9604fe3dfa67"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/b552c3b2-637b-4add-a231-86db677303e8"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/0a8c35b7-aa8d-4b3d-aae9-e91a7bc2996d"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/7700a6b4-7119-4789-8073-a55534a1d53a"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/d41ef052-1014-4fe7-9c36-ea478681505e"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/6f728dfb-13e0-4554-8410-61970bd663db"/>
</p>

Copy current netlist before committing the ECO changes to the verilog file.
<p align="center">
             <img src="https://github.com/user-attachments/assets/be9ef3c3-9e21-4d67-8b8b-57f1fbcd8c95"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/3c29e7ea-320a-4c72-8b47-fc5ce08052f7"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/a0f2a396-55ff-4b9a-8b8f-2efd78b54ebb"/>
</p>

Let's Start over again, this time by using synthesis configuration settings.
<p align="center">
             <img src="https://github.com/user-attachments/assets/b0b8472e-67bb-4878-adfa-5553845f5561"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/1d6790ba-27ff-4058-92df-c93e3be44c29"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/b928afc9-ba85-4f0c-88f3-0438c63d6510"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/91a8e59c-1391-4590-ac7e-2afac95113ea"/>
</p>

Then the *run_placement* command is executed.
<p align="center">
             <img src="https://github.com/user-attachments/assets/390ede01-70cd-496f-b895-4ab6441f8aee"/>
</p>

Next *run_cts* command is executed.
<p align="center">
             <img src="https://github.com/user-attachments/assets/f54f8701-46e8-47cc-985f-362876fe14c3"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/bfdd25cd-54bb-4d42-b66b-5ff2f3d002a9"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/9cf6e418-eebc-42d5-9e58-9873c7328c14"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/dcf0b727-c2f5-4b78-8fb9-c8dd457dc709"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/3bea3682-354b-4a19-a4cb-337a70fc7fd6"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/7bc3f19e-e779-45f1-bf9e-69deaeb22cbb"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/8b1ade5f-8ff6-4c66-8488-c01455530b55"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/099a55a4-389c-45df-bb55-b3e6dcdd067c"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/46f60623-a1a1-477b-9457-ef4b4d4a328c"/>
</p>


<p align="center">
             <img src="https://github.com/user-attachments/assets/db737b3e-0589-4c01-8f4f-3f4aa09ac171"/>
</p>


We could have just continued with the next step which is PDN generation. But in case we want to shutdown the system and start later and continue from where we left, we can use the following commands to do so.
<p align="center">
             <img src="https://github.com/user-attachments/assets/3d498033-b4dc-4220-87aa-3e53bad163cb"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/31a166b0-25b1-43c1-a1df-dad0d990273a"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/b932c4bf-9abe-4e4e-974e-3876b5afcee0"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/dc2fe2d8-8562-4948-ab03-a0c757724a24"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/adc9dd70-ff29-4322-bd56-ed79c1546869"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/88d809b4-c639-4ccb-b17c-f2252ca4057f"/>
</p>
We now run the *run_routing* command to start the routing process. This step takes several iterations for the routing to get completed. 
<p align="center">
             <img src="https://github.com/user-attachments/assets/90a08399-c879-4a4f-a513-3ea578c87cc8"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/6ca95d13-8804-43f3-a105-fed8c131f3d6"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/693ab8a3-c321-40fb-88f7-4ca976c60282"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/09a60b48-0649-40cb-88ac-e369f4940485"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/7b572ba0-9327-4238-a3c8-c10b5ea784ed"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/95052db6-7b5b-4fd9-b498-8225bd4c843e"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/ae02ca82-fe1c-40ae-920c-67cfc1706275"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/888f3f8f-6b1b-4726-b051-0204cf2161df"/>
</p>

The *.SPEF* file is also generated automatically so we proceed with final timing analysis using the SPEF file.
<p align="center">
             <img src="https://github.com/user-attachments/assets/b5007f42-965a-4944-b3e8-c7ec8d0ba04d"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/e90a4b7a-4147-4ec3-8121-a24f64f0cde0"/>
</p>

<p align="center">
             <img src="https://github.com/user-attachments/assets/4f67171d-6d50-4cea-b940-e5969b2573fc"/>
</p>

Next we have to generate GDS file. It is not clear how to proceed further. However, when looked into the *flow.tcl* file, it showed the next steps after routing.
<p align="center">
<img src="https://github.com/user-attachments/assets/df03728f-83af-4533-bc21-d349131ce2ed"/>
</p>

However, running the command *%run_magic* gave an error that the variable DIE_AREA is not defined in *mag_gds.tcl*.
Searching for this *mag_gds.tcl* it is found to be in the *scripts/magic/* folder within openlane.
This file contents are as shown below:
<p align="center">
<img src="https://github.com/user-attachments/assets/b86570c6-5cf3-4b80-b748-396f875c7008"/>
</p>
Since the env variable MAGIC_ZEROIZE_ORIGIN is not defined, the program enters the *else* section and finds the DIE_AREA not to be defined. Lets define the variable MAGIC_ZEROIZE_ORIGIN using the command:

```python
% set ::env(MAGIC_ZEROIZE_ORIGIN) 1

#Now re-run the command.
%magic_run
```

The GDS file is now generated successfully.
<p align="center">
<img src="https://github.com/user-attachments/assets/ba71ced4-a4c9-4fec-8716-a22789956c55"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/c73a03b3-87b4-4fa7-8baa-290685a9bf06"/>
</p>
This concludes the creation of GDS file which can be sent to Foundry for Chip manufacturing.
</details>

<p></p>

<br></br>

<p></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5821c94-e2a3-4782-b9eb-c9cddfbfac3f" width="1200" height="100"/>
</p>

## Acknowledgements
##### Samsung Semiconductor India Research, *sponsor of Chip Design for High School course*
##### Kunal Ghosh, *Co-founder, VSD Corp. Pvt. Ltd.*
##### Mohammed Fayiz Ferosh, *reference github provided by VSD*

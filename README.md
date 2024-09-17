
**THEORY**

In this project we will inculcate a standard cell design based on skywater PDKs and plug it in a design Picorv32, a RISC V CPU core. 
It implements the RISC-V instruction set architecture (ISA).



A brief description of the Picorv32:


![picorv32a core and die](https://github.com/user-attachments/assets/cf1a7986-85ab-42c7-be1d-d3318a901f5d)

The die is the part of a wafer of Silicon or any other material, but in semiconductor industry its Silicon. The core or the are within which chips are contained are compartmented within the core. There are input and output contacts, clocks on the IO pad that surround the core area and is a no logic zone.

The IPs are the intellectual property and they are logic blocks that took some intelligence to be builts.
![picorv32a all parts](https://github.com/user-attachments/assets/14f6fc27-a645-4a94-9f96-1b357931b27a)

Final project showing our chip as encircled on the PCB after being manufactured and packaged by the foundary:
![final project](https://github.com/user-attachments/assets/cae32f48-e6b0-40de-b50c-de9b42502a62)






Pictorial representation of the processes and resources required for Digital ASIC Design
![ASIC Basic](https://github.com/user-attachments/assets/b0a61623-a9ef-40b0-b846-035adb238027)

RTL designs: Basic netlist or a connection of network of the logics. There are several open sources that cater to development of a RTL design: Eg. github.
PDKs : Process design kits, they contain files and resources pertaining to necessary information required for development of an IC.
EDA Tools: They are design automation tool that nculcate the whole physical design flow processes , namely : QFlow, Openroad, Openlane.



Basic ASIC Flow Architecture:
![vsdworkshop (Snapshot 1)  Running  - Oracle VM VirtualBox 17-09-2024 08_33_01](https://github.com/user-attachments/assets/91d79e50-7bdd-48d1-82b9-10abcecab262)


Steps that occur in Physical design:
1) Synthesis: It is the step involving RTL Synthesis
2) Floorplanning: It involves placing the macro as well as the rows used for placement and routing and defines input and output ports.
3) Placement : Placement of component cells in the design.
4) CTS (Clock Tree Synthesis) : Clock network distribution.
5) Routing : Defining network routes.
6) Tapeout : Define final GDSII layout file from routing def file.
7) Signoff : Final step involving DRC, LVS ,Antenna Checks and ERC.

The tools that we utilized in our project are :
1) Yosys Synthesis suite.
2) Openlane RTL2GDS digital design suite.
3) NGSpice for characterization.
4) MAGIC for layout and floorplanning.
5) OpenSTA for static timing analysis. 

The Openlane flow in interactive mode is genereally is as follows:
1) prep -design <design> -tag <tag> <config> -init_design_config -overwrite
2) run_synthesis
3) run_floorplan
4) run_placement
5) run_cts
6) run_routing
7) run_magic
8) run_magic_spice_export
9) run_magic_drc
10) run_netgen
11) run_magic_antenna_clock









**LABS**


**DAY 1**:

1) Openlane loaded and design preparation is isnitiated.
 ![image](https://github.com/user-attachments/assets/07227471-b4b2-4f75-8e08-e2588389e46c)

 2)Synthesis performed in openlane
  ![image](https://github.com/user-attachments/assets/2ce62a89-cbfe-470f-a8c1-e0eff3aa0bc4)

3) Number of cell synthesised is highlighted in the picture below:
   ![image](https://github.com/user-attachments/assets/1d2c8fa0-ae80-45ee-8f5d-4fb0952e4a59)
4) Number of D flip flops is highlighted below:
   ![image](https://github.com/user-attachments/assets/493358d3-7c05-49ab-a14d-082df54181e8)
   Flop ratio = Number of D flip flop/ Number of Cells = 1613/14876= 0.1084296854
6) Configuration README.md files showing all the parameters.
   ![image](https://github.com/user-attachments/assets/2d0fe742-ec41-4a48-834e-f861275f7a04)

   **DAY 2**
   
1) Floorplan.tcl shows the default parameters.
   ![image](https://github.com/user-attachments/assets/4ecd6734-c2f9-46ea-b5e5-0ba41a192e7b)

3)  Floorplanning run successfully
    ![image](https://github.com/user-attachments/assets/328a2928-4f6b-4c85-aee9-cffdd3f24000)

5)  Core utilization is a representation of how much core area is utilized.
    ![image](https://github.com/user-attachments/assets/d24add31-fe4b-47d8-8936-8aeaba09e55d)
7) The die are as highlighted in the def files is 660685 X 671405 
    ![image](https://github.com/user-attachments/assets/635c5e01-0524-4e5e-ad46-765c4e7cf4ea)
9) Running floorplan in magic
    ![image](https://github.com/user-attachments/assets/45d3e1c3-3f83-4f2a-806d-5a0bfb356363)
    ![image](https://github.com/user-attachments/assets/70631889-adcb-40f7-a480-ed0c0a5eb3f7)
12) Zoomed in floorplan showing grid cell and pin cell
    ![image](https://github.com/user-attachments/assets/446ac6aa-9963-4ba7-9b93-e50c7b17b55e)



13) Executing placement in openlane flow
    ![image](https://github.com/user-attachments/assets/85872b00-af58-4c44-b6e0-046091314d58)
14) Placement observed using magic. All the standard cells are within column and are legally placed.
    ![image](https://github.com/user-attachments/assets/a55e3c87-670d-4dec-ae8f-705b3cdb3a30)
15) Pins are equidistant now.
   ![image](https://github.com/user-attachments/assets/fd068e8f-15c1-4d5b-8f39-cec20a588c21)

**DAY 3**

1) Upon changing IOmode variable from floorplan.tcl of configuration in openlane and running floorplanning, it is found that pin configuration has changed.
  ![image](https://github.com/user-attachments/assets/77c4c599-33c3-4065-9ab2-9066ab73dfb6)
  ![image](https://github.com/user-attachments/assets/c3c9efcd-3915-49cc-9376-bd4b76943424)
  ![image](https://github.com/user-attachments/assets/b3689683-3c99-4f4a-ba18-826d99e346fb)
2) Spice deck creation for CMOS inverter. Sky130A.tech file copied
   ![image](https://github.com/user-attachments/assets/dbb82db5-ce2c-418b-b411-a78019c738c9)
   ![image](https://github.com/user-attachments/assets/1848d6be-217a-425a-a143-194a1e94fd17)
3) Load an inverter standard cell layout through magic
   ![image](https://github.com/user-attachments/assets/0f5ec826-9796-4a31-8542-51a7058790e8)
4) tkcon console to interact with the layout
   ![image](https://github.com/user-attachments/assets/4e66d428-bc76-4c48-bab1-82f89d4db4e7)
5) Removal of layer shows DRC errors, as highlighted by white patches in the picture.
   ![image](https://github.com/user-attachments/assets/f1333517-295a-4bd9-9070-fa6b76b9e793)

   
6) Extrack the layout design and use it for ngspice along with it all the parasitic capacitances and resistances will be extracted as well.
   ![image](https://github.com/user-attachments/assets/ab8c6fbc-5462-4e7e-b017-5018ae9b67f3)
7) Check if the new file is created in the vsdstdcelldesign
   ![image](https://github.com/user-attachments/assets/dc8b58f4-2e0e-41f6-8dd2-b612bb55e59e)
8) The spice program initially looks like :
   ![image](https://github.com/user-attachments/assets/a88a630a-6927-44f1-9cdd-a483fc0e099f)
9) Edit the spice program to change the scale as 0.01um, include the nmos and pmos lib files, make all the changes and perform transient analysis.
   ![image](https://github.com/user-attachments/assets/817e24e6-b8d2-4dc7-96f3-3593835a9db6)
   ![image](https://github.com/user-attachments/assets/03430c06-851d-46a8-8f7c-e121fc931807)
   ![image](https://github.com/user-attachments/assets/70752aee-befc-4b3a-b032-c01ab497626b)
10) The following plot is obtained :
   ![image](https://github.com/user-attachments/assets/aa1e42f2-f5e0-47f8-b359-821a0fe93e13)
11) Cell Characterization done on the basis of data points obtained from the curve is :
   ![image](https://github.com/user-attachments/assets/341cf046-4d01-4b68-9134-dc5d9da05cc0)
   
1)	Rise time = 3.901 e-9 – 3.522 e-9 = 0.379 ns
2)	Fall time = 4.541 e-9 – 4.335 e-9 = 0.106 ns
3)	Cell rise delay = 4.500 e-9 – 3.731 e-9 = 0.769 ns
4)	Cell fall delay = 4.438 e-10 – 3.50 e-10 = 0.093 ns

12) Download and install drc_tests and run magic:
   ![image](https://github.com/user-attachments/assets/50a4f97b-ee71-4d76-af61-ff9f1507c9ad)
13) Load met3.mag file on magic to explore the DRC rules:
   ![image](https://github.com/user-attachments/assets/0d377e1b-a6df-4af9-a39a-c0f428cafdd8)
14) Rules pertaining to m3 mentioned on the website
    ![image](https://github.com/user-attachments/assets/e297603a-4fb3-4989-afa5-1632335d1a92)
15) cif see VIA2 is derived command and shows the mask cuts that will finally be available in GDSII. It hold to the DRC rules.
    ![image](https://github.com/user-attachments/assets/24cf2e5f-bf3f-4cde-ad69-b2fcd1ae70ca)

16) Rules pertaining to poly.lib on skywater website in the periphery section of the rules:
    ![image](https://github.com/user-attachments/assets/164c3abd-cc76-4720-9fcc-13703fa3a72d)
17) Poly.lib loaded on magic.
    ![image](https://github.com/user-attachments/assets/bf13cce1-b45b-47d7-bbb3-253ffbc71cb6)
18) DRC rules pertaining to poly as defined 
    ![image](https://github.com/user-attachments/assets/63c2a56b-28bf-4c50-a3ec-3e8e535a3829)
    a) Poly.9 giving error upon editing its drc rules in tech file in response to a DRC check.
    ![image](https://github.com/user-attachments/assets/9195c647-e2fb-42c8-aa96-65b3279af4be)
    b) Similarly for poly.2 upon changing its drc rule in tech file, it is giving an error.
    ![image](https://github.com/user-attachments/assets/49c99bf4-a8b8-4537-a0bb-e9d88fa54b30)


19) Lab to implement poly resistor spacing and diff and tap and seeing those error using drc why command in tkcon
    ![image](https://github.com/user-attachments/assets/6d6ff13e-c864-4b7b-b724-7a122b32d0be)
20) Lab challenge exercise to describe DRC error as a geometrical construct.
  a) Geometric rules pertaining to nwell and their description in tech file:
  ![image](https://github.com/user-attachments/assets/dfa70047-8f20-428a-bad6-e5c4865eece1)
  ![image](https://github.com/user-attachments/assets/21550eb5-0bbe-49a3-b44d-bcd0adfa40c9)
  b) Observe nwell shrink, the are within is highlighted:
  ![image](https://github.com/user-attachments/assets/c8b0595a-6572-4cbd-a874-97653a7cd7ca)
  c) Observe temporary layer, which shows the error
  ![image](https://github.com/user-attachments/assets/94629ec8-c928-4607-bdb4-c5f812210048)

21) Lab to find missing or incomplete rule and fix them. Eg. n-well:
    a) Rules pertaining to n-well
    ![image](https://github.com/user-attachments/assets/c34b1f6b-31ba-4641-b469-4cbf5cbac5c1)
22) Load n-well
    ![image](https://github.com/user-attachments/assets/f34b1f24-dc57-4c40-ab88-b4477067865c)
23) Create a new DRC rule. Copy cifmaxwidth rule to nwell and change name to nwell_untapped.
    ![image](https://github.com/user-attachments/assets/1026bf93-b281-4604-b579-a781dbfdd9fa)
24) Create templayer. Create n well that are tapped and leave all n well that are not tapped.
    ![image](https://github.com/user-attachments/assets/47bee251-9327-499d-9d1f-ed51acf567e0)
25) Wrap the rules in variant drc full as shown. Implying it is only checked for drc style full.
    ![image](https://github.com/user-attachments/assets/be7d1af6-fe2f-44de-bb01-fa5a79d32934)
26) Check implementation of new DRC rule for tapped and untapped nwell:
    ![image](https://github.com/user-attachments/assets/6adea09a-35f3-42eb-96a7-df9a3219c42e)

    **DAY 4**

1) Load tracks.info to show track info from openlane directory
   ![image](https://github.com/user-attachments/assets/cb15bd82-c5dc-4851-a404-219926be4da1)
2) Tracks.info file containing all the tracks’ information, consisting of metal layers and the topmost two lines are horizontal and vertical origin and span
   ![image](https://github.com/user-attachments/assets/99ce4844-508f-4ad6-9278-609aad9b70f9)
3) Create grid, which also useful for routing
   ![image](https://github.com/user-attachments/assets/c8f27b66-490b-407a-a4bf-65d3ed50673d)
4) Lab input and outputs lie at the intersection of horizontal and vertical lines
   ![image](https://github.com/user-attachments/assets/66dd7532-3bde-40f3-8f02-cd3a64da044d)
5) Width and length of std cell are odd multiples of x pitch and ypitch. Here they are 3 and 9.
   ![image](https://github.com/user-attachments/assets/6c7806ec-69ed-485f-b010-6e471c7e75df)
6) To define a port write the following commands in console window after selecting them:
1)	For output port Y:
   
port class output

port use signal

3)	For Input
port class input

port use signal

4)	For VPWR

port class inout

port use power

5)	For VGND

port class inout

port use ground

7) Saved file as sky130_vsdkashinv.mag
   ![image](https://github.com/user-attachments/assets/94f52601-4f48-4b23-af0f-ab745621b3ba)
  ![image](https://github.com/user-attachments/assets/13811b50-c99d-44d4-b1d8-165435ef427e)
8) Lef file created
   ![image](https://github.com/user-attachments/assets/3103e64d-4156-4238-979c-070cde001d0b)
9) Lef file having pins that were converted from ports
    ![image](https://github.com/user-attachments/assets/06f1ce8d-322d-4390-a1b2-4fb8d25e90f9)
10) Export lef file to picorv32a
    ![image](https://github.com/user-attachments/assets/db36ca68-40cc-4c6f-8d9a-8f5d224d1efb)
11) Copying lef file and libraries to src folder
    ![image](https://github.com/user-attachments/assets/0d882471-6a98-4835-b444-c326b890efb7)

12) Synthesis initiated on openlane
    With the following steps:
    prep -design picorv32a -tag 11-09_16-08 -overwrite
    set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
    add_lefs -src $lefs

    ![image](https://github.com/user-attachments/assets/7a174d27-e003-42a7-9729-fe28ecad8841)

    Now forgo the following steps:
      prep -design picorv32a -tag 11-09_16-08 -overwrite

    set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

    add_lefs -src $lefs

    set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

    add_lefs -src $lefs

    echo $::env(SYNTH_STRATEGY)

    set ::env(SYNTH_STRATEGY) "DELAY 3"

    echo $::env(SYNTH_BUFFERING)

    echo $::env(SYNTH_SIZING)

    set ::env(SYNTH_SIZING) 1

    echo $::env(SYNTH_DRIVING_CELL)


14) Parameters optimised to minimise tns and wns value although with the tradeoff of gain in area
    ![image](https://github.com/user-attachments/assets/51f2971e-88be-4d2c-bd70-2e905c60b4f0)
15) Now run the floorplan
    ![image](https://github.com/user-attachments/assets/e5588854-407c-47de-9762-5526c5839d40)
16) On running floorplan we get the following errors
    ![image](https://github.com/user-attachments/assets/c5962bd9-0f92-44d9-b121-f8f23f735318)
Fix them using the following commands :
 1. init_floorplan
 
 2. place_io
 
 3. tap_decap_or

    floorplan.def is created.

16) Run Placement
    ![image](https://github.com/user-attachments/assets/496b40f7-9521-4f5b-b05c-4257899e6ca6)
17) Load placement def file in magic
    ![image](https://github.com/user-attachments/assets/45bc1e1e-72c7-4302-849e-fdda94d1ba89)
18) Expand to see the connectivity to the power and ground rails:
    ![image](https://github.com/user-attachments/assets/32dbd8a6-1b03-40f9-a204-71037cfc0d35)
19) Our cell is in lef placement
    ![image](https://github.com/user-attachments/assets/d639ad04-6889-46ef-9ccc-a55cbfeab2d5)
20) Optimise parameters to reduce output load capacitances
    ![image](https://github.com/user-attachments/assets/0c8f2819-4b04-48a9-9446-3e40c9c6494e)
    Although no pins are present we experiment with pin replacement and output load. Replace pins of net _3697 from 2 to 1
    ![image](https://github.com/user-attachments/assets/701001cc-f8a6-4ac5-9cb3-05e51c459250)
    Observe capacitance to be reduced:
    ![image](https://github.com/user-attachments/assets/d5a81ac6-999c-4302-b500-56416ce78af7)

    > Create pre_sta.config that contains flow and addresses as well as link
    > ![vsdworkshop (Snapshot 1)  Running  - Oracle VM VirtualBox 16-09-2024 03_25_14](https://github.com/user-attachments/assets/a734cf34-5785-4c18-b3f8-ffbc4263d345)
    > Create my_base.sdc file that contains the constraints, whose variables are read by sdc files:
    > ![image](https://github.com/user-attachments/assets/1a861bbd-b6db-426e-adac-4722bf951383)
    > run openSTA outside of flow to get STA results
    > ![image](https://github.com/user-attachments/assets/29427a3a-1f15-4a4a-bd47-da187fe11496)
    > We can explain the above report by probable mismatch in sdc file and config.tcl



21) Run CTS
    ![vsdworkshop (Snapshot 1)  Running  - Oracle VM VirtualBox 17-09-2024 05_42_11](https://github.com/user-attachments/assets/9425cbbd-d332-43f2-a783-634626c5869d)

    **DAY 5**
  
1) Generate PDN
   ![image](https://github.com/user-attachments/assets/b2864949-6d8a-422c-bc2c-34a69fba9f49)

2) Run routing
    >Detailed routing, iterations are happening and memory is left
    ![image](https://github.com/user-attachments/assets/900f8909-57a7-4c74-86f4-2cfa40aab07f)
    >Routing Completed
    >![image](https://github.com/user-attachments/assets/1278c5d3-0ebd-4fc7-b92b-6ad959275c5b)
3) Post routing:
    > Paratics extraction
    ![image](https://github.com/user-attachments/assets/d1a7c90f-de7b-4b58-a6a1-422f814c3159)
    > SPEF file creation:
    ![image](https://github.com/user-attachments/assets/c045d961-71f6-46d2-acca-8413bb11889c)
    > For post routing analysis, the Verilog file we require to do it and we can use same sdc
    ![image](https://github.com/user-attachments/assets/3c79a614-8968-4c38-9e21-8cf638695349)



































   








   












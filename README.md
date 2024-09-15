
**SKY130_D1_SK3**:

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

   **SKY130_D2_SK1**
   
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

**SKY130_D2_SK2**

1) Executing placement in openlane flow
    ![image](https://github.com/user-attachments/assets/85872b00-af58-4c44-b6e0-046091314d58)
2) Placement observed using magic. All the standard cells are within column and are legally placed.
    ![image](https://github.com/user-attachments/assets/a55e3c87-670d-4dec-ae8f-705b3cdb3a30)
3) Pins are equidistant now.
   ![image](https://github.com/user-attachments/assets/fd068e8f-15c1-4d5b-8f39-cec20a588c21)

**SKY130_D3_SK1**

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


**SKY130_D3_SK3**   
   
1) Extrack the layout design and use it for ngspice along with it all the parasitic capacitances and resistances will be extracted as well.
   ![image](https://github.com/user-attachments/assets/ab8c6fbc-5462-4e7e-b017-5018ae9b67f3)
2) Check if the new file is created in the vsdstdcelldesign
   ![image](https://github.com/user-attachments/assets/dc8b58f4-2e0e-41f6-8dd2-b612bb55e59e)
3) The spice program initially looks like :
   ![image](https://github.com/user-attachments/assets/a88a630a-6927-44f1-9cdd-a483fc0e099f)
4) Edit the spice program to change the scale as 0.01um, include the nmos and pmos lib files, make all the changes and perform transient analysis.
   ![image](https://github.com/user-attachments/assets/817e24e6-b8d2-4dc7-96f3-3593835a9db6)
   ![image](https://github.com/user-attachments/assets/03430c06-851d-46a8-8f7c-e121fc931807)
   ![image](https://github.com/user-attachments/assets/70752aee-befc-4b3a-b032-c01ab497626b)
5) The following plot is obtained :
   ![image](https://github.com/user-attachments/assets/aa1e42f2-f5e0-47f8-b359-821a0fe93e13)
6) Cell Characterization done on the basis of data points obtained from the curve is :
   ![image](https://github.com/user-attachments/assets/341cf046-4d01-4b68-9134-dc5d9da05cc0)
   
1)	Rise time = 3.901 e-9 – 3.522 e-9 = 0.379 ns
2)	Fall time = 4.541 e-9 – 4.335 e-9 = 0.106 ns
3)	Cell rise delay = 4.500 e-9 – 3.731 e-9 = 0.769 ns
4)	Cell fall delay = 4.438 e-10 – 3.50 e-10 = 0.093 ns

7) Download and install drc_tests and run magic:
   ![image](https://github.com/user-attachments/assets/50a4f97b-ee71-4d76-af61-ff9f1507c9ad)
8) Load met3.mag file on magic to explore the DRC rules:
   ![image](https://github.com/user-attachments/assets/0d377e1b-a6df-4af9-a39a-c0f428cafdd8)
9) Rules pertaining to m3 mentioned on the website
    ![image](https://github.com/user-attachments/assets/e297603a-4fb3-4989-afa5-1632335d1a92)
10) cif see VIA2 is derived command and shows the mask cuts that will finally be available in GDSII. It hold to the DRC rules.
    ![image](https://github.com/user-attachments/assets/24cf2e5f-bf3f-4cde-ad69-b2fcd1ae70ca)

11) Rules pertaining to poly.lib on skywater website in the periphery section of the rules:
    ![image](https://github.com/user-attachments/assets/164c3abd-cc76-4720-9fcc-13703fa3a72d)
12) Poly.lib loaded on magic.
    ![image](https://github.com/user-attachments/assets/bf13cce1-b45b-47d7-bbb3-253ffbc71cb6)
13) DRC rules pertaining to poly as defined 
    ![image](https://github.com/user-attachments/assets/63c2a56b-28bf-4c50-a3ec-3e8e535a3829)
    a) Poly.9 giving error upon editing its drc rules in response to a DRC check
    ![image](https://github.com/user-attachments/assets/9195c647-e2fb-42c8-aa96-65b3279af4be)
    b) Similarly for poly.2 upon changing its drc rule, it is giving an error.
    ![image](https://github.com/user-attachments/assets/49c99bf4-a8b8-4537-a0bb-e9d88fa54b30)


15) Lab to implement poly resistor spacing and diff and tap and seeing those error using drc why command in tkcon
    ![image](https://github.com/user-attachments/assets/6d6ff13e-c864-4b7b-b724-7a122b32d0be)
16) Lab challenge exercise to describe DRC error as a geometrical construct.
  a) Geometric rules pertaining to nwell and their description in tech file:
  ![image](https://github.com/user-attachments/assets/dfa70047-8f20-428a-bad6-e5c4865eece1)
  ![image](https://github.com/user-attachments/assets/21550eb5-0bbe-49a3-b44d-bcd0adfa40c9)
  b) Observe nwell shrink, the are within is highlighted:
  ![image](https://github.com/user-attachments/assets/c8b0595a-6572-4cbd-a874-97653a7cd7ca)
  c) Observe temporary layer, which shows the error
 ![image](https://github.com/user-attachments/assets/94629ec8-c928-4607-bdb4-c5f812210048)

17) Lab to find missing or incomplete rule and fix them. Eg. n-well:
    a) Rules pertaining to n-well
    ![image](https://github.com/user-attachments/assets/c34b1f6b-31ba-4641-b469-4cbf5cbac5c1)
18) Load n-well
    ![image](https://github.com/user-attachments/assets/f34b1f24-dc57-4c40-ab88-b4477067865c)
19) Create a new DRC rule. Copy cifmaxwidth rule to nwell and change name to nwell_untapped.
    ![image](https://github.com/user-attachments/assets/1026bf93-b281-4604-b579-a781dbfdd9fa)
20) Create templayer. Create n well that are tapped and leave all n well that are not tapped.
    ![image](https://github.com/user-attachments/assets/47bee251-9327-499d-9d1f-ed51acf567e0)
21) Wrap the rules in variant drc full as shown. Implying it is only checked for drc style full.
    ![image](https://github.com/user-attachments/assets/be7d1af6-fe2f-44de-bb01-fa5a79d32934)
22) Check implementation of new DRC rule for tapped and untapped nwell:
    ![image](https://github.com/user-attachments/assets/6adea09a-35f3-42eb-96a7-df9a3219c42e)

    **SKY130_D4_SK1**

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






















   








   












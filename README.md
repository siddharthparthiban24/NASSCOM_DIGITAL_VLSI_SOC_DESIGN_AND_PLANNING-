# NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING
### Complete procedure of RTL to GDS design flow using OPENLANE and SKY130 PDK.
<br><br><br>

# Day 1 - Introduction to Openlane and SKY130 PDK.<br>
## Commands for intializing Picorv32
```
cd Desktop/work/tools/openlane_working_dir/openlane
docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

run_synthesis
```
## Introduction to Openlane
![Image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/351ebe8b796eb3a4fccd99500cbc61c2e573679c/Screenshot%20from%202025-12-12%2022-35-30.png)

## Run_Synthesis
![image_Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/Run_Synthesis_Start.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/Run_Sysnthesis_End.png)

## Generation of Report for the Synthesis 
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/Commands_For_Report.png)

## Report
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/Report.png)

## Number of Cells and D Flip Flops
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/No%20of%20Cells.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/b7deed8769362817946ecbcdb02c359482b7e735/Day%201/no%20of%20DFF.png)

## Calculations of DFF and Flop Ratio
The synthesis report provides two key values:<br>  * Total number of cells in the design<br>  * Total number of D flip-flops (DFFs)<br>
These values are used to compute the Flip-Flop Ratio, which indicates the percentage of sequential elements in the synthesized design.<br><br>
From the Report<br>
Number of Cells = 14876<br>
Number of D Flip Flops = 1613<br>

Formulae is given as Flop Ratio = (Number of D Flip Flops)/ (Number of Cells)<br>

Fop Ratio = 1613/14876 = 0.10842968539<br>
DFF = 0.10842968539 X 100% = 10.84 %
<br><br><br>


# Day 2 - Introduction to Library Cells and Floorplan.<br>
### In this day of work, Floorplan Design is Carried out with following Steps<br><br>
## Command for Run FloorPlan
```
% run_floorplan
```
### Screenshot
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/FloorPlan_Start.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/FloorPlan_End.png)
<br>

## Calculation of Die Area in Microns from floorplan.def
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Die_Area.png)
From the floorplan.def<br> we see that 1 unit= 1000 microns <br> Distance in micron = (value in unit distance )/1000 <br> 
* Die width= (660685-0)/1000 = 660.685 &micro;m<br> 
* Die Height = (671405-0)/1000 = 671.405 &micro;m<br><br>
Total Die Area = 660.685 X 671.405 = 443587.212425 &micro;m<sup>2</sup>

## Load the floorplan in def<br>
#### Commands are<br>
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-12_17-05/results/floorplan/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Flooerplan_Def_in_magic.png)
<br>
#### Equidistant Port
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Equidistant_port.png)
<br>
#### Run the Congestion Aware Palcement for PICORV32A
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Run_Congestion_Aware_Placement.png)
<br><br>
## Load the DEF in magic <br>
#### Commands are<br>
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-12_17-05/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Load_Placement_in_Magic.png)
<br>
#### Standard Cells in the Placement DEF in magic
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/c51aa4c0b3e56c2e90655476161af5dac9daabb9/Day%202/Standard%20Cell.png)

<br><br><br>



# Day 3 - Design of Library Cell.<br>
### Lab Work with the Design of Library Cell with the Magic layout and using the ngspice to reperesent the charactirization of the layout.<br>

#### Cloning the invertor design from the git hub repository. Following command is used.
```
cd Desktop/work/tools/openlane_working_dir/openlane

git clone https://github.com/nickson-jose/vsdstdcelldesign

cd vsdstdcelldesign

cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

ls

magic -T sky130A.tech sky130_inv.mag &

```
#### Terminal Page
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/3c6e67f37746bc1dc5749446ba2cc9a0e799e28f/Day%203/Git_Clone.png)
<br>

#### Image of Layout of the Invertor 
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/3c6e67f37746bc1dc5749446ba2cc9a0e799e28f/Day%203/Magic_Layout.png)
<br>

### Spice Extraction of layout in magic<br>
#### Following Commands is used to extract the spice file for the invertor layout design
```
pwd

extract all

ext2spice cthresh 0 rthresh 0

ext2spice

```
#### Once the above command are typed in the tkon terminal , the spice is generated

![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/3c6e67f37746bc1dc5749446ba2cc9a0e799e28f/Day%203/Spice_File%20Created.png)

#### Edited Spice file
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/629b618733eccfbe01807a2c8642171724cf7d0b/Day%203/Edited_Spice_file.png)

### After the extraction of Spice file, Command for the ngspice must be given
```
ngspice sky130_inv.spice

plot y vs time a
```
#### Command page
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/629b618733eccfbe01807a2c8642171724cf7d0b/Day%203/ngspice_Run.png)
#### The graph is generated
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/629b618733eccfbe01807a2c8642171724cf7d0b/Day%203/ngspice_with_Graph.png)
#### Graph
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/629b618733eccfbe01807a2c8642171724cf7d0b/Day%203/graph.jpeg)

#### Rise time Calculation<br>
Rise Transition time = Time taken by output raise to 80% - Time take by output raise to 20%.

#### Fall transition time calculation<br> 
Fall Transition time = Time taken by output to fall to 20% -  Time taken by output to fall to 20%


### Skywater Process - To Fix the DRC issues in Old magic file
#### Command to view the issue
```
cd

wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

tar xfz drc_tests.tgz

cd drc_tests

ls -al

gvim .magicrc

magic -d XR &
```

#### magicrc File
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/629b618733eccfbe01807a2c8642171724cf7d0b/Day%203/Magicrc%20file.png).
<br><br><br>


# Day 4 - Timing Analysis and Custom Cell Integration.<br>
### In this day of lab session, it deals with the timing analysis , LEF generation , Fixing small DRC errors and post layout verification.<br>

#### In order to fix the minor DRC errors it is important to open the custom invertor layout with the following commands.
Commands are

```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

magic -T sky130A.tech sky130_inv.mag &
```
#### Command Run
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Command%20run.png)

#### Track info of sky130_fd_sc
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Track%20info.png)

#### Commnds to be given in the tkon terminal to set grid
```
help grid

grid 0.46um 0.34um 0.23um 0.17um
```
#### Command run in the tkon terminal
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/set%20grid%20in%20tkon.png)

#### Condition 1 verified
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Condition%201%20verified.png)

#### Condition 2 verified
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/condition%202%20verified.png)

### Save the final layout with the custom name , then opening the layout
#### Command for save and open
```
# Command to save as
save sky130_vsdinv.mag
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
```
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Save%20the%20layout.png).

#### Generation of LEF layout, following command is used
```
# lef command
lef write
```

![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Generate%20LEF.png)

#### Newly Created Lef file
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Newly%20Saved%20Layout.png)

### Copy the newly generated lef and  files to 'picorv32a' design 'src' directory.
#### Commands are
```
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Cmnds%20to%20copy%20necessary%20files%20to%20'picorv32a'%20design%20'src'%20directory.png)

### Edit the Generated config.tcl file
#### Commands are
```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```
#### Edited config.tcl file
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Edit%20Config.tcl%20file.png)

### Now to run the openlane commands for the synthesis and floorplan
#### Commands are
```
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

run_synthesis

```
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/opening%20of%20openlane.png)<br>

#### Run Synthesis
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/run_synthesis.png)<br>

#### Commands to view and change the timing parameters.
```
prep -design picorv32a -tag 24-03_10-03 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

echo $::env(SYNTH_STRATEGY)

set ::env(SYNTH_STRATEGY) "DELAY 3"

echo $::env(SYNTH_BUFFERING)

echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

echo $::env(SYNTH_DRIVING_CELL)

run_synthesis

```
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Commands%20to%20view%20and%20change%20parameters.png)<br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/run_synthesis.png) <br>

#### Inorder to avoid the unexpected and unexplained error during the Floorplan process we do follow the below commands based on the Openlane_Commands.amd.
#### Commands are<br>
```

init_floorplan
place_io
tap_decap_or

```
#### Command Run
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Run_Floorplan-1.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Run_Floorplan-2.png)<br><br>


### Commands to load placement def in magic in another terminal
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```
#### Placement DEF in magic 
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/placement%20def%20in%20magic.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/placement%20def%20in%20magic_1.png)<br><br>

### Post-Synthesis timing analysis using Open STA tool<br>
#### Following Commands are used to invoke the OpenLANE flow include new lef and perform synthesis<br>
```
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

set ::env(SYNTH_SIZING) 1

run_synthesis

```
#### Completion of run_synthesis process <br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/run_synthesis.png).

### Newly Created "pre_sta.conf" for STA analysis
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Run%20STA_1.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Run_STA_2.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2f03417962b3b903dfffb5c75e4eb7044724bede/Day%204/Run_STA_3.png)<br><br>
<br>

# Day 5- Final Rpocedure for RTL2GDS using TritonRoute and OpenSTA<br>
### The last day of the workshop deals with the detailed routing using TritonRoute and post-route timing analysis using OpenSTA to complete the RTL-to-GDSII flow.<br><br>

### Power generation of PDN and Explore the PDN layout<br>
#### Commands for Openlane and Newly added lef followed by run_synthesis , run_placement and generation of pdn file as follow<br>
```
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

set ::env(SYNTH_STRATEGY) "DELAY 3"

set ::env(SYNTH_SIZING) 1


run_synthesis

init_floorplan
place_io
tap_decap_or

run_placement

run_cts

gen_pdn

```
#### Images of the commands as follow
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_Synthesis.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_Synthesis_Successfull.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_Placement.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_Placement_Successfull.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_PDN.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Run_PDN_Successfull.png)<br><br>

#### Commads to load the PDN in def magic<br><br>
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-12_16-22/tmp/floorplan/


magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &

```
#### Image of Commands and PDN in def
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Commands%20to%20lead%20PDN%20in%20def.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/PDN%20in%20def_1.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/PDN%20in%20def_2.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/PDN%20in%20def_3.png)<br><br>

### Perform Detailed routing using TritonRoute and to explore it<br><br>
#### Commands are<br>
```
echo $::env(CURRENT_DEF)

echo $::env(ROUTING_STRATEGY)

run_routing
```
#### Image sif Routing Run<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routing_Run_1.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routing_Run_2.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routing_run_Successful.png)<br><br>

#### Commands to load Routing in DEf magic 
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-12_16-22/results/routing/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &

```
#### Image of the command
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Commands%20for%20Routing%20Def.png)<br><br>

#### Routing in def magic<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routed_def_1.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routed_def_2.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Routed_def_3.png)<br><br>

#### Rotung Guide in New Terminal
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Route_Guide.png)<br><br>

### Post-Route Extraction using SPEF extractor<br>
#### Commands for SPEf Extraction<br>
```

cd Desktop/work/tools/openlane_working_dir/openlane/scripts/spef_extractor

python3 main.py \
  --def_file /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-12_16-22/results/routing/picorv32a.def \
  --lef_file /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-12_16-22/tmp/merged.lef
```
#### Image of the Commands runned
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Commands_Post-route%20Extraction.png)<br><br>

### Post-Route OpenSTA time analysis
#### Commands are
```
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/15-12_16-22/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/15-12_16-22/results/routing/picorv32a.def

write_db pico_route.db

read_db pico_route.db

read_verilog /openLANE_flow/designs/picorv32a/runs/15-12_16-22/results/synthesis/picorv32a.synthesis_preroute.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

read_spef /openLANE_flow/designs/picorv32a/runs/15-12_16-22/results/routing/picorv32a.spef

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

exit

```
#### Images of Commands Runned and the Report Generated<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Post_Route_OpenSTA.png)<br><br>
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/post_Route_OpenSTA_1.png)
![image Alt](https://github.com/siddharthparthiban24/NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-/blob/2d9435fb9a9f9746a27fc27e2df99dc9c2dfbda2/Day%205/Post_Route_OpenSTA_2.png)<br><br>






































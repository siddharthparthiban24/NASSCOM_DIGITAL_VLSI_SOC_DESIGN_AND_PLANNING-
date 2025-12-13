# NASSCOM_DIGITAL_VLSI_SOC_DESIGN_AND_PLANNING-
### Complete procedure of RTL to GDS design flow using OPENLANE and SKY130 PDK.

# Day 1
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


# Day 2
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












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



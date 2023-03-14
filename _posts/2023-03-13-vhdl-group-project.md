---
title: COEN6741 Computer Architecture and Design -  Group Project
date: 2023-03-12 17:10:08 -0500
categories: [Concordia, COEN6741 Computer Architecturea and Design]
tags: [vhdl] # TAG names should always be lowercase
---

# Project Description

The idea of this project is to design a **simple pipelined processor**, called Mini-MIPS, which is a subset of a **32-bit architecture (MIPS)** similar to the RISC-V as described in the textbook (Appendix A). Mini-MIPS uses the same **3 instruction formats** of MIPS (**R, I and J-types**) to implement one of the following variants of instruction sets (each group will be assigned a particular variant of instruction set):

- Variant 1:
  NOR, SLL, XOR, ANDI, SUBUI, ADD, BEQ, LW, SB, JR and J.
- Variant 2:
  OR, SRL, XNOR, ANDI, SUBI, ADDU, BNE, LB, SH, JR and J.
- Variant 3:
  NORI, SRL, XOR, NANDI, SUBU, ADDI, BEQ, LH, SW, JR and J.
- Variant 4:
  ORI, SLL, XNOR, NAND, SUBI, ADDIU, BNE, LH, SB, JR and J.

It will be assumed that the **memory** can be accessed in **one clock cycle** and works synchronously with the CPU (i.e., no need to provide explicit external memory control). Your group should proceed step by step towards building the CPU by:

1. Understanding and analyzing the behavior of each **instruction**
2. Defining the detailed micro-operations and encoding of each instruction
3. Identifying **which operations will be parallelized** to obtain the pipelined CPU
4. Designing a detailed **block diagram** of the CPU
5. Partitioning the blocks into **Datapath and Control Unit**
6. Designing each of the blocks of the Datapath at the **RT- level** (no need to go at the gate level)
7. Designing the **Control Unit** including: **decoding, datapath control, pipeline control, hazard control**, etc. (the control design can be left at the **FSM level**)
8. Putting all blocks together to get the full CPU
9. Simulate your CPU with a comprehensive test assembly program
   Special attention should be given to the pipeline design. Your CPU should be structural hazards free. Data hazards and control hazards should be solved with the appropriate techniques learned in class.

## Lanuage

- VHDL

## SSH Remote Accessing **ModelSim**

- Launch Xming

  - install X-Server software such as [Xming](https://sourceforge.net/projects/xming/)

- VPN Connect

  - [Install](https://adsys1.concordia.ca/vpnclient/Download_VPN.aspx)

  - Configure VPN
    ![vpn configuration](vpn.jpg)

- PuTTy Connect ([Model Sim Tutorial Video](https://www.econcordia.com/courses/computer_architecture/dynamicvideo.aspx?filename=lesson0/COEN6741_Course_Lab_Tutorial))
  - Host Name:
    - login.encs.concordia.ca
    - computation.encs.concordia.ca
  - Connection > SSH > X11 > Enable x11 forwarding
  - login as: x_limin

### Testing **ModelSim** tool

```shell
> source /CMC/ENVIRONMENT/modelsim.env
<!-- make the tool run -->
> vsim &
```

#### Create Project

- Project Name
- Project Location (default: /nfs/home/x/x_limin -> custom: /nfs/home/x/x_limin/COEN6741)

  => OK

#### Add Existing File

- Browse > add > FA.vhd FA_TB.vhd
- Right Click > Compile > Compile All > should have no errors
- Bottom panel > Library > work > testbench_full_adder > behavior > Right Click > **Simulate** (going to test the full_adder)
- Right Click > Add > To Wave > Signals In Design
  ![](https://raw.githubusercontent.com/BBeerBear/blog_img/master/md/vhdl/Screenshot%202023-03-11%20222659.png)

### Testing **Precision RTL** tool

```shell
> source /CMC/ENVIRONMENT/fpga_advantage.env
> precision &
```

#### New Project

- Project Name
- Project Directory

  => OK

#### Add Input File

- Add FA.vhd
- Project Settings
  ![project settings](https://raw.githubusercontent.com/BBeerBear/blog_img/master/md/vhdl/Screenshot%202023-03-11%20224428.png)
- Left Panel > Design > Compile > Synthesize >
  ![Synthesize](https://raw.githubusercontent.com/BBeerBear/blog_img/master/md/vhdl/Screenshot%202023-03-11%20225019.png)
- Click Tech Schem
  ![Tech Schem](https://raw.githubusercontent.com/BBeerBear/blog_img/master/md/vhdl/Screenshot%202023-03-11%20225256.png)
- Show Repo
  ![Repo](https://raw.githubusercontent.com/BBeerBear/blog_img/master/md/vhdl/Screenshot%202023-03-11%20225557.png)

  [More Tutorials of Digital Logic Simulation and Synthesis Using Modelsim, Precision RTL](https://aits.encs.concordia.ca/helpdesk/resource/tutorial.html)

# Project Composition

- report documenting above tasks
- poster
- video presentation
  - main decisions
  - challenges

The load of the project should be distributed among members of the group, e.g. `architecture design, RTL design, control, datapath, pipeline handling, VHDL/Verilog coding, CAD implementation, simulation, report writing, poster design, video production, presentation, etc.`

## Project Report

### documenting the following tasks:

1. Description of each instruction (encoding, micro-operations, pipelined execution)
2. Detailed block diagram of the CPU
3. Description of the Datapath and Control Unit
4. Design of each block of the Datapath at RTL
5. Design of the Control Unit including: decoding, datapath control, pipeline control, hazard control, etc.
6. Writing a test assembly program (testbench) to test many pipeline scenarios
7. Report of simulation results and analysis

### cover page

### sections:

1. Introduction
2. Instruction Set Architecture Design and Encoding
3. Datapath Design
4. Control Unit Design
5. Simulation and Testing Results
6. Conclusions
7. References

## Project Poster Guidelines (4%)

1. Objectives
2. Instruction Set Architecture Design and Encoding
3. Datapath Design
4. Control Unit Design
5. Simulation and Testing Results
6. Conclusions

PDF format

## Project Video Presentation Guidelines (2%)

## Project Code Guidelines (2%)

- VHDL/Verilog code
- ReadME

## Project Demonstration Guidelines (4%)

TA meeting with ALL GROUP MEMBERS via Zoom

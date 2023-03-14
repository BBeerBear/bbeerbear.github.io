---
title: VHDL Learning
date: 2023-03-12 17:10:08 -0500
categories: [VHDL, Introduction]
tags: [vhdl] # TAG names should always be lowercase
img_path: /assets/img/posts/java/io
---

# Term

## FPGA

FPGA stands for Field-Programmable Gate Array. It is an integrated circuit that can be programmed after it has been manufactured, allowing it to be reconfigured for a wide range of different digital circuit designs.

Unlike fixed-function circuits such as ASICs (Application-Specific Integrated Circuits) that are designed for specific tasks, FPGAs can be customized to perform different tasks by programming the gate array with a specific configuration of logic gates and interconnects. This makes them highly versatile and useful for a wide range of applications, from aerospace and defense to consumer electronics and telecommunications.

FPGAs are commonly used in applications that require high-speed data processing, low latency, and real-time performance. They are also used in prototyping and rapid development of hardware designs, as they offer a quick and flexible way to test and optimize digital circuits.

## Gate

In digital electronics, a gate is a fundamental building block of a digital circuit. It is an **electronic device that performs a specific logical function** on one or more binary inputs to produce a single binary output. The most common types of gates are the AND, OR, and NOT gates.

## Building block

In electronics and digital logic, basic building blocks such as logic gates (such as AND, OR, NOT gates) and flip-flops (such as D-flip-flops) are used to build more complex digital circuits. These building blocks can be combined in various ways to create circuits that perform specific functions, such as arithmetic operations or data storage.

## flip-flop

In digital electronics, a flip-flop is a sequential logic circuit that can **store a single bit of binary data (either 0 or 1) and change its output state based on clock pulses and input signals**. Flip-flops are used in digital circuits for storing data, synchronizing signals, and performing other functions.

There are several types of flip-flops, but the most commonly used ones are the D flip-flop, JK flip-flop, and SR flip-flop.

A **D flip-flop** has a single data input (D) and a clock input (CLK), and it stores the value of D at the instant the clock signal transitions from low to high (or high to low, depending on the specific design). The output (Q) of the D flip-flop is the value stored in the flip-flop and is updated only when there is a clock transition. The complement of the output (Q') is also available at the output.

A JK flip-flop has two inputs (J and K) in addition to the clock input. The output of a JK flip-flop depends on the state of the inputs and the clock signal. The J and K inputs allow the JK flip-flop to be used as a toggle or a frequency divider, among other applications.

An SR flip-flop has two inputs (S and R) in addition to the clock input. The output of an SR flip-flop is set to 1 when the S input is 1 and the R input is 0, and it is reset to 0 when the R input is 1 and the S input is 0. When both inputs are 1, the output state is indeterminate.

Flip-flops are used in various digital circuits such as registers, counters, and memory elements. They are essential building blocks in digital systems and play a crucial role in the storage and manipulation of digital data.

## Schematics (**Logic-level**)

Schematics (short for schematic diagrams) are **graphical representations of electrical or electronic circuits** using standardized symbols and notation. Schematics are used to convey the functional relationship between components and the flow of electrical signals in a circuit.

A typical schematic diagram shows the electrical connections between various components in a circuit, such as resistors, capacitors, inductors, transistors, diodes, and integrated circuits. Schematics may also include symbols for power sources, ground connections, and test points.

Schematics are important tools for understanding and designing electronic circuits, and they are commonly used by engineers, technicians, and hobbyists in the electronics industry. They provide a concise and clear representation of a circuit's function and allow designers to easily communicate their ideas to others.

In addition to the standard symbols for components, schematics may also include additional information such as component values, voltage levels, and other important parameters. Schematics may be drawn by hand, using specialized software, or a combination of both.

## VHDL (**Behavioral Description**)

VHDL (VHSIC Hardware Description Language) is a programming language used for describing the **behavior** of digital circuits and systems. VHDL is a standard language used for **designing digital circuits and systems at different levels** of abstraction, ranging from high-level system-level design to low-level gate-level design.

VHDL was developed by the United States Department of Defense in the early 1980s as a part of the Very High-Speed Integrated Circuit (VHSIC) program. The language was initially developed to help automate the design process of digital circuits for military applications, but it has since become widely used in the commercial electronics industry.

VHDL provides a means of describing the behavior of a digital circuit or system using a set of concurrent processes and signals. The language allows designers to define the functionality of a circuit or system at **different levels** of abstraction, ranging from **behavioral models to detailed gate-level descriptions**.

VHDL also supports a wide range of **simulation and synthesis tools**, allowing designers to **simulate the behavior of a circuit or system and synthesize it into hardware implementations such as FPGAs (Field-Programmable Gate Arrays)** and ASICs (Application-Specific Integrated Circuits).

VHDL has become an important tool for digital system design and is used extensively in the electronics industry for applications such as digital signal processing, communications, and control systems, among others.

# VHDL Syntax

## Interface (VHDL Entity)

Define all the **inputs and outputs**

### Entity Syntax

```vhdl
entity identifier is
    [port (port interface list);]
end [entity] [identifier];
```

Example

```vhdl
entity MUX is
    port ( A   : in bit;
           B   : in bit;
           SEL : in bit;
           C   : out bit);
end MUX;
```

## Behavior (VHDL Architecture)

Describe the functional operation

> Architecture
>
> > Concurrent Statements
> >
> > Process
> >
> > > Sequential Statements
> >
> > Concurrent Statements
> >
> > Process
> >
> > > Sequential Statements

### Architecture Structure

Example of Complete Component

```vhdl
entity SEQCON is
  port ( A    : in bit;
         B    : in bit;
         C    : out bit);
end SEQCON;

architecture BEHAV of SEQCON is
signal C: bit; -- Internal Signal
begin

-- Concurrent Statement
D <= not C;
-- Process
process (A, B)
begin
  if A = '1' or B = '1'
    C <= '1';
  else then
    C <= '0';
end process;

end BEHAV;

```

### Process

Contains Only **Sequential** Statements

Execute **Concurrently** with other Processes

#### Syntax

```vhdl
process_label: process (signal list)
begin
end process [process_label]
```

Example

```vhdl
MUX: process (A, B, SEL)
begin
    if SEL = '1' then
        C <= A;
    else
        C <= B;
    end if;
end process;
```

Rules

- Executes when signal in sensitivity list changes
- Only contains sequential statements
- Signal assignment only occur at the **end process** statement
- Signals get the last executed assignment

### Vectors

A bit_vector is a **group/array of bits**

Using **double quote** for bit_vector value instead of single quote for bit value

```vhdl
entity VECTOREX is
  port ( Y_NIB    : in bit_vector(3 downto 0);  -- bit_vector(right index direction left index)
         Z_BYTE   : out bit_vector(7 downto 0));
end VECTOREX;

architecture BEHAV of VECTOREX is
begin

process (Y_NIB)
begin
  if Y_NIB = "0000" then
    Z_BYTE <= "01010101";
  else
    Z_BYTE <= "10101010";
end process;

end BEHAV;
```

# VHDL Simulators

- Modelsim (Intel/Altera)
- Vivado (Xilinx)
- GHDL
- EDAplayground

## First VHDL Design

### Step

1. Install

   [Modelsim Install](https://www.intel.com/content/www/us/en/software-kit/660907/intel-quartus-prime-lite-edition-design-software-version-20-1-1-for-windows.html)

2. Enter VHDL Code with Text Editor

3. Save VHDL file as design_name.vhd

4. Check for syntax errors with compiling

5. Start simulation

6. Add signals to the Waveform

7. Force inputs -> run -> force input

### Practice

We will create our first VHDL design, and then simulate the design to make sure it is correct.

The design will have three inputs :

1. current_temp , a 7 bit vector, as an input

2. desired_temp, a 7 bit vector, as an input

3. display_select, a signle bit

The design will have one output, temp_display.

The logic we want is that if the display_select is a '1' we want to put current_temp out on temp_display, but if the display_select is a '0', we want to put desired_temp on the output temp_display.

You should create an entity and architecture for this lab. You should then simulate in either Modelsim or Vivado.

**Questions for this assignment**

What will be the basic structure of you design, and how will you get the VHDL design to accomplish the objectives?

1. Create a VHDL file using notepad++

   ```vhdl
   entity TEMPMUX is
     port ( CURRENT_TEMP    : in  bit_vector(6 downto 0);
            DESIRED_TEMP    : in  bit_vector(6 downto 0);
            DISPLAY_SELECT  : in  bit;
            TEMP_DISPLAY    : out bit_vector(6 downto 0));
   end TEMPMUX;

   architecture RTL of TEMPMUX is
   begin

   process (CURRENT_TEMP, DESIRED_TEMP, DISPLAY_SELECT)
     begin
       if DISPLAY_SELECT = '1'
         then TEMP_DISPLAY <= CURRENT_TEMP;
       else
         then TEMP_DISPLAY <= DESIRED_TEMP;
       end if
     end process;

   end RTL;
   ```

2. Compile
   Open Modelsim > Change Directory > Compile > Select the file \*\*.vhd

3. Simulate

   - Choose file: Simulate > Work > \*\*.vhd
   - **Default** window > Select tempmux & Right Click [Add Wave] > Select the Signal & Right Click [Force Selected Signal] > Change default signal "0000000" to "0101010"

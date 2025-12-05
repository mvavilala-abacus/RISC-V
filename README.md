RISC-V Single-Cycle Processor Design

This repository contains a simple and easy to understand implementation of a RISC-V single-cycle processor (RV32I). The goal of this project is to help beginners understand how a processor is structured and how all the components work together

Main Components of the Processor

A basic single-cycle RISC-V processor is built around four important hardware blocks:

1. Program Counter

   Holds the address of the current instruction and updates every cycle

2. Instruction Memory

   Stores all program instructions and provides the instruction at the PC address
   
3. Register File
   
   Contains 32 registers (x0–x31)

   Used to read input values and write back computation results

4. Data Memory
   
   Used for load and store operations during execution

   These blocks form the core of the architecture, but they need additional components to connect everything properly
   


Supporting Components

→ Multiplexers

Multiplexers help choose the correct data source for different operations:

    • PCSrc MUX: Selects between PC+4 and branch/jump target

    • ALUSrc MUX: Selects ALU input between a register value or an immediate

    • ResultSrc MUX: Chooses what value goes back into the register file

→ Adders

    • PCPlus4: Adds 4 to the PC to move to the next instruction

    • PCTarget: Calculates the branch/jump target using PC + immediate

→ Arithmetic Logic Unit

Handles all arithmetic and logical operations such as add, subtract, AND, OR, shifts, and comparisons

→ ALU Control Unit (ALU CU)

Decides which ALU operation to perform, based on the instruction
This includes:

        • The Main Decoder, which generates control signals

        • The ALU Decoder, which interprets funct3/funct7 fields

→ Extend Unit

Extracts and sign-extends immediate values from instruction formats like I-type, S-type, B-type, U-type, and J-type

→ Datapath

The datapath connects all the modules together

It defines how instructions move through the processor and how results are produced and stored









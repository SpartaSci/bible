---
aliases: []
---
> a description of the connectivity of electronic circuit
It contains the list of required cells and how they are connected together


# from Register Transfer Level to logic level 

by means of a [[hardware/VLSI and IP/logic synthesis|logic synthesis]]

To build the circuit manually, we need to:
1. Translate the [[hardware/VLSI and IP/RTL - register transfer level|RTL]] description to a logic level
	1. Map register to flip-flop
	2. Map the adder to a number of full adder

For each full adder determinate the necessary gates (AND, OR)
Obtain a **netlist** detailing these connections, that is not the final result. Each elements is made of transistors that must be properly sized and placed on the silicon chip


Using a *cell library* provides several views of each cell

- The **layout view** shows how the cell should be physically arranged on the chip 
- The **logic behaviour view** shows the functionality (e.g a two input AND)
- The **transistor level description** details the internal transistor structure

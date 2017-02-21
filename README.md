# CS385SemesterProject

By: Kyle Sturmer and Scott Perretta

CS385 Semester Project: Building a mini MIPS machine (maximum grade 45 points including the presentation)

Note that this is a team project. So, you need to form teams of 2-3 members to accomplish it.

Description: Design a simplified version of a MIPS machine and write Verilog programs that describe its structure and simulate its functioning. Use gate-level modeling for all components unless otherwise specified. The machine should include the following components:

General purpose registers (register file): 4 registers, 16-bit long, numbered 0 - 3. Register $0 must contain 0 (read-only). Implemented by D flip-flops with gate-level modeling.
Other registers: 16-bit program counter, pipeline registers. Implemented by reg vectors in Verilog.
Istruction Memory. Word size: 16 bits, word addressed, size: 1024 bytes. Implemented by reg vectors in Verilog.
Data Memory. Word size: 16 bits, byte addressed, size: 1024 bytes. Implemented by reg vectors in Verilog.
Data Cache (optional): direct mapped, write-through, 16-bit block size, size: 8 blocks. Any kind of Verilog model accepted.
ALU: 16-bit data, 3-bit control. Functions: and, or, add, sub, slt.
Control unit: may be implemented by behavioral modeling.
Other components necessary to connect the main components: multiplexes and decoders implemented by gate-level modeling.
Instruction set

Instruction	Opcode
add	0000
sub	0001
and	0010
or	0011
addi	0100
lw	0101
sw	0110
slt	0111
beq	1000
bne	1001
Instruction formats:

R-format (add, sub, and, or, slt)

op	rs	rt	rd	unused
4	2	2	2	6
I-format (addi, lw, sw, beq, bne)

op	rs	rt	address / value
4	2	2	8
Restrictions:

Use structural (gate level) modeling for all components except for the program counter, memories, and pipeline registers.
Implement a pipelined datapath and control.
Extra credit (maximum 5 points): Implementing a data cache, additional MIPS instructions, or improvements of the pipeline (forwarding or stalling). For implementing the data cache see cache.vl, cache2.vl. For additional MIPS instructions see "Implementing Jumps" and Fig. 4-24 on pages 270-271.

Testing: To test the MIPS machine write a simple program that includes arithmetic (add, sub), data transfer (lw, sw) and branch (beq or bne) instructions. Use the addi instruction to introduce numeric constants in your program. For example, this may be a program that sums up 5 consecutive memory words by using a loop and stores the result in a register. Include in your report:

The assembly source of the test program with comments explaining the algortihm
The machine code (the contents of the memory)
Simulation results obtained by running the Verilog program. To monitor the execution of the test program for each instruction display the value at the write data input of the register file. For the branch instructions show results from both decisions (branch taken and branch not taken). Show the PC in the simulation output. For the pipelined processor show results with and without nop's that demonstarte the pipeline hazards.
Progress reports: Three progress reports describing the current status of the project and including the design of the major components of the MIPS machine should be submitted through Blackboard Learn. Each report must include:

The names of the team members  and the tasks that each one accomplished.
A detailed description of the instruction set architecture of the current version of the CPU (instruction codes, formats, meaning). 
Logic diagrams or truth tables (for non-gate level designed modules) of the CPU and each of its major components (ALU, regfile, control unit) with labels for all components and data/control signals corresponding exactly to the modules, input/outputs and wire names used in the Verilog code.
The Verilog source code including detailed comment for each module defined or used.
Test results showing the correct functioning of the CPU by running a test program. The source and the machine language translation of the program must be included too.
The schedule for the progress reports and the presentation is the following:

Due on March 1: A simpilfied single-cycle datapath capable of executing the addi instruction and all R-type instructions. Major components: Instruction memory, ALU, and Register File. Use template files: ALU4.vl (redesign mux's at gate-level and extend it to 16 bit) and regfile.vl (change the D flip-flops with 16-bit registers and redesign mux4x1 using gate-level modeling and extend it to 16-bit data). See the behavioral implementation mips-r-type_addi.vl. For testing use the test program test-r-addi.asm and adjust it to the 16-bit version of MIPS following the requirements given in section "Testing".
Due on TBD: Complete single-cycle datapath. Implement all instructions and run a complete test program as explained in section "Testing". See the behavioral model of MIPS mips-simple.vl for the implementation of the data memory and branching logic. Use the test program from mips-simple.vl extended with the bne instruction and run it with different data to simulate both branch decisions (taken and not taken). Show the PC in the simulation output.
Due on TBD: 3-stage pipelined datapath for addi and R-type instructions, where the third stage combines EX, MEM and WB stages in the 5-stage standard MIPS pipeline. Use the 3-stage behavioural model mips-pipe3.vl and make the necessary changes. For testing use the test program from mips-pipe3.vl and adjust it to the project 16-bit architecture. Include in the report: A top-level diagram of the datapath, Verilog source files and test results. The test results should include simulations with and without nop's that demonstarte the pipeline hazards.
TBD: Semester project presentation (5 pts.). Prepare presentation slides (PPT or PDF) and make a 10-15 min presentation of your project. The slides and the presentation should target a general audience of CS students who have not taken the Computer Architecture class. Every team member should present his/her work as a part of the project.
Final Project: Implement the final version of the complete pipelined datapath. Use the behavioural model mips-pipe.vl and make the necessary changes. Write a general description of the machine and short description of each major component, include the Verilog code with comments and results from running the Verilog program simulating the MIPS test program (see the "Testing" section above).

Due on TBD: Submission of the final project. Submit the final project report as Word, HTML or PDF documents in Blackboard Learn. The submission must inlcude the following items:

The report file with a general description of the machine architecture, diagrams/truth tables for the major components, instruction set and format, and description of each major component. The report should also inlcude:
The test program with comment showing the result that each instruction produces and Verilog simulation output that matches these results. Follow the directions in section Testing above.
The Verilog source code with comment.
The presentation slides (PPT or PDF).  The presentation slides should target a general audience of CS students who have not taken the Computer Architecture class.

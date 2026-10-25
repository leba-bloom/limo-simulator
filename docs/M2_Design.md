# LIMO - M2 Simulator Design

## 1. Architecture Overview
We use a standard 5-stage pipeline: IF, ID, EX, MEM, WB.

**Branch Resolution:** Branches resolve in the ID stage. This creates a 1-cycle flush penalty (which we will quantify against Ripes in M5).
**Memory:** Harvard architecture (separate 4KB Instruction and 4KB Data memories).

## 2. Pipeline Register Data Model
- **IF/ID:** `pc`, `instr`, `pcPlus4`, `valid`
- **ID/EX:** `pc`, `rs1`, `rs2`, `rd`, `rs1Val`, `rs2Val`, `imm`, `ctrl` (RegWrite, ALUSrc, ALUOp, MemRead, MemWrite, MemToReg, Branch, Jump)
- **EX/MEM:** `aluResult`, `rs2Val`, `rd`, `ctrl`
- **MEM/WB:** `memData`, `aluResult`, `rd`, `ctrl`

## 3. Interface Wireframes & Design
*(check live prototype at the GitHub Pages link)*
- **Editor View:** Textarea with line numbers, Assemble/Step/Run/Reset buttons, Forwarding toggle.
- **Datapath View:** 5-stage diagram with live value labels on wires.
- **Control View:** Table of 8 control signals and their current state.
- **Hazards View:** RAW, load-use, and control hazard indicators.

## 4. M2 Implementation Progress
- Working live site deployed to GitHub Pages.
- Interpreter executing LIMO mnemonics.
- ISA table and registers frozen and aligned with M1 feedback.

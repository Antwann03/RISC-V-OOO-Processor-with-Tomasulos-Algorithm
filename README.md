# RISC-V Out-of-Order Processor with Tomasulo's Algorithm
---
This repository contains the implementation of a **cycle-accurate RISC-V out-of-order processor** using **Tomasulo's Algorithm** in VHDL for **ECE 622: Computer Systems Architecture** (Spring 2026).

**Author:** Antonio Anzora Jr  
**Professor:** Dr. Mirzaei Shahnam

## Overview
---
This project demonstrates dynamic instruction scheduling, register renaming, and in-order commitment through a complete RTL implementation in VHDL. The processor executes a subset of the RISC-V RV32I instruction set and is verified through detailed behavioral simulations in Vivado 2023.2.


## Project Structure

### Core Components (20 VHDL files)

| Component | Purpose |
|-----------|---------|
| **Register_File_32** | 32 registers with dual write/read ports |
| **RAT** | Register Alias Table for register renaming |
| **Instruction_Queue** | 8-entry FIFO for fetched instructions |
| **Reservation_Status** | Dynamic instruction scheduling (4 entries) |
| **ALU** | Arithmetic/Logic Unit (ADD, SUB, AND, OR, XOR, SLT) |
| **MEM_Unit** | Load/Store functional unit with simulated memory |
| **CDB** | Common Data Bus for result broadcasting |
| **ROB** | Reorder Buffer for in-order commit (8 entries) |
| **TOP** | Top-level integration with control logic |

Each component includes:
- Entity + Architecture (`.vhd`)
- Comprehensive testbench (`_TB.vhd`)

### Warmup Components (4 VHDL files)
- `D_FF.vhd` / `D_FF_tb.vhd` — Basic flip-flop
- `FIFO.vhd` / `FIFO_tb.vhd` — Circular buffer
- `Register_File.vhd` / `Register_File_tb.vhd` — 8-register warmup

---

## Key Features

- **Out-of-Order Execution:** Instructions execute based on operand availability
- **Register Renaming:** RAT eliminates false data dependencies (WAR, WAW hazards)
- **Dynamic Scheduling:** Reservation Stations track operand readiness
- **In-Order Commit:** ROB ensures architectural consistency
- **CDB Snooping:** All components listen for broadcast results

---

## Architecture

---

## Results & Simulation

Behavioral simulation verifies:
- Correct instruction issuance and enqueueing
- Out-of-order execution with proper dependency handling
- Result broadcasting on CDB
- In-order commitment via ROB

[See waveforms directory for detailed simulation results]

---

## Tools & Environment

- **Language:** VHDL
- **Simulator:** Vivado 2023.2 (Behavioral Simulation)
- **Target:** Simulation only (no synthesis/bitstream)
- **ISA:** RISC-V RV32I (subset)

---

## Testing

Each component is independently verified with testbenches covering:
- Basic functionality
- Edge cases (full/empty conditions, wraparound)
- CDB snooping and result forwarding
- Commit semantics

Integration tested via `TOP_tb.vhd` with multi-instruction programs.



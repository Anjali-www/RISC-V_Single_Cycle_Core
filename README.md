# RISC-V_Single_Cycle_Core

This project implements a **single-cycle RISC-V processor core** using a classic single-cycle datapath design.  
It executes basic **RISC-V RV32I** instructions and demonstrates the core structure of a CPU.

---

## 📌 Overview

The processor runs each instruction in a single clock cycle, integrating:

- **Instruction Fetch**
- **Instruction Decode**
- **Execution**
- **Memory Access**
- **Write Back**

The **Control Unit** manages all control signals required for execution.

---

## 🖼 Datapath Diagram

![Datapath Diagram](risc-v-single_cycle_core_image.png)

**Main Components:**
1. **Program Counter (PC)** – Tracks the current instruction address.
2. **Instruction Memory** – Stores instructions.
3. **Register File** – Stores and provides CPU register values.
4. **ALU** – Performs arithmetic and logical operations.
5. **Data Memory** – Used for load/store instructions.
6. **Control Unit** – Generates control signals such as `PCSrc`, `ResultSrc`, `MemWrite`, `ALUControl`, `ALUSrc`, `ImmSrc`, and `RegWrite`.
7. **Immediate Generator (Extend)** – Sign-extends immediate values.
8. **Multiplexers (MUX)** – Select data inputs for ALU, write-back stage, and PC updates.

---

## 🔧 Control Signals

| Signal        | Function |
|---------------|----------|
| **PCSrc**     | Selects the next PC value (sequential or branch target) |
| **ResultSrc** | Chooses ALU result or memory data for write-back |
| **MemWrite**  | Enables writing to Data Memory |
| **ALUControl**| Defines ALU operation type |
| **ALUSrc**    | Selects between register data or immediate for ALU operand B |
| **ImmSrc**    | Decodes immediate type (I, S, B, etc.) |
| **RegWrite**  | Enables register write-back |

---

## ⚙️ Instruction Flow

1. **Fetch** – PC fetches an instruction from Instruction Memory.
2. **Decode** – Control Unit decodes instruction and generates control signals.
3. **Execute** – ALU performs computation or address calculation.
4. **Memory Access** – Reads or writes data as required.
5. **Write Back** – Stores result back to the Register File.

---

## 🚀 Supported Instructions

- **R-type**: `ADD`, `SUB`, `AND`, `OR`, `SLT`, etc.
- **I-type**: `ADDI`, `ANDI`, `ORI`, `LW`, etc.
- **S-type**: `SW`
- **B-type**: `BEQ`, `BNE`
- **J-type**: `JAL`
- **U-type**: `LUI`

---

## 📂 Project Structure

```
├── images/
│   └── datapath.png          # Datapath diagram
├── src/
│   ├── control_unit.v        # Control unit
│   ├── alu.v                 # Arithmetic Logic Unit
│   ├── register_file.v       # CPU registers
│   ├── instruction_memory.v  # Instruction storage
│   ├── data_memory.v         # Data memory
│   └── top_module.v          # Integration
└── README.md
```

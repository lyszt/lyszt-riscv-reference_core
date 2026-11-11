---
name: lui
title: lui
category: jump
syntax: "lui rd, imm"
operation: "rd = imm << 12"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/lui
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# lui

> Load a constant into the upper bits.

**Syntax:** `lui rd, imm`  
**Operation:** `rd = imm << 12`  
**Category:** Jumps & functions  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110111`


## Description

Places a constant in the upper half of a register. In `lui rd, imm`, the constant occupies bits 31 to 12 and the low 12 bits are set to zero. Combined with `addi` for the low half, it builds any 32-bit constant in two instructions.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

LUI (load upper immediate) is used to build 32-bit constants and uses the U-type format. LUI places the 32-bit U-immediate value into the destination register `rd`, filling in the lowest 12 bits with zeros.

> The assembly syntax for `lui` and `auipc` does not represent the lower 12 bits of the U-immediate, which are always zero. The AUIPC instruction supports two-instruction sequences to access arbitrary offsets from the PC for both control-flow transfers and data accesses. The combination of an AUIPC and the 12-bit immediate in a JALR can transfer control to any 32-bit PC-relative address, while an AUIPC plus the 12-bit immediate offset in regular load or store instructions can access any 32-bit PC-relative data address. The current PC can be obtained by setting the U-immediate to 0. Although a JAL +4 instruction could also be used to obtain the local PC (of the instruction following the JAL), it might cause pipeline breaks in simpler microarchitectures or pollute BTB structures in more complex microarchitectures.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/lui)
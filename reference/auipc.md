---
name: auipc
title: auipc
category: jump
syntax: "auipc rd, imm"
operation: "rd = pc + (imm << 12)"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/auipc
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# auipc

> Add an upper constant to the PC.

**Syntax:** `auipc rd, imm`  
**Operation:** `rd = pc + (imm << 12)`  
**Category:** Jumps & functions  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010111`


## Description

Adds a constant to the program counter. In `auipc rd, imm`, the constant occupies bits 31 to 12 of the sum and the instruction's own address fills the rest. The result is position-independent and runs unchanged wherever the program is loaded. An `auipc` followed by a `jalr` reaches any 32-bit relative offset.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

AUIPC (add upper immediate to `pc`) is used to build `pc`-relative addresses and uses the U-type format. AUIPC forms a 32-bit offset from the U-immediate, filling in the lowest 12 bits with zeros, adds this offset to the address of the AUIPC instruction, then places the result in register `rd`.

> The assembly syntax for `lui` and `auipc` does not represent the lower 12 bits of the U-immediate, which are always zero. The AUIPC instruction supports two-instruction sequences to access arbitrary offsets from the PC for both control-flow transfers and data accesses. The combination of an AUIPC and the 12-bit immediate in a JALR can transfer control to any 32-bit PC-relative address, while an AUIPC plus the 12-bit immediate offset in regular load or store instructions can access any 32-bit PC-relative data address. The current PC can be obtained by setting the U-immediate to 0. Although a JAL +4 instruction could also be used to obtain the local PC (of the instruction following the JAL), it might cause pipeline breaks in simpler microarchitectures or pollute BTB structures in more complex microarchitectures.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/auipc). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
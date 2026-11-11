---
name: sll
title: sll
category: shift
syntax: "sll rd, rs1, rs2"
operation: "rd = rs1 << (rs2 & 31)"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/sll
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# sll

> Shift bits left (by a register).

**Syntax:** `sll rd, rs1, rs2`  
**Operation:** `rd = rs1 << (rs2 & 31)`  
**Category:** Shifts  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110011`
 · funct3 `001`
 · funct7 `0000000`


## Description

Shifts the bits of a register to the left. In `sll rd, rs1, rs2`, the value in `rs1` moves left by the count held in the low five bits of `rs2`, and zeros fill the emptied positions. A shift of one position doubles the value, and bits that pass the left edge are discarded.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

SLL, SRL, and SRA perform logical left, logical right, and arithmetic right shifts on the value in register `rs1` by the shift amount held in the lower 5 bits of register `rs2`.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/sll)
---
name: sltiu
title: sltiu
category: compare
syntax: "sltiu rd, rs1, imm"
operation: "rd = (rs1 < imm) ? 1 : 0"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/sltiu
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# sltiu

> Set if less than a constant (unsigned).

**Syntax:** `sltiu rd, rs1, imm`  
**Operation:** `rd = (rs1 < imm) ? 1 : 0`  
**Category:** Compare & set  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010011`
 · funct3 `011`


## Description

Writes 1 or 0 to record whether an unsigned value is smaller than a constant. In `sltiu rd, rs1, imm`, the constant is sign-extended first and then read as unsigned, and the result is 1 when `rs1` falls below it. The assembler writes the zero test `sltiu rd, rs, 1` as `seqz`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

SLTI (set less than immediate) places the value 1 in register `rd` if register `rs1` is less than the sign-extended immediate when both are treated as signed numbers, else 0 is written to `rd`. SLTIU is similar but compares the values as unsigned numbers (i.e., the immediate is first sign-extended to XLEN bits then treated as an unsigned number). Note, SLTIU `rd, rs1, 1` sets `rd` to 1 if `rs1` equals zero, otherwise sets `rd` to 0 (assembler pseudoinstruction SEQZ `rd, rs`).

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/sltiu). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
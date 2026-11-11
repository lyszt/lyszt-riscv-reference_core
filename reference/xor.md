---
name: xor
title: xor
category: logic
syntax: "xor rd, rs1, rs2"
operation: "rd = rs1 ^ rs2"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/xor
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# xor

> Bitwise exclusive-OR.

**Syntax:** `xor rd, rs1, rs2`  
**Operation:** `rd = rs1 ^ rs2`  
**Category:** Bitwise logic  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110011`
 · funct3 `100`
 · funct7 `0000000`


## Description

Computes the bitwise exclusive OR of two register values. In `xor rd, rs1, rs2`, a result bit is 1 where the two input bits differ. Combining a register with itself clears it, and the same method compares two registers, since equal bits produce zero.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

ADD performs the addition of `rs1 and rs2`. SUB performs the subtraction of `rs2` from `rs1`. Overflows are ignored and the low XLEN bits of results are written to the destination `rd`. SLT and SLTU perform signed and unsigned compares respectively, writing 1 to `rd` if `rs1` < `rs2`, 0 otherwise. Note, SLTU `rd`, `x0`, `rs2` sets `rd` to 1 if `rs2` is not equal to zero, otherwise sets `rd` to zero (assembler pseudoinstruction SNEZ `rd, rs`). AND, OR, and XOR perform bitwise logical operations.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/xor)
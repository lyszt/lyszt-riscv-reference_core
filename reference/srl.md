---
name: srl
title: srl
category: shift
syntax: "srl rd, rs1, rs2"
operation: "rd = rs1 >>> (rs2 & 31)"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/srl
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# srl

> Shift bits right, zero-filled.

**Syntax:** `srl rd, rs1, rs2`  
**Operation:** `rd = rs1 >>> (rs2 & 31)`  
**Category:** Shifts  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110011`
 · funct3 `101`
 · funct7 `0000000`


## Description

Shifts a register's bits to the right. In `srl rd, rs1, rs2`, the value in `rs1` moves right by the count in the low five bits of `rs2`, and zeros fill the emptied positions. Every position moved halves an unsigned value, and bits that fall past the right edge are discarded.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

SLL, SRL, and SRA perform logical left, logical right, and arithmetic right shifts on the value in register `rs1` by the shift amount held in the lower 5 bits of register `rs2`.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/srl). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
---
name: xori
title: xori
category: logic
syntax: "xori rd, rs1, imm"
operation: "rd = rs1 ^ imm"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/xori
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# xori

> XOR with a constant.

**Syntax:** `xori rd, rs1, imm`  
**Operation:** `rd = rs1 ^ imm`  
**Category:** Bitwise logic  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010011`
 · funct3 `100`


## Description

Computes the bitwise exclusive OR of a register with a sign-extended constant. In `xori rd, rs1, imm`, a result bit is 1 where the two input bits differ. Writing `xori rd, rs, -1` inverts every bit of the register, which the assembler writes as `not`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

ANDI, ORI, XORI are logical operations that perform bitwise AND, OR, and XOR on register `rs1` and the sign-extended 12-bit immediate and place the result in `rd`. Note, XORI `rd, rs1, -1` performs a bitwise logical inversion of register `rs1` (assembler pseudoinstruction NOT `rd, rs`).

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/xori). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
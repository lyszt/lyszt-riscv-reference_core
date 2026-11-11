---
name: lbu
title: lbu
category: memory
syntax: "lbu rd, off(rs1)"
operation: "rd = mem[rs1 + off]"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/lbu
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# lbu

> Load one byte (unsigned).

**Syntax:** `lbu rd, off(rs1)`  
**Operation:** `rd = mem[rs1 + off]`  
**Category:** Memory  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0000011`
 · funct3 `100`


## Description

Loads a byte from memory into a register. In `lbu rd, offset(rs1)`, the byte is zero-extended to 32 bits and written to `rd`. Zero extension fills the top 24 bits with zeros, so the result is always non-negative, from 0 to 255.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I is a load-store architecture, where only load and store instructions access memory and arithmetic instructions only operate on CPU registers. RV32I provides a 32-bit address space that is byte-addressed. The EEI will define what portions of the address space are legal to access with which instructions (e.g., some addresses might be read only, or support word access only). Loads with a destination of `x0` must still raise any exceptions and cause any other side effects even though the load value is discarded.

The LW instruction loads a 32-bit value from memory into `rd`. LH loads a 16-bit value from memory, then sign-extends to 32-bits before storing in `rd`. LHU loads a 16-bit value from memory but then zero extends to 32-bits before storing in `rd`. LB and LBU are defined analogously for 8-bit values. The SW, SH, and SB instructions store 32-bit, 16-bit, and 8-bit values from the low bits of register `rs2` to memory.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.6, Load and Store Instructions, pages 33 to 34. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=52)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/lbu)
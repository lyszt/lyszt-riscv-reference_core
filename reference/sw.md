---
name: sw
title: sw
category: memory
syntax: "sw rs2, off(rs1)"
operation: "mem[rs1 + off] = rs2"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/sw
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# sw

> Store a 32-bit word to memory.

**Syntax:** `sw rs2, off(rs1)`  
**Operation:** `mem[rs1 + off] = rs2`  
**Category:** Memory  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0100011`
 · funct3 `010`


## Description

Stores a register value to memory. In `sw rs2, offset(rs1)`, the address is the value in `rs1` plus `offset`, and the low 32 bits of `rs2` are written there. The first operand names the source and the second the address, the reverse of the order in `lw`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I is a load-store architecture, where only load and store instructions access memory and arithmetic instructions only operate on CPU registers. RV32I provides a 32-bit address space that is byte-addressed. The EEI will define what portions of the address space are legal to access with which instructions (e.g., some addresses might be read only, or support word access only). Loads with a destination of `x0` must still raise any exceptions and cause any other side effects even though the load value is discarded.

The LW instruction loads a 32-bit value from memory into `rd`. LH loads a 16-bit value from memory, then sign-extends to 32-bits before storing in `rd`. LHU loads a 16-bit value from memory but then zero extends to 32-bits before storing in `rd`. LB and LBU are defined analogously for 8-bit values. The SW, SH, and SB instructions store 32-bit, 16-bit, and 8-bit values from the low bits of register `rs2` to memory.

## Example

```
la t0, slot
li t1, 99
sw t1, 0(t0)   # memory at slot now holds 99
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.6, Load and Store Instructions, pages 33 to 34. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=52)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/sw). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
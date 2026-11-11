---
name: srli
title: srli
category: shift
syntax: "srli rd, rs1, shamt"
operation: "rd = rs1 >>> shamt"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/srli
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# srli

> Shift right by a constant, zero-filled.

**Syntax:** `srli rd, rs1, shamt`  
**Operation:** `rd = rs1 >>> shamt`  
**Category:** Shifts  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010011`
 · funct3 `101`
 · funct7 `0000000`


## Description

Shifts a register's bits to the right by a constant. In `srli rd, rs1, shamt`, the value moves right by `shamt` positions and zeros fill the emptied spots. Every position moved halves an unsigned value, and the result matches a division by a power of two.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

Shifts by a constant are encoded as a specialization of the I-type format. The operand to be shifted is in `rs1`, and the shift amount is encoded in the lower 5 bits of the I-immediate field. The right-shift type is encoded in bit 30. SLLI is a logical left shift (zeros are shifted into the lower bits); SRLI is a logical right shift (zeros are shifted into the upper bits); and SRAI is an arithmetic right shift (the original sign bit is copied into the vacated upper bits).

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/srli). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
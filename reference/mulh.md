---
name: mulh
title: mulh
category: arith
syntax: "mulh rd, rs1, rs2"
operation: "rd = (rs1 * rs2) >> 32"
extension: "Multiply and divide, M"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/mulh
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# mulh

> High 32 bits of a signed product.

**Syntax:** `mulh rd, rs1, rs2`  
**Operation:** `rd = (rs1 * rs2) >> 32`  
**Category:** Arithmetic  
**Extension:** Multiply and divide, M  
**Encoding:** opcode `0110011`
 · funct3 `001`
 · funct7 `0000001`


## Description

Multiplies the values of two registers as signed numbers and stores the high 32 bits of the product. In `mulh rd, rs1, rs2`, the upper half of the 64-bit product goes to `rd`. A nonzero result indicates that the full product does not fit in one register, and wide arithmetic and cryptography use both halves together with `mul` to recover it.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

MUL performs an XLEN-bit×XLEN-bit multiplication of `rs1` by `rs2` and places the lower XLEN bits in the destination register. MULH, MULHU, and MULHSU perform the same multiplication but return the upper XLEN bits of the full 2×XLEN-bit product, for signed×signed, unsigned×unsigned, and `rs1`×unsigned `rs2` multiplication. If both the high and low bits of the same product are required, then the recommended code sequence is: `MULH[[S]U] rdh, rs1, rs2; MUL rdl, rs1, rs2` (source register specifiers must be in same order and `rdh` cannot be the same as `rs1` or `rs2`). Microarchitectures can then fuse these into a single multiply operation instead of performing two separate multiplies.

> In RV64, MUL can be used to obtain the upper 32 bits of the 64-bit product, but signed arguments must be proper 32-bit signed values, whereas unsigned arguments must have their upper 32 bits clear. If the arguments are not known to be sign- or zero-extended, an alternative is to shift both arguments left by 32 bits, then use MULH[[S]U].

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 12.1, Multiplication Operations, page 65. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=84)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/mulh). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
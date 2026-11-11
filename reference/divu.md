---
name: divu
title: divu
category: arith
syntax: "divu rd, rs1, rs2"
operation: "rd = rs1 / rs2"
extension: "Multiply and divide, M"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/divu
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# divu

> Unsigned integer division.

**Syntax:** `divu rd, rs1, rs2`  
**Operation:** `rd = rs1 / rs2`  
**Category:** Arithmetic  
**Extension:** Multiply and divide, M  
**Encoding:** opcode `0110011`
 · funct3 `101`
 · funct7 `0000001`


## Description

Divides the value of one register by another, reading both as unsigned numbers. In `divu rd, rs1, rs2`, the quotient of `rs1` and `rs2` goes to `rd`. The unsigned reading counts the 32 bits from 0 to about 4 billion and serves addresses, sizes, counts and pixel coordinates, where signed `div` returns wrong results once a value passes about 2 billion with its top bit set. A zero divisor also differs from the signed case, yielding the largest unsigned value with every bit set.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

DIV and DIVU perform an XLEN bits by XLEN bits signed and unsigned integer division of `rs1` by `rs2`, rounding towards zero. REM and REMU provide the remainder of the corresponding division operation. For REM, the sign of a nonzero result equals the sign of the dividend.

| Condition | Dividend | Divisor | DIVU[W] | REMU[W] | DIV[W] | REM[W] |
| --- | --- | --- | --- | --- | --- | --- |
| Division by zero Overflow (signed only) | `x` -2^L-1 | 0 −1 | 2^L-1 - | `x` - | −1 -2^L-1 | `x` 0 |

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 12.2, Division Operations, pages 65 to 66. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=84)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/divu). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
---
name: rem
title: rem
category: arith
syntax: "rem rd, rs1, rs2"
operation: "rd = rs1 % rs2"
extension: "Multiply and divide, M"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/rem
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# rem

> Signed remainder (modulo).

**Syntax:** `rem rd, rs1, rs2`  
**Operation:** `rd = rs1 % rs2`  
**Category:** Arithmetic  
**Extension:** Multiply and divide, M  
**Encoding:** opcode `0110011`
 · funct3 `110`
 · funct7 `0000001`


## Description

Returns the remainder left over after a division. In `rem rd, rs1, rs2`, the remainder of `rs1` divided by `rs2` goes to `rd`. Dividing 17 by 5 goes 3 times with 2 left over, and `div` returns the 3 while `rem` returns the 2. The remainder takes the sign of the dividend, and checking for even numbers must test whether the remainder is zero, as a test against 1 fails on negatives.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

DIV and DIVU perform an XLEN bits by XLEN bits signed and unsigned integer division of `rs1` by `rs2`, rounding towards zero. REM and REMU provide the remainder of the corresponding division operation. For REM, the sign of a nonzero result equals the sign of the dividend.

If both the quotient and remainder are required from the same division, the recommended code sequence is: `DIV[U] rdq, rs1, rs2; REM[U] rdr,` `rs1, rs2` (`rdq` cannot be the same as `rs1` or `rs2`). Microarchitectures can then fuse these into a single divide operation instead of performing two separate divides.

Semantics for division by zero and division overflow. L is the width of the operation in bits: XLEN for DIV[U] and REM[U], or 32 for DIV[U]W and REM[U]W.

| Condition | Dividend | Divisor | DIVU[W] | REMU[W] | DIV[W] | REM[W] |
| --- | --- | --- | --- | --- | --- | --- |
| Division by zero Overflow (signed only) | `x` -2^L-1 | 0 −1 | 2^L-1 - | `x` - | −1 -2^L-1 | `x` 0 |

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 12.2, Division Operations, pages 65 to 66. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=84)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/rem). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
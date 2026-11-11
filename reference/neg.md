---
name: neg
title: neg
category: arith
syntax: "neg rd, rs"
operation: "rd = -rs"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/neg
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# neg

> Flip the sign of a number.

**Syntax:** `neg rd, rs`  
**Operation:** `rd = -rs`  
**Category:** Arithmetic  
**Extension:** Pseudo-instruction  


## Description

Reverses the sign of a value. In `neg rd, rs`, the negation of the value in `rs` is written to `rd`, so 5 becomes -5 and -5 becomes 5. The assembler expands it to `sub rd, zero, rs`, subtracting the value from the permanent zero held in register `zero`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

ADD performs the addition of `rs1 and rs2`. SUB performs the subtraction of `rs2` from `rs1`. Overflows are ignored and the low XLEN bits of results are written to the destination `rd`. SLT and SLTU perform signed and unsigned compares respectively, writing 1 to `rd` if `rs1` < `rs2`, 0 otherwise. Note, SLTU `rd`, `x0`, `rs2` sets `rd` to 1 if `rs2` is not equal to zero, otherwise sets `rd` to zero (assembler pseudoinstruction SNEZ `rd, rs`). AND, OR, and XOR perform bitwise logical operations.

## Expands to

```
sub rd, zero, rs
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.1, Programmers' Model for Base Integer ISA, page 23. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=42)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/neg). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
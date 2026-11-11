---
name: snez
title: snez
category: compare
syntax: "snez rd, rs"
operation: "rd = (rs != 0) ? 1 : 0"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/snez
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# snez

> Set to 1 if the value is non-zero.

**Syntax:** `snez rd, rs`  
**Operation:** `rd = (rs != 0) ? 1 : 0`  
**Category:** Compare & set  
**Extension:** Pseudo-instruction  


## Description

Writes 1 when a value is not zero, otherwise 0. In `snez rd, rs`, the result is 1 when `rs` holds anything other than zero. The test reduces a computed value to a single flag, and the assembler expands it to `sltu rd, zero, rs`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

ADD performs the addition of `rs1 and rs2`. SUB performs the subtraction of `rs2` from `rs1`. Overflows are ignored and the low XLEN bits of results are written to the destination `rd`. SLT and SLTU perform signed and unsigned compares respectively, writing 1 to `rd` if `rs1` < `rs2`, 0 otherwise. Note, SLTU `rd`, `x0`, `rs2` sets `rd` to 1 if `rs2` is not equal to zero, otherwise sets `rd` to zero (assembler pseudoinstruction SNEZ `rd, rs`). AND, OR, and XOR perform bitwise logical operations.

## Expands to

```
sltu rd, zero, rs
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/snez). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
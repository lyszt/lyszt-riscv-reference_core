---
name: seqz
title: seqz
category: compare
syntax: "seqz rd, rs"
operation: "rd = (rs == 0) ? 1 : 0"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/seqz
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# seqz

> Set to 1 if the value is zero.

**Syntax:** `seqz rd, rs`  
**Operation:** `rd = (rs == 0) ? 1 : 0`  
**Category:** Compare & set  
**Extension:** Pseudo-instruction  


## Description

Writes 1 when a value is zero, otherwise 0. In `seqz rd, rs`, the result is 1 when `rs` equals zero. The test covers empty counters, successful calls and string ends, and the assembler expands it to `sltiu rd, rs, 1`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

SLTI (set less than immediate) places the value 1 in register `rd` if register `rs1` is less than the sign-extended immediate when both are treated as signed numbers, else 0 is written to `rd`. SLTIU is similar but compares the values as unsigned numbers (i.e., the immediate is first sign-extended to XLEN bits then treated as an unsigned number). Note, SLTIU `rd, rs1, 1` sets `rd` to 1 if `rs1` equals zero, otherwise sets `rd` to 0 (assembler pseudoinstruction SEQZ `rd, rs`).

## Expands to

```
sltiu rd, rs, 1
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/seqz). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
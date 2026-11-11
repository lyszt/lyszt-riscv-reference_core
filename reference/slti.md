---
name: slti
title: slti
category: compare
syntax: "slti rd, rs1, imm"
operation: "rd = (rs1 < imm) ? 1 : 0"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/slti
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# slti

> Set if less than a constant (signed).

**Syntax:** `slti rd, rs1, imm`  
**Operation:** `rd = (rs1 < imm) ? 1 : 0`  
**Category:** Compare & set  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010011`
 · funct3 `010`


## Description

Writes 1 or 0 to record whether a signed value is smaller than a constant. In `slti rd, rs1, imm`, the result is 1 when the signed value in `rs1` is less than the sign-extended `imm`, otherwise 0. The constant spans -2048 to 2047. Wider constants go into a register through `li` and the register form `slt`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

Most integer computational instructions operate on `XLEN` bits of values held in the integer register file. Integer computational instructions are either encoded as register-immediate operations using the I-type format or as register-register operations using the R-type format. The destination is register `rd` for both register-immediate and register-register instructions. No integer computational instructions cause arithmetic exceptions.

```
add t0, t1, t2
slti t3, t2, 0
slt t4, t0, t1
bne t3, t4, overflow
```

### Integer Register-Immediate Instructions

SLTI (set less than immediate) places the value 1 in register `rd` if register `rs1` is less than the sign-extended immediate when both are treated as signed numbers, else 0 is written to `rd`. SLTIU is similar but compares the values as unsigned numbers (i.e., the immediate is first sign-extended to XLEN bits then treated as an unsigned number). Note, SLTIU `rd, rs1, 1` sets `rd` to 1 if `rs1` equals zero, otherwise sets `rd` to 0 (assembler pseudoinstruction SEQZ `rd, rs`).

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4, Integer Computational Instructions, page 27. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=46)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/slti). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
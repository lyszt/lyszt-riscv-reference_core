---
name: slt
title: slt
category: compare
syntax: "slt rd, rs1, rs2"
operation: "rd = (rs1 < rs2) ? 1 : 0"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/slt
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# slt

> Set to 1 if less than (signed).

**Syntax:** `slt rd, rs1, rs2`  
**Operation:** `rd = (rs1 < rs2) ? 1 : 0`  
**Category:** Compare & set  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110011`
 · funct3 `010`
 · funct7 `0000000`


## Description

Writes 1 or 0 to record which of two signed values is smaller. In `slt rd, rs1, rs2`, the result is 1 when the signed value in `rs1` is less than `rs2`, otherwise 0. Later instructions can test the result as a value.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

Most integer computational instructions operate on `XLEN` bits of values held in the integer register file. Integer computational instructions are either encoded as register-immediate operations using the I-type format or as register-register operations using the R-type format. The destination is register `rd` for both register-immediate and register-register instructions. No integer computational instructions cause arithmetic exceptions.

```
add t0, t1, t2
slti t3, t2, 0
slt t4, t0, t1
bne t3, t4, overflow
```

### Integer Register-Register Instructions

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

ADD performs the addition of `rs1 and rs2`. SUB performs the subtraction of `rs2` from `rs1`. Overflows are ignored and the low XLEN bits of results are written to the destination `rd`. SLT and SLTU perform signed and unsigned compares respectively, writing 1 to `rd` if `rs1` < `rs2`, 0 otherwise. Note, SLTU `rd`, `x0`, `rs2` sets `rd` to 1 if `rs2` is not equal to zero, otherwise sets `rd` to zero (assembler pseudoinstruction SNEZ `rd, rs`). AND, OR, and XOR perform bitwise logical operations.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4, Integer Computational Instructions, page 27. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=46)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/slt). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
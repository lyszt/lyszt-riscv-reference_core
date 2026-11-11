---
name: addi
title: addi
category: arith
syntax: "addi rd, rs1, imm"
operation: "rd = rs1 + imm"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/addi
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# addi

> Add a small constant to a register.

**Syntax:** `addi rd, rs1, imm`  
**Operation:** `rd = rs1 + imm`  
**Category:** Arithmetic  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0010011`
 · funct3 `000`


## Description

Adds a constant to a register. In `addi rd, rs1, imm`, the constant `imm` is added to the value in `rs1` and the result goes to `rd`. The constant is signed and spans -2048 to 2047, and larger values must first be placed in a register with `li`. A negative constant turns the addition into a subtraction, as in the counter decrement `addi t0, t0, -1`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

Most integer computational instructions operate on `XLEN` bits of values held in the integer register file. Integer computational instructions are either encoded as register-immediate operations using the I-type format or as register-register operations using the R-type format. The destination is register `rd` for both register-immediate and register-register instructions. No integer computational instructions cause arithmetic exceptions.

> We did not include special instruction-set support for overflow checks on integer arithmetic operations in the base instruction set, as many overflow checks can be cheaply implemented using RISC-V branches. Overflow checking for unsigned addition requires only a single additional branch instruction after the addition: `add t0, t1, t2; bltu t0, t1, overflow`. For signed addition, if one operand's sign is known, overflow checking requires only a single branch after the addition: `addi t0, t1, +imm; blt t0, t1, overflow`. This covers the common case of addition with an immediate operand. For general signed addition, three additional instructions after the addition are required, leveraging the observation that the sum should be less than one of the operands if and only if the other operand is negative. In RV64I, checks of 32-bit signed additions can be optimized further by comparing the results of ADD and ADDW on the operands.

### Integer Register-Immediate Instructions

ADDI adds the sign-extended 12-bit immediate to register `rs1`. Arithmetic overflow is ignored and the result is simply the low XLEN bits of the result. ADDI `rd, rs1, 0` is used to implement the MV `rd, rs1` assembler pseudoinstruction.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4, Integer Computational Instructions, page 27. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=46)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/addi). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
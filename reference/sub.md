---
name: sub
title: sub
category: arith
syntax: "sub rd, rs1, rs2"
operation: "rd = rs1 - rs2"
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/sub
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# sub

> Subtract one register from another.

**Syntax:** `sub rd, rs1, rs2`  
**Operation:** `rd = rs1 - rs2`  
**Category:** Arithmetic  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `0110011`
 · funct3 `000`
 · funct7 `0100000`


## Description

Subtracts the value of one register from another and writes the result to a third. In `sub rd, rs1, rs2`, the value in `rs2` is subtracted from `rs1` and the result goes to `rd`, and the order of the two sources matters. No subtract-immediate instruction exists; a constant is subtracted with `addi` and a negative value instead. A subtraction from the `zero` register reverses a value's sign, which the assembler writes as `neg`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

Most integer computational instructions operate on `XLEN` bits of values held in the integer register file. Integer computational instructions are either encoded as register-immediate operations using the I-type format or as register-register operations using the R-type format. The destination is register `rd` for both register-immediate and register-register instructions. No integer computational instructions cause arithmetic exceptions.

```
add t0, t1, t2
slti t3, t2, 0
slt t4, t0, t1
bne t3, t4, overflow
```

> We did not include special instruction-set support for overflow checks on integer arithmetic operations in the base instruction set, as many overflow checks can be cheaply implemented using RISC-V branches. Overflow checking for unsigned addition requires only a single additional branch instruction after the addition: `add t0, t1, t2; bltu t0, t1, overflow`. For signed addition, if one operand's sign is known, overflow checking requires only a single branch after the addition: `addi t0, t1, +imm; blt t0, t1, overflow`. This covers the common case of addition with an immediate operand. For general signed addition, three additional instructions after the addition are required, leveraging the observation that the sum should be less than one of the operands if and only if the other operand is negative. In RV64I, checks of 32-bit signed additions can be optimized further by comparing the results of ADD and ADDW on the operands.

### Integer Register-Register Instructions

RV32I defines several arithmetic R-type operations. All operations read the `rs1 and rs2` registers as source operands and write the result into register `rd`. The `funct7 and funct3` fields select the type of operation.

ADD performs the addition of `rs1 and rs2`. SUB performs the subtraction of `rs2` from `rs1`. Overflows are ignored and the low XLEN bits of results are written to the destination `rd`. SLT and SLTU perform signed and unsigned compares respectively, writing 1 to `rd` if `rs1` < `rs2`, 0 otherwise. Note, SLTU `rd`, `x0`, `rs2` sets `rd` to 1 if `rs2` is not equal to zero, otherwise sets `rd` to zero (assembler pseudoinstruction SNEZ `rd, rs`). AND, OR, and XOR perform bitwise logical operations.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.2, Integer Register-Register Instructions, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.1, Programmers' Model for Base Integer ISA, page 23. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=42)
3. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4, Integer Computational Instructions, page 27. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=46)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/sub). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
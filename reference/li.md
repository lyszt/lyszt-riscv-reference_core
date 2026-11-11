---
name: li
title: li
category: memory
syntax: "li rd, imm"
operation: "rd = imm"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/li
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# li

> Load any constant into a register.

**Syntax:** `li rd, imm`  
**Operation:** `rd = imm`  
**Category:** Memory  
**Extension:** Pseudo-instruction  


## Description

Writes a constant into a register. In `li rd, imm`, the constant goes to `rd` regardless of its width. `addi` covers constants up to 12 bits; `li` takes any 32-bit value and expands into whatever instruction sequence that value needs.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

ADDI adds the sign-extended 12-bit immediate to register `rs1`. Arithmetic overflow is ignored and the result is simply the low XLEN bits of the result. ADDI `rd, rs1, 0` is used to implement the MV `rd, rs1` assembler pseudoinstruction.

## Expands to

```
addi rd, zero, imm          # small constants
lui rd, hi  +  addi rd, rd, lo   # large constants
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/li). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
---
name: mv
title: mv
category: memory
syntax: "mv rd, rs"
operation: "rd = rs"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/mv
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# mv

> Copy one register to another.

**Syntax:** `mv rd, rs`  
**Operation:** `rd = rs`  
**Category:** Memory  
**Extension:** Pseudo-instruction  


## Description

Copies a value between registers. In `mv rd, rs`, the value in `rs` goes to `rd` and the source keeps its value. The assembler expands it to `addi rd, rs, 0`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

ADDI adds the sign-extended 12-bit immediate to register `rs1`. Arithmetic overflow is ignored and the result is simply the low XLEN bits of the result. ADDI `rd, rs1, 0` is used to implement the MV `rd, rs1` assembler pseudoinstruction.

## Expands to

```
addi rd, rs, 0
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/mv). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
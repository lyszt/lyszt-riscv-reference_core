---
name: ble
title: ble
category: branch
syntax: "ble rs1, rs2, label"
operation: "if (rs1 <= rs2) goto label"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/ble
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# ble

> Jump if less or equal (signed).

**Syntax:** `ble rs1, rs2, label`  
**Operation:** `if (rs1 <= rs2) goto label`  
**Category:** Branches  
**Extension:** Pseudo-instruction  


## Description

Branches to a label when one signed value is at most another. In `ble rs1, rs2, label`, the branch is taken when `rs1` is not above `rs2`. The assembler expands it to `bge` with the operands reversed.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

All branch instructions use the B-type instruction format. The 12-bit B-immediate encodes signed offsets in multiples of 2 bytes. The offset is sign-extended and added to the address of the branch instruction to give the target address. The conditional branch range is ±4 KiB.

Branch instructions compare two registers. BEQ and BNE take the branch if registers `rs1 and rs2` are equal or unequal respectively. BLT and BLTU take the branch if `rs1` is less than `rs2`, using signed and unsigned comparison respectively. BGE and BGEU take the branch if `rs1` is greater than or equal to `rs2`, using signed and unsigned comparison respectively. Note, BGT, BGTU, BLE, and BLEU can be synthesized by reversing the operands to BLT, BLTU, BGE, and BGEU, respectively.

## Expands to

```
bge rs2, rs1, label
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.5.2, Conditional Branches, pages 31 to 32. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=50)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/ble)
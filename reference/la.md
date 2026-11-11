---
name: la
title: la
category: memory
syntax: "la rd, label"
operation: "rd = &label"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/la
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# la

> Load the address of a label.

**Syntax:** `la rd, label`  
**Operation:** `rd = &label`  
**Category:** Memory  
**Extension:** Pseudo-instruction  


## Description

Stores the address of a label in a register. In `la rd, label`, the assembler resolves the label's address and writes it to `rd`. It reaches data declared under .data and anywhere a pointer is needed in a register.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

AUIPC (add upper immediate to `pc`) is used to build `pc`-relative addresses and uses the U-type format. AUIPC forms a 32-bit offset from the U-immediate, filling in the lowest 12 bits with zeros, adds this offset to the address of the AUIPC instruction, then places the result in register `rd`.

> The assembly syntax for `lui` and `auipc` does not represent the lower 12 bits of the U-immediate, which are always zero. The AUIPC instruction supports two-instruction sequences to access arbitrary offsets from the PC for both control-flow transfers and data accesses. The combination of an AUIPC and the 12-bit immediate in a JALR can transfer control to any 32-bit PC-relative address, while an AUIPC plus the 12-bit immediate offset in regular load or store instructions can access any 32-bit PC-relative data address. The current PC can be obtained by setting the U-immediate to 0. Although a JAL +4 instruction could also be used to obtain the local PC (of the instruction following the JAL), it might cause pipeline breaks in simpler microarchitectures or pollute BTB structures in more complex microarchitectures.

## Expands to

```
auipc rd, hi(label)
addi  rd, rd, lo(label)
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/la)
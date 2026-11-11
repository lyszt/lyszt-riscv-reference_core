---
name: nop
title: nop
category: system
syntax: "nop"
operation: ""
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/nop
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# nop

> Do nothing for one instruction.

**Syntax:** `nop`  
**Category:** System  
**Extension:** Pseudo-instruction  


## Description

Advances the program without changing any state. In `nop`, only the program counter moves, and registers and memory stay untouched. It fills the space between instructions, giving later instructions addresses the hardware handles faster, and it leaves room that tools overwrite later with real instructions.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

The NOP instruction does not change any architecturally visible state, except for advancing the `pc` and incrementing any applicable performance counters. NOP is encoded as ADDI `x0, x0, 0`.

> NOPs can be used to align code segments to microarchitecturally significant address boundaries, or to leave space for inline code modifications. Although there are many possible ways to encode a NOP, we define a canonical NOP encoding to allow microarchitectural optimizations as well as for more readable disassembly output. The other NOP encodings are made available for rv32i-hints. ADDI was chosen for the NOP encoding as this is most likely to take fewest resources to execute across a range of systems (if not optimized away in decode). In particular, the instruction only reads one register. Also, an ADDI functional unit is more likely to be available in a superscalar design as adds are the most common operation. In particular, address-generation functional units can execute ADDI using the same hardware needed for base+offset address calculations, while register-register ADD or logical/shift operations require additional hardware.

## Expands to

```
addi zero, zero, 0
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.3, NOP Instruction, page 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=48)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/nop). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
---
name: call
title: call
category: jump
syntax: "call label"
operation: "ra = pc + 4; goto label"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/call
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# call

> Call a function.

**Syntax:** `call label`  
**Operation:** `ra = pc + 4; goto label`  
**Category:** Jumps & functions  
**Extension:** Pseudo-instruction  


## Description

Calls a function at a label. In `call label`, the return address goes into `ra` and execution continues at the label; the caller resumes there when the callee returns. The assembler expands it to `jal ra, label`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

The jump and link (JAL) instruction uses the J-type format, where the J-immediate encodes a signed offset in multiples of 2 bytes. The offset is sign-extended and added to the address of the jump instruction to form the jump target address. Jumps can therefore target a ±1 MiB range. JAL stores the address of the instruction following the jump ('pc'+4) into register `rd`. The standard software calling convention uses 'x1' as the return address register and 'x5' as an alternate link register.

Plain unconditional jumps (assembler pseudoinstruction J) are encoded as a JAL with `rd`=`x0`.

The JAL and JALR instructions will generate an instruction-address-misaligned exception if the target address is not aligned to a four-byte boundary.

Return-address prediction stacks are a common feature of high-performance instruction-fetch units, but require accurate detection of instructions used for procedure calls and returns to be effective. For RISC-V, hints as to the instructions' usage are encoded implicitly via the register numbers used. A JAL instruction should push the return address onto a return-address stack (RAS) only when `rd` is 'x1' or `x5`. JALR instructions should push/pop a RAS as shown in rashints.

## Expands to

```
jal ra, label
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.5.1, Unconditional Jumps, page 30. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=49)
2. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/call)
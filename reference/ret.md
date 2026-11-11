---
name: ret
title: ret
category: jump
syntax: "ret"
operation: "goto ra"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/ret
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# ret

> Return from a function.

**Syntax:** `ret`  
**Operation:** `goto ra`  
**Category:** Jumps & functions  
**Extension:** Pseudo-instruction  


## Description

Returns from a function to its caller. In `ret`, execution continues at the address held in `ra`. Every non-leaf function ends with it, and the assembler expands it to `jalr zero, ra, 0`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

The indirect jump instruction JALR (jump and link register) uses the I-type encoding. The target address is obtained by adding the sign-extended 12-bit I-immediate to the register `rs1`, then setting the least-significant bit of the result to zero. The address of the instruction following the jump (`pc`+4) is written to register `rd`. Register `x0` can be used as the destination if the result is not required.

Plain unconditional indirect jumps (assembler pseudoinstruction JR) are encoded as a JALR with `rd`=`x0`. Procedure returns in the standard calling convention (assembler pseudoinstruction RET) are encoded as a JALR with `rd`=`x0`, `rs1`=`x1`, and `imm`=0.

> The unconditional jump instructions all use PC-relative addressing to help support position-independent code. The JALR instruction was defined to enable a two-instruction sequence to jump anywhere in a 32-bit absolute address range. A LUI instruction can first load `rs1` with the upper 20 bits of a target address, then JALR can add in the lower bits. Similarly, AUIPC then JALR can jump anywhere in a 32-bit `pc`-relative address range. Note that the JALR instruction does not treat the 12-bit immediate as multiples of 2 bytes, unlike the conditional branch instructions. This avoids one more immediate format in hardware. In practice, most uses of JALR will have either a zero immediate or be paired with a LUI or AUIPC, so the slight reduction in range is not significant. Clearing the least-significant bit when calculating the JALR target address both simplifies the hardware slightly and allows the low bit of function pointers to be used to store auxiliary information. Although there is potentially a slight loss of error checking in this case, in practice jumps to an incorrect instruction address will usually quickly raise an exception. When used with a base `rs1`=`x0`, JALR can be used to implement a single instruction subroutine call to the lowest or highest address region from anywhere in the address space, which could be used to implement fast calls to a small runtime library. Alternatively, an ABI could dedicate a general-purpose register to point to a library elsewhere in the address space.

The JAL and JALR instructions will generate an instruction-address-misaligned exception if the target address is not aligned to a four-byte boundary.

Return-address prediction stacks are a common feature of high-performance instruction-fetch units, but require accurate detection of instructions used for procedure calls and returns to be effective. For RISC-V, hints as to the instructions' usage are encoded implicitly via the register numbers used. A JAL instruction should push the return address onto a return-address stack (RAS) only when `rd` is 'x1' or `x5`. JALR instructions should push/pop a RAS as shown in rashints.

Return-address stack prediction hints encoded in the register operands of a JALR instruction.

> Some other ISAs added explicit hint bits to their indirect-jump instructions to guide return-address stack manipulation. We use implicit hinting tied to register numbers and the calling convention to reduce the encoding space used for these hints. When two different link registers (`x1` and `x5`) are given as `rs1` and `rd`, then the RAS is both popped and pushed to support coroutines. If `rs1 and rd` are the same link register (either `x1` or `x5`), the RAS is only pushed to enable macro-op fusion of the sequences: `lui ra, imm20; jalr ra, imm12(ra) and auipc ra, imm20; jalr ra, imm12(ra)`

## Expands to

```
jalr zero, ra, 0
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.5.1, Unconditional Jumps, page 30. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=49)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/ret). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
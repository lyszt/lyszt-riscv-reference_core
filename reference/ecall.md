---
name: ecall
title: ecall
category: system
syntax: "ecall"
operation: ""
extension: "Base integer, RV32I"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/ecall
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# ecall

> Ask the system to do something.

**Syntax:** `ecall`  
**Category:** System  
**Extension:** Base integer, RV32I  
**Encoding:** opcode `1110011`


## Description

Requests a service from the environment. In `ecall`, the service number is read from `a7` and the argument from `a0`, and execution traps to the environment. Printing an integer uses service 1 with the value in `a0`; service 10 ends the program.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

The `ECALL` instruction is used to make a service request to the execution environment. The `EEI` will define how parameters for the service request are passed, but usually these will be in defined locations in the integer register file.

> ECALL and EBREAK were previously named SCALL and SBREAK. The instructions have the same functionality and encoding, but were renamed to reflect that they can be used more generally than to call a supervisor-level operating system or debugger.

> EBREAK was primarily designed to be used by a debugger to cause execution to stop and fall back into the debugger. EBREAK is also used by the standard GCC compiler to mark code paths that should not be executed. Another use of EBREAK is to support "semihosting", where the execution environment includes a debugger that can provide services over an alternate system call interface built around the EBREAK instruction. Because the RISC-V base ISAs do not provide more than one EBREAK instruction, RISC-V semihosting uses a special sequence of instructions to distinguish a semihosting EBREAK from a debugger inserted EBREAK. Note that these three instructions must be 32-bit-wide instructions, i.e., they mustn't be among the compressed 16-bit instructions described in compressed. The shift NOP instructions are still considered available for use as HINTs. Semihosting is a form of service call and would be more naturally encoded as an ECALL using an existing ABI, but this would require the debugger to be able to intercept ECALLs, which is a newer addition to the debug standard. We intend to move over to using ECALLs with a standard ABI, in which case, semihosting can share a service ABI with an existing standard. We note that ARM processors have also moved to using SVC instead of BKPT for semihosting calls in newer designs.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.8, Environment Call and Breakpoints, page 36. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=55)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/ecall). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
---
name: not
title: not
category: logic
syntax: "not rd, rs"
operation: "rd = ~rs"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/not
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# not

> Flip every bit.

**Syntax:** `not rd, rs`  
**Operation:** `rd = ~rs`  
**Category:** Bitwise logic  
**Extension:** Pseudo-instruction  


## Description

Writes the bitwise complement of a register value. In `not rd, rs`, every bit of the value in `rs` is flipped and written to `rd`, so each 0 becomes 1 and each 1 becomes 0. The assembler expands it to `xori rd, rs, -1`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

ANDI, ORI, XORI are logical operations that perform bitwise AND, OR, and XOR on register `rs1` and the sign-extended 12-bit immediate and place the result in `rd`. Note, XORI `rd, rs1, -1` performs a bitwise logical inversion of register `rs1` (assembler pseudoinstruction NOT `rd, rs`).

## Expands to

```
xori rd, rs, -1
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.4.1, Integer Register-Immediate Instructions, pages 28 to 29. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=47)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/not)
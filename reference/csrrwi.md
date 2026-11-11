---
name: csrrwi
title: csrrwi
category: system
syntax: "csrrwi rd, csr, uimm"
operation: "rd = csr; csr = uimm"
extension: "Control and status registers, Zicsr"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/csrrwi
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# csrrwi

> Write a constant into a control register and read the old value.

**Syntax:** `csrrwi rd, csr, uimm`  
**Operation:** `rd = csr; csr = uimm`  
**Category:** System  
**Extension:** Control and status registers, Zicsr  
**Encoding:** opcode `1110011`
 · funct3 `101`


## Description

Writes a 5-bit constant to a CSR. In `csrrwi rd, csr, uimm`, the value 0 to 31 replaces the content of `csr`, and the previous content goes to `rd`. The constant field holds five bits, so larger values go through a register with `csrw`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

All CSR instructions atomically read-modify-write a single CSR, whose CSR specifier is encoded in the 12-bit `csr` field of the instruction held in bits 31-20. The immediate forms use a 5-bit zero-extended immediate encoded in the `rs1` field.

The CSRRWI, CSRRSI, and CSRRCI variants are similar to CSRRW, CSRRS, and CSRRC respectively, except they update the CSR using an XLEN-bit value obtained by zero-extending a 5-bit unsigned immediate (uimm[4:0]) field encoded in the `rs1` field instead of a value from an integer register. For CSRRSI and CSRRCI, if the uimm[4:0] field is zero, then these instructions will not write to the CSR, and shall not cause any of the side effects that might otherwise occur on a CSR write, nor raise illegal-instruction exceptions on accesses to read-only CSRs. For CSRRWI, if `rd`=`x0`, then the instruction shall not read the CSR and shall not cause any of the side effects that might occur on a CSR read. Both CSRRSI and CSRRCI will always read the CSR and cause any read side effects regardless of `rd and rs1` fields.

| Instruction | `rd` is `x0` | `uimm`=0 | Reads CSR | Writes CSR |
| --- | --- | --- | --- | --- |
| CSRRWI | Yes | - | No | Yes |
| CSRRWI | No | - | Yes | Yes |
| CSRRSI/CSRRCI | - | Yes | Yes | No |
| CSRRSI/CSRRCI | - | No | Yes | Yes |

The assembler pseudoinstruction to read a CSR, CSRR `rd, csr`, is encoded as CSRRS `rd, csr, x0`. The assembler pseudoinstruction to write a CSR, CSRW `csr, rs1`, is encoded as CSRRW `x0, csr, rs1`, while CSRWI `csr, uimm`, is encoded as CSRRWI `x0, csr, uimm`.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 6.1, CSR Instructions, pages 47 to 49. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=66)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/csrrwi)
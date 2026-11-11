---
name: csrw
title: csrw
category: system
syntax: "csrw csr, rs"
operation: "csr = rs"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/csrw
manual_version: 20260120
manual_commit: 6ad05e3d
license: Apache-2.0
official_license: CC-BY-4.0
---

# csrw

> Write a register into a control register.

**Syntax:** `csrw csr, rs`  
**Operation:** `csr = rs`  
**Category:** System  
**Extension:** Pseudo-instruction  


## Description

Writes a register to a CSR. In `csrw csr, rs`, the value in `rs` replaces the content of `csr`. The assembler expands it to `csrrw` with the destination `zero`, which skips the read.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

All CSR instructions atomically read-modify-write a single CSR, whose CSR specifier is encoded in the 12-bit `csr` field of the instruction held in bits 31-20. The immediate forms use a 5-bit zero-extended immediate encoded in the `rs1` field.

The CSRRW (Atomic Read/Write CSR) instruction atomically swaps values in the CSRs and integer registers. CSRRW reads the old value of the CSR, zero-extends the value to XLEN bits, then writes it to integer register `rd`. The initial value in `rs1` is written to the CSR. If `rd`=`x0`, then the instruction shall not read the CSR and shall not cause any of the side effects that might occur on a CSR read.

A CSRRW with `rs1`=`x0` will attempt to write zero to the destination CSR.

The CSRRWI, CSRRSI, and CSRRCI variants are similar to CSRRW, CSRRS, and CSRRC respectively, except they update the CSR using an XLEN-bit value obtained by zero-extending a 5-bit unsigned immediate (uimm[4:0]) field encoded in the `rs1` field instead of a value from an integer register. For CSRRSI and CSRRCI, if the uimm[4:0] field is zero, then these instructions will not write to the CSR, and shall not cause any of the side effects that might otherwise occur on a CSR write, nor raise illegal-instruction exceptions on accesses to read-only CSRs. For CSRRWI, if `rd`=`x0`, then the instruction shall not read the CSR and shall not cause any of the side effects that might occur on a CSR read. Both CSRRSI and CSRRCI will always read the CSR and cause any read side effects regardless of `rd and rs1` fields.

| Instruction | `rd` is `x0` | `rs1` is `x0` | Reads CSR | Writes CSR |
| --- | --- | --- | --- | --- |
| CSRRW | Yes | - | No | Yes |
| CSRRW | No | - | Yes | Yes |
| CSRRS/CSRRC | - | Yes | Yes | No |
| CSRRS/CSRRC | - | No | Yes | Yes |

In addition to side effects that occur as a consequence of reading or writing a CSR, individual fields within a CSR might have side effects when written.  The CSRRW[I] instructions action side effects for all such fields within the written CSR.  The CSRRS[I] an CSRRC[I] instructions only action side effects for fields for which the `rs1` or `uimm` argument has at least one bit set corresponding to that field.

The assembler pseudoinstruction to read a CSR, CSRR `rd, csr`, is encoded as CSRRS `rd, csr, x0`. The assembler pseudoinstruction to write a CSR, CSRW `csr, rs1`, is encoded as CSRRW `x0, csr, rs1`, while CSRWI `csr, uimm`, is encoded as CSRRWI `x0, csr, uimm`.

## Expands to

```
csrrw zero, csr, rs
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 6.1, CSR Instructions, pages 47 to 49. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=66)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/csrw). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
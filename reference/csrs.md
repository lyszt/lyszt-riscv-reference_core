---
name: csrs
title: csrs
category: system
syntax: "csrs csr, rs"
operation: "csr |= rs"
extension: "Pseudo-instruction"
pseudo: true
canonical: https://lyszt.net/academia/resources/riscv/reference/csrs
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# csrs

> Set bits in a control register.

**Syntax:** `csrs csr, rs`  
**Operation:** `csr |= rs`  
**Category:** System  
**Extension:** Pseudo-instruction  


## Description

Sets the bits named by a register in a CSR. In `csrs csr, rs`, bits that are 1 in `rs` are set in `csr`, and the remaining bits keep their values. The assembler expands it to `csrrs` with the destination `zero`.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

All CSR instructions atomically read-modify-write a single CSR, whose CSR specifier is encoded in the 12-bit `csr` field of the instruction held in bits 31-20. The immediate forms use a 5-bit zero-extended immediate encoded in the `rs1` field.

The CSRRS (Atomic Read and Set Bits in CSR) instruction reads the value of the CSR, zero-extends the value to XLEN bits, and writes it to integer register `rd`. The initial value in integer register `rs1` is treated as a bit mask that specifies bit positions to be set in the CSR. Any bit that is high in `rs1` will cause the corresponding bit to be set in the CSR, if that CSR bit is writable.

> Since CSRRS and CSRRC perform a read-modify-write operation, any bits that read as a different value to their underlying value may be modified by these instructions even if the corresponding bit is not set in `rs1`. For example, pmpaddr__n__[G-1] may have an underlying value of 1 but read as 0. Executing CSRRC or CSRRS to modify a different bit will cause 0 to be read from pmpaddr__n__[G-1] and then written back, updating the underlying value to 0.

For both CSRRS and CSRRC, if `rs1`=`x0`, then the instruction will not write to the CSR at all, and so shall not cause any of the side effects that might otherwise occur on a CSR write, nor raise illegal-instruction exceptions on accesses to read-only CSRs. Both CSRRS and CSRRC always read the addressed CSR and cause any read side effects regardless of `rs1 and rd` fields. Note that if `rs1` specifies a register other than `x0`, and that register holds a zero value, the instruction will not action any attendant per-field side effects, but will action any side effects caused by writing to the entire CSR.

The CSRRWI, CSRRSI, and CSRRCI variants are similar to CSRRW, CSRRS, and CSRRC respectively, except they update the CSR using an XLEN-bit value obtained by zero-extending a 5-bit unsigned immediate (uimm[4:0]) field encoded in the `rs1` field instead of a value from an integer register. For CSRRSI and CSRRCI, if the uimm[4:0] field is zero, then these instructions will not write to the CSR, and shall not cause any of the side effects that might otherwise occur on a CSR write, nor raise illegal-instruction exceptions on accesses to read-only CSRs. For CSRRWI, if `rd`=`x0`, then the instruction shall not read the CSR and shall not cause any of the side effects that might occur on a CSR read. Both CSRRSI and CSRRCI will always read the CSR and cause any read side effects regardless of `rd and rs1` fields.

| Instruction | `rd` is `x0` | `rs1` is `x0` | Reads CSR | Writes CSR |
| --- | --- | --- | --- | --- |
| CSRRW | Yes | - | No | Yes |
| CSRRW | No | - | Yes | Yes |
| CSRRS/CSRRC | - | Yes | Yes | No |
| CSRRS/CSRRC | - | No | Yes | Yes |

In addition to side effects that occur as a consequence of reading or writing a CSR, individual fields within a CSR might have side effects when written.  The CSRRW[I] instructions action side effects for all such fields within the written CSR.  The CSRRS[I] an CSRRC[I] instructions only action side effects for fields for which the `rs1` or `uimm` argument has at least one bit set corresponding to that field.

The assembler pseudoinstruction to read a CSR, CSRR `rd, csr`, is encoded as CSRRS `rd, csr, x0`. The assembler pseudoinstruction to write a CSR, CSRW `csr, rs1`, is encoded as CSRRW `x0, csr, rs1`, while CSRWI `csr, uimm`, is encoded as CSRRWI `x0, csr, uimm`.

Further assembler pseudoinstructions are defined to set and clear bits in the CSR when the old value is not required: CSRS/CSRC `csr, rs1`; CSRSI/CSRCI `csr, uimm`.

## Expands to

```
csrrs zero, csr, rs
```

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 6.1, CSR Instructions, pages 47 to 49. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=66)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/csrs). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
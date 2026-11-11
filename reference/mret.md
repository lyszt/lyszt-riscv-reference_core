---
name: mret
title: mret
category: system
syntax: "mret"
operation: "pc = mepc; MIE = MPIE"
extension: "Privileged architecture"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/mret
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# mret

> Return from a trap handler.

**Syntax:** `mret`  
**Operation:** `pc = mepc; MIE = MPIE`  
**Category:** System  
**Extension:** Privileged architecture  
**Encoding:** opcode `1110011`


## Description

Returns from a trap handler. In `mret`, execution continues at the address held in `mepc`, and the interrupt state is restored from the saved fields. Trap handlers end with it the way functions end with `ret`.

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/mret). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
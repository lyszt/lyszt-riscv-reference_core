---
name: wfi
title: wfi
category: system
syntax: "wfi"
operation: "wait until an interrupt is pending"
extension: "Privileged architecture"
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/wfi
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# wfi

> Wait until an interrupt arrives.

**Syntax:** `wfi`  
**Operation:** `wait until an interrupt is pending`  
**Category:** System  
**Extension:** Privileged architecture  
**Encoding:** opcode `1110011`


## Description

Pauses the hart until work arrives. In `wfi`, execution stops until an interrupt becomes pending, and the interrupt then proceeds through its normal handling. Idle loops use it to wait without burning power.

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/wfi). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
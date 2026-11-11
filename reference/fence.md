---
name: fence
title: fence
category: system
syntax: "fence pred, succ"
operation: ""
extension: ""
pseudo: false
canonical: https://lyszt.net/academia/resources/riscv/reference/fence
manual_version: 20260120
manual_commit: 6ad05e3d
license: CC-BY-4.0
---

# fence

> Order device I/O and memory accesses.

**Syntax:** `fence pred, succ`  
**Category:** System  


## Description

Orders memory and device accesses. In `fence pred, succ`, the predecessor accesses before the fence complete before the successor accesses after it become visible to other harts and devices. The operands name the categories, and `iorw` covers device input, device output, memory reads and memory writes.

## Official definition

> Verbatim excerpt from the RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture, Version 20260120. Copyright (c) RISC-V International, used under CC BY 4.0. Attribution in the References section.

FENCE instructions are used to order device I/O and memory accesses as viewed by other RISC-V harts and external devices or coprocessors. Any combination of device input (I), device output (O), memory reads (R), and memory writes (W) may be ordered with respect to any combination of the same. Informally, no other RISC-V hart or external device can observe any operation in the `successor` set following a FENCE before any operation in the `predecessor` set preceding the FENCE. memorymodel provides a precise description of the RISC-V memory consistency model.

FENCE instructions also order memory reads and writes made by the hart as observed by memory reads and writes made by an external device. However, FENCE instructions do not order observations of events made by an external device using any other signaling mechanism.

> A device might observe an access to a memory location via some external communication mechanism, e.g., a memory-mapped control register that drives an interrupt signal to an interrupt controller. This communication is outside the scope of the FENCE ordering mechanism and hence FENCE instructions can provide no guarantee on when a change in the interrupt signal is visible to the interrupt controller. Specific devices might provide additional ordering guarantees to reduce software overhead but those are outside the scope of the RISC-V memory model.

The EEI will define what I/O operations are possible, and in particular, which memory addresses when accessed by load and store instructions will be treated and ordered as device input and device output operations respectively rather than memory reads and writes. For example, memory-mapped I/O devices will typically be accessed with uncached loads and stores that are ordered using the I and O bits rather than the R and W bits. Instruction-set extensions might also describe new I/O instructions that will also be ordered using the I and O bits in a FENCE instruction.

The FENCE mode field `fm` defines the semantics of the FENCE instruction. A `FENCE` (with `fm`=`0000`) orders all memory operations in its predecessor set before all memory operations in its successor set.

A `FENCE.TSO` instruction is encoded as a FENCE instruction with `fm`=`1000`, `predecessor`=`RW`, and `successor`=`RW`. `FENCE.TSO` orders all load operations in its predecessor set before all memory operations in its successor set, and all store operations in its predecessor set before all store operations in its successor set. This leaves `non-AMO` store operations in the `FENCE.TSO's` predecessor set unordered with `non-AMO` loads in its successor set.

> Because `FENCE RW,RW` imposes a superset of the orderings that `FENCE.TSO` imposes, it is correct to ignore the `fm` field and implement `FENCE.TSO` as `FENCE RW,RW`.

The unused fields in the FENCE instructions--`rs1 and rd`--are reserved for finer-grain fences in future extensions. For forward compatibility, base implementations shall ignore these fields#, and standard software shall zero these fields. Likewise, many `fm` and predecessor/successor set settings are also reserved for future use. Base implementations shall treat all such reserved configurations as `FENCE` instructions (with `fm`=`0000`), and standard software shall use only non-reserved configurations.

> We chose a relaxed memory model to allow high performance from simple machine implementations and from likely future coprocessor or accelerator extensions. We separate out I/O ordering from memory R/W ordering to avoid unnecessary serialization within a device-driver hart and also to support alternative non-memory paths to control added coprocessors or I/O devices. Simple implementations may additionally ignore the `predecessor and successor` fields and always execute a conservative FENCE on all operations.

## References

1. RISC-V International. The RISC-V Instruction Set Manual, Volume I: Unprivileged Architecture. Version 20260120. Section 2.7, Memory Ordering Instructions, page 35. [PDF](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf#page=54)

---

View on [lyszt.net](https://lyszt.net/academia/resources/riscv/reference/fence). This page is generated from the [LYSZT reference pipeline](https://lyszt.net).
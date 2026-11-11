# RISC-V instruction reference

Generated from the LYSZT reference pipeline.


## Arithmetic

- [add](./add.md) - Add two registers together.
- [sub](./sub.md) - Subtract one register from another.
- [addi](./addi.md) - Add a small constant to a register.
- [mul](./mul.md) - Multiply, keeping the low 32 bits.
- [mulh](./mulh.md) - High 32 bits of a signed product.
- [mulhsu](./mulhsu.md) - High 32 bits of a signed-unsigned product.
- [mulhu](./mulhu.md) - High 32 bits of an unsigned product.
- [div](./div.md) - Signed integer division.
- [divu](./divu.md) - Unsigned integer division.
- [rem](./rem.md) - Signed remainder (modulo).
- [remu](./remu.md) - Unsigned remainder.
- [neg](./neg.md) - Flip the sign of a number.

## Bitwise logic

- [and](./and.md) - Bitwise AND of two registers.
- [or](./or.md) - Bitwise OR of two registers.
- [xor](./xor.md) - Bitwise exclusive-OR.
- [andi](./andi.md) - AND with a constant.
- [ori](./ori.md) - OR with a constant.
- [xori](./xori.md) - XOR with a constant.
- [not](./not.md) - Flip every bit.

## Shifts

- [sll](./sll.md) - Shift bits left (by a register).
- [srl](./srl.md) - Shift bits right, zero-filled.
- [sra](./sra.md) - Shift right, keeping the sign.
- [slli](./slli.md) - Shift left by a fixed amount.
- [srli](./srli.md) - Shift right by a constant, zero-filled.
- [srai](./srai.md) - Shift right by a constant, sign-kept.

## Compare & set

- [slt](./slt.md) - Set to 1 if less than (signed).
- [sltu](./sltu.md) - Set if less than (unsigned).
- [slti](./slti.md) - Set if less than a constant (signed).
- [sltiu](./sltiu.md) - Set if less than a constant (unsigned).
- [seqz](./seqz.md) - Set to 1 if the value is zero.
- [snez](./snez.md) - Set to 1 if the value is non-zero.

## Memory

- [lw](./lw.md) - Load a 32-bit word from memory.
- [lh](./lh.md) - Load a 16-bit halfword (signed).
- [lb](./lb.md) - Load one byte (signed).
- [lhu](./lhu.md) - Load a 16-bit halfword (unsigned).
- [lbu](./lbu.md) - Load one byte (unsigned).
- [sw](./sw.md) - Store a 32-bit word to memory.
- [sh](./sh.md) - Store the low 16 bits.
- [sb](./sb.md) - Store the low 8 bits.
- [la](./la.md) - Load the address of a label.
- [li](./li.md) - Load any constant into a register.
- [mv](./mv.md) - Copy one register to another.

## Branches

- [beq](./beq.md) - Jump if two registers are equal.
- [bne](./bne.md) - Jump if two registers differ.
- [blt](./blt.md) - Jump if less than (signed).
- [bge](./bge.md) - Jump if greater or equal (signed).
- [bltu](./bltu.md) - Jump if less than (unsigned).
- [bgeu](./bgeu.md) - Jump if greater or equal (unsigned).
- [beqz](./beqz.md) - Jump if the register is zero.
- [bnez](./bnez.md) - Jump if the register is non-zero.
- [bltz](./bltz.md) - Jump if the register is negative.
- [bgez](./bgez.md) - Jump if the register is zero or positive.
- [bgtz](./bgtz.md) - Jump if the register is positive.
- [blez](./blez.md) - Jump if the register is zero or negative.
- [bgt](./bgt.md) - Jump if greater than (signed).
- [ble](./ble.md) - Jump if less or equal (signed).

## Jumps & functions

- [jal](./jal.md) - Call: jump and save the return spot.
- [jalr](./jalr.md) - Jump to a computed address, and link.
- [j](./j.md) - Jump unconditionally.
- [jr](./jr.md) - Jump to an address in a register.
- [call](./call.md) - Call a function.
- [ret](./ret.md) - Return from a function.
- [lui](./lui.md) - Load a constant into the upper bits.
- [auipc](./auipc.md) - Add an upper constant to the PC.

## System

- [ecall](./ecall.md) - Ask the system to do something.
- [nop](./nop.md) - Do nothing for one instruction.
- [ebreak](./ebreak.md) - Stop the program at a breakpoint.
- [fence](./fence.md) - Order device I/O and memory accesses.
- [mret](./mret.md) - Return from a trap handler.
- [wfi](./wfi.md) - Wait until an interrupt arrives.
- [csrrw](./csrrw.md) - Swap a register with a control register.
- [csrrs](./csrrs.md) - Read a control register and set bits in it.
- [csrrc](./csrrc.md) - Read a control register and clear bits in it.
- [csrrwi](./csrrwi.md) - Write a constant into a control register and read the old value.
- [csrrsi](./csrrsi.md) - Read a control register and set bits from a constant.
- [csrrci](./csrrci.md) - Read a control register and clear bits from a constant.
- [csrr](./csrr.md) - Read a control register.
- [csrw](./csrw.md) - Write a register into a control register.
- [csrs](./csrs.md) - Set bits in a control register.
- [csrc](./csrc.md) - Clear bits in a control register.
- [csrwi](./csrwi.md) - Write a constant into a control register.
- [csrsi](./csrsi.md) - Set bits in a control register from a constant.
- [csrci](./csrci.md) - Clear bits in a control register from a constant.

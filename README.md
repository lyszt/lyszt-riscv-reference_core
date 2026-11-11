# LYSZT RISC-V references

<img width="1542" height="789" alt="image" src="https://github.com/user-attachments/assets/ee77147e-e98d-40e5-8106-2f2edad5798e" />


Open mirror of the LYSZT RISC-V instruction reference, rendered at
[lyszt.net](https://lyszt.net/academia/resources/riscv/reference).

This is documentation of the RISC-V instruction set written for people who are
learning assembly, with the purpose of explaining clearly what the
instruction does, in a readable manner.

## Purpose

LYSZT aims to make RISC-V documentation easier to learn from and navigate. The
official instruction set manual is the authoritative source for architectural
definitions, but its technical presentation can be difficult to approach when
learning assembly for the first time.

These references provide an additional layer of explanation for each
instruction, and the output is translated to many languages so the non-english speaking public can read it and learn.
They are intended to help readers understand what an instruction does, how it operates on registers
and memory, and how its encoding relates to its behavior.

The official definitions remain available alongside the explanations, allowing
readers to compare the descriptions with the architectural specification and
use the references as a starting point for further study.

## Contents

- `reference/` - one page per instruction: curated description, the official
  definition excerpted from the RISC-V manual, encoding, expansions and references.

## Conventions

- Official definition sections are verbatim excerpts of the RISC-V Instruction
  Set Manual, Volume I: Unprivileged Architecture
- Description sections are written by collaborators.

## License

Apache License 2.0 for the content of this repository. Official definition
sections quote the RISC-V Instruction Set Manual, (c) RISC-V International,
and remain under CC BY 4.0

## Contributing

Found an error, or an explanation that could be clearer? Open an issue or a
pull request.

## Rules

Readability comes before everything else, no matter who or what wrote the
text. A description is ready when a beginner can picture the instruction
after one reading, and anything that needs a second pass is not. Padding,
decoration and repetition are turned away, whatever their source.


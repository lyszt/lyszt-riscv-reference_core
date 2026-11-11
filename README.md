# LYSZT RISC-V reference

Open mirror of the LYSZT RISC-V instruction reference, generated from the
[lyszt.net](https://lyszt.net) reference pipeline.

## Contents

- `reference/` - one page per instruction: curated description, the official
  definition excerpted from the RISC-V manual, encoding, expansions and references.

## Conventions

- Official definition sections are verbatim excerpts of the RISC-V Instruction
  Set Manual, Volume I: Unprivileged Architecture, Version 20260120,
  pinned to commit 6ad05e3d of riscv/riscv-isa-manual.
- Description sections are written by colaborators.

## License

CC BY 4.0. Official excerpts are from the RISC-V Instruction Set Manual,
(c) RISC-V International, used under CC BY 4.0; keep the attribution in the
References section when redistributing. See ATTRIBUTION.md.

## Regenerating

The pages are generated, not hand-edited. From the LYSZT site repository:


```bash
bun run scripts/reference/export-mirror.mjs ../lyszt-riscv-reference
```

Corrections flow through the LYSZT content process, not as direct edits here.

## Canonical

Each page links to its canonical rendering on
[lyszt.net](https://lyszt.net/academia/resources/riscv/reference).

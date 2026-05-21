# GPL dependency policy

CorBi should not merge GPL-derived MAX30100 implementation work into `main` unless the whole repository is intentionally relicensed under a GPL-compatible license.

## Current decision

- Keep GPL-dependent MAX30100 experiments on isolated branches.
- Mark GPL-dependent branches clearly in README or PR descriptions.
- Prefer a clean-room MAX30100 driver, permissively licensed alternative, or transport-only boundary before merging sensor logic to `main`.

## Rationale

The current MAX30100 Arduino library is GPL-3.0. Linking it directly into CorBi Reader makes the firmware a derivative work under GPL terms. That conflicts with the project direction of keeping future licensing flexible.

## Practical rule

Any PR that adds `oxullo/MAX30100lib` must stay draft until the licensing decision is explicitly accepted.

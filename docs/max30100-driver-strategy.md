# MAX30100 driver strategy

The existing MAX30100 library is useful for early experiments, but it is not the long-term Reader implementation.

## Decision

Reader should move toward a project-owned MAX30100 raw-sample driver.

## Why

- The current library's BPM update rate is tied to beat detection, which is too sparse for CorBi visualization.
- The library is GPL-3.0, which blocks clean integration into a permissively licensed or future commercial-friendly project.
- CorBi needs raw IR/Red samples for downstream Core-side algorithms and LLM/context experiments.

## Migration path

1. Keep GPL library experiments isolated and draft-only.
2. Use raw-sample BLE output to validate the desired data contract.
3. Replace library calls with a minimal driver that configures MAX30100 registers and reads FIFO samples.
4. Validate the clean driver against the same Core receiver and BLE output contract.

## Non-goal

Reader does not need to solve high-quality BPM estimation in firmware before the raw stream is stable.

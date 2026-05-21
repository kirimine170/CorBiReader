# Heart-rate calculation strategy

CorBi Reader should prioritize raw optical samples over firmware-side BPM calculation.

## Decision

- Reader sends IR and Red raw samples at the highest stable BLE cadence.
- Core calculates BPM from raw samples, initially with a frequency-domain or peak-interval estimator.
- Reader may later add lightweight beat events, but they should be additional data, not the only heart-rate source.

## Rationale

The MAX30100 library's beat detector updates BPM only when it detects a beat. That makes downstream visualization feel sparse and makes algorithm tuning difficult. Raw samples preserve enough information for Core-side experiments such as FFT, filtering, peak detection, and confidence scoring.

## Output contract

Reader should expose:

- IR raw samples
- Red raw samples
- A monotonically increasing order value for missing-data detection

Core can derive:

- BPM
- pulse events
- signal quality

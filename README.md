# pulsar-best 2.4.0

Own-only lossless compressor. **Core-Lite.** Public source for official benches.

Copyright (c) 2026 Corey Tasz / Slid Phi Labs.

**Silesia (12 files, individually):** **56,654,942** bytes of 211,938,580 (0.2673).  
DECODE_OK 12/12. Beats gzip-9 12/12. Loses to bzip2-9 12/12 (+3.94%).

Not a rank claim against paq8px, cmix, or zpaq. Combined GC and AWARE are **not in this repo**.

## What this is

Compressor A (demonstrator). BW22 / OZL2 / PZ22 picker. No taught residual core.

## What this is not

- Not Combined GC
- Not AWARE 1.19.2
- Not the Drive-lock encoder (dickens 243,675 is a reference constant, not this output)
- Not Autonoma / Blackjack production

Commercial inquiries for the private engines: Slid Phi Labs / Corey Tasz.

## Official packet

See [OFFICIAL/](OFFICIAL/). Silesia OSCB line for the 2.3.1 measurement (same codec path):

```
56654942 2907 18482 2647 1886 2936 2947 1307 4719 5121 8948 4276 473  pulsar-best 2.3.1
```

Industry calibration: gzip -9 = 67,631,990; bzip2 = 54,506,769.

## Build

```
cargo test --lib
cargo run --release --bin pulsar -- encode IN -o OUT
cargo run --release --bin pulsar -- decode OUT -o BACK
```

## License

**2.4.0+ : GPL-3.0-or-later.**  
2.3.1 and earlier snapshots remain MIT. See `LICENSE` and `LICENSE-CHANGE.md`.

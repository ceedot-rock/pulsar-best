# pulsar-best 2.3.1

Own-only lossless compressor. Public source for official benches.

**Silesia (12 files, individually):** **56,654,942** bytes of 211,938,580 (0.2673).  
DECODE_OK 12/12. Beats gzip-9 12/12. Loses to bzip2-9 12/12 (+3.94%).

Not a rank claim against paq8px, cmix, or zpaq. Combined GC (AWARE+XZ1, 47,752,368) is a disclosed xz wrap and lives in [combined-gc-view](https://github.com/ceedot-rock/combined-gc-view).

## Official packet

See [OFFICIAL/](OFFICIAL/). Submitted to Matt Mahoney’s [Silesia Open Source Compression Benchmark](https://mattmahoney.net/dc/silesia.html) on 2026-08-31.

```
56654942 2907 18482 2647 1886 2936 2947 1307 4719 5121 8948 4276 473  pulsar-best 2.3.1
```

Industry calibration on the same files matches Mahoney: gzip -9 = 67,631,990; bzip2 = 54,506,769.

## Build

Zero Cargo dependencies.

```
cargo test --lib
cargo run --release --bin pulsar -- encode IN -o OUT
cargo run --release --bin pulsar -- decode OUT -o BACK
```

Encode keeps the smallest blob among OZL2, PZ22 (files < 64 KiB), and BW22 that roundtrips to the original. On Silesia the winner is BW22: RLE-1 + sentinel BWT (900 KiB) + MTF + Wheeler RLE-0 + order-0 rANS.

## License

MIT.

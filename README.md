# Shivanshu Sharma

**C++ systems engineer · low-latency trading infrastructure · quant research tooling · Bengaluru**

I build systems that are fast, measured, and tested against something other than themselves. Production C++ at LG Soft India (automotive connectivity: RIL/telephony, 4G/5G stack, V2X on Qualcomm platforms). On my own: trading systems and research infrastructure.

## Highlights

**QUANT research platform** *(private repo, walkthrough on request)*
Bybit ingest → TimescaleDB + mmap'd binary store → C++23 engine → FastAPI → React strategy lab.

- **786M** 1-minute candles ingested across 842 perpetuals, 0 failed downloads, 0 missing minutes on the research set
- **2.0 ns/bar**: a 3.4M-bar backtest in 6.9 ms on one core, 2.6× faster than TA-Lib + Numba with bit-identical trades
- **201/201** TA-Lib functions bit-identical to an independent reference; a look-ahead property test with a negative control that proves it can fail
- **19,110** SMA pairs × 10 coins, checked with Hansen SPA, Romano-Wolf and walk-forward. Result: no edge, so no capital deployed

**Live arbitrage engine**: C++20, single binary, trading ETH/USDT on multi-exchange spot and perpetuals. Pinned cores under SCHED_FIFO, lock-free SPSC ring, branchless signal evaluation, 4-gate dispatch, Ed25519 signing, RDTSCP timing.

## Open source

| Repo | What it is |
|---|---|
| [itch-feed-handler](https://github.com/shivanshu1177/itch-feed-handler) | C++20 NASDAQ ITCH 5.0 handler: A/B feed failover, MoldUDP64 gap recovery, 8-shard lock-free book, SeqLock BBO, zero hot-path allocations |
| [RTES](https://github.com/shivanshu1177/RTES) | Price-time priority matching engine, no heap allocation on the matching path |
| [ulmd](https://github.com/shivanshu1177/ulmd) | Zero-copy SPSC market-data pipeline with TSC timestamps and latency-percentile benchmarks |

## Stack

- **Languages:** C++17/20/23, Python, TypeScript, SQL
- **Systems:** Linux/POSIX, multithreading, lock-free queues, mmap, epoll, CPU pinning, IPC over UNIX domain sockets
- **Data:** pcap and HDF files, binary formats, TimescaleDB, PostgreSQL, simdjson
- **Testing:** pytest, sanitizers, differential and property testing, fuzzing
- **Quant:** TA-Lib, QuantStats, pyfolio, Qlib, Numba; SPA, Romano-Wolf, PBO, deflated Sharpe
- **Backend:** FastAPI, nanobind, React, Docker, CI/CD

## Contact

[shivanshu.prof@gmail.com](mailto:shivanshu.prof@gmail.com) · [LinkedIn](https://www.linkedin.com/in/shivanshu-sharma-4014931b8/)

<sub>Benchmarks: Apple M2, single thread, warm cache, median of ≥20 runs after warm-up.</sub>

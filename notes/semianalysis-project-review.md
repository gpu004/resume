# SemiAnalysis resume project review

Reviewed October 12, 2026. The supplied Episode 035 transcript describes the consulting business rather than a single job specification. I used its emphasis on GPU performance projections, custom analytical dashboards, technical diligence, and clear research outputs to select projects. The [official careers page](https://semianalysis.com/semianalysis-careers/) also lists consulting roles involving technical analysis and analytical models.

The current resume is two pages. Its projects are GPU Napkin Math, VLIW/SIMD Kernel Optimization, and Monkey Compiler. Horizon, Market Maker Simulator, and the OCaml Ledger State Machine were removed at the user's request. GPU Napkin Math was refreshed against the latest Rust implementation and October 12 measurements. The other evidence below preserves the original project review. Python, SQL, OCaml, PyTorch, and performance-analysis skills were added based on the reviewed implementations.

## Reviewed projects and evidence

| Project | Reason to include | Evidence reviewed |
| --- | --- | --- |
| [GPU Napkin Math](https://github.com/gpu004/napkin-math-gpu) | GPU performance projections, LLM inference arithmetic, and workload cost analysis | Rust CLI, LLM and cost modules, shared profile types, Rust/CUDA calibration harness, four measured GPU profiles, methodology guide, and commit history |
| [VLIW/SIMD Kernel Optimization](https://github.com/gpu004/original_performance_takehome) | Concrete performance result and an explanation of the optimization process | Modified kernel, four optimization reports, commit history, and unchanged upstream tests |
| [Horizon](https://github.com/gpu004/mongomongo/tree/main/horizon) | Reproducible experiments, independent verification, recovery, and database infrastructure | README, experiment report, controller, recovery code, MongoDB ledger, and test inventory |
| [OCaml Ledger State Machine](https://github.com/gpu004/6666) | Finance-related systems work with explicit semantics and correctness checks | README, state machine, ledger, scenario tests, QCheck properties, and workload benchmark source |

## Checks performed this session

### Simulated kernel

Reviewed revision `1a76cbd927`. The project is a fork of Anthropic's challenge; the resume attributes the simulator to Anthropic and describes the optimization contribution.

Ran the current kernel with Python 3.12.14 against `tests/submission_tests.py`. Both that file and `tests/frozen_problem.py` matched the current upstream files byte for byte.

- Workload: tree height 10, 16 rounds, batch size 256.
- Result: 2,910 simulated cycles against the supplied baseline of 147,734 cycles.
- Ratio: 50.7677, rounded to 50.8x in the resume.
- Correctness test passed across eight random inputs. The baseline and updated-starting-point speed thresholds also passed.
- Six stricter speed thresholds failed. The full suite therefore exited with status 1, with three tests passing and six failing. The resume claims output correctness and the measured speedup, not that the full suite passed.
- This is a simulated VLIW/SIMD result, not a GPU, CUDA, or production inference speedup.

### GPU estimator

Refreshed against revision [`c75638e298163ac8c0b97dc743886378e24224f4`](https://github.com/gpu004/napkin-math-gpu/commit/c75638e298163ac8c0b97dc743886378e24224f4). The former Python estimator and Astro dashboard have been replaced by a Rust workspace with `napkin`, `napkin-profile`, and `napkin-bench` crates.

Reviewed the current README, Cargo workspace, CLI, [LLM recipe implementation](https://github.com/gpu004/napkin-math-gpu/blob/c75638e298163ac8c0b97dc743886378e24224f4/crates/napkin/src/llm.rs), [cost implementation](https://github.com/gpu004/napkin-math-gpu/blob/c75638e298163ac8c0b97dc743886378e24224f4/crates/napkin/src/cost.rs), benchmark entry point, Modal launcher, and all four measured profiles through GitHub.

- Roofline estimates account for compute, HBM traffic, transfers, launch overhead, and serial or overlapped stages. Copy estimates distinguish synchronous per-copy latency from an asynchronous lower bound.
- LLM recipes derive prefill/decode FLOPs, weight and KV-cache traffic, and resident memory from model dimensions, batch, context, and precision. These are analytical lower bounds for dense decoder-only models, not measured model throughput. Memory fit distinguishes shardable weights/cache from replicated per-GPU memory.
- Cost estimates include GPU count, utilization, startup, idle time, billing increments, and user-supplied or dated provider prices. Tokens per dollar requires a supplied workload count or rate; it is not inferred from peak FLOPs.

The October 12, 2026 calibrations use two GPUs per Modal request, CUDA 12.9, Rust/cudarc, CUDA-event timing, and cuBLAS GEMM. The checked-in records contain seven rounds, raw samples, hardware/software metadata, and passing correctness flags:

| GPU | Dense BF16 GEMM | HBM copy bandwidth |
| --- | ---: | ---: |
| A100 SXM 80GB | 265.2066 TFLOP/s | 1,738.0673 GB/s |
| H100 SXM 80GB | 733.5508 TFLOP/s | 3,003.0502 GB/s |
| B200 | 1,584.6249 TFLOP/s | 6,322.0785 GB/s |
| B300 SXM6 | 1,823.0299 TFLOP/s | 6,486.5177 GB/s |

The resume rounds the [B300 record](https://github.com/gpu004/napkin-math-gpu/blob/c75638e298163ac8c0b97dc743886378e24224f4/profiles/b300.measured.json) to 1.82 PFLOP/s dense BF16 GEMM and 6.49 TB/s HBM copy bandwidth. GEMM uses an 8192 x 8192 x 8192 shape. HBM copy bandwidth counts both read and write bytes, using decimal GB/s. Measured values remain separate from datasheet ceilings.

No new GPU allocation, benchmark run, Rust CLI execution, or project test run was performed for this refresh. These are recorded calibration results. The [evidence guide](https://github.com/gpu004/napkin-math-gpu/blob/main/BENCHMARKS.md) still requires replacement by upstream authority metric by metric before calling the profiles canonical. The previous Python CLI result and August H100 figures are superseded in the resume.

### Horizon and OCaml ledger

Reviewed implementation and test source, without rerunning their full suites or benchmarks. No new throughput, model-quality, production deployment, or cluster-scale claim was added.

Horizon was reviewed at `dc784906ad4fa130e4a23a5fe50b99dac67b22ac`. Its recorded results include scripted experiments, so the resume describes the harness and verification mechanisms rather than attributing a latency improvement to a live model.

The OCaml ledger was reviewed at `e0be6d681045fb626759c0e2155e4458aa8cc9ea`. It is an experimental in-memory core. The copied Zig server components are upstream work. Full TigerBeetle equivalence and server integration remain incomplete; no claim of a complete replacement database or speed advantage over TigerBeetle was added.

## Other candidates considered

Repository metadata was reviewed across the public account, including fork status. Candidate source trees and READMEs were inspected before selection.

- Multi-head self-attention and multilingual tokenization are relevant learning exercises, but the GPU estimator and kernel optimization provide stronger evidence for this application.
- The DuckDB recommendation query has useful analytical work, but its README's local timing lacks a hardware record and was not rerun here.
- Computer Vision Project 2 is substantial coursework, with less direct connection to the consulting work described in the podcast.
- The million-sphere visualization has no recorded hardware-specific FPS evidence; the headline 60 FPS claim was not used.
- The macOS DuckDB viewer documents an unresolved query problem.
- Forks such as Mojo GPU Puzzles were not treated as original projects solely because they appear on the account.

## Resume validation

Compiled `basic/main.tex` with Tectonic. Confirmed two letter-sized pages and inspected both rendered pages for clipping, overlap, and broken section transitions. Project links point to the reviewed GitHub repositories. The compiler emits a header-box warning in the existing class; the rendered header is visibly within the page.

# SemiAnalysis resume project review

Reviewed October 12, 2026. The supplied Episode 035 transcript describes the consulting business rather than a single job specification. I used its emphasis on GPU performance projections, custom analytical dashboards, technical diligence, and clear research outputs to select projects. The [official careers page](https://semianalysis.com/semianalysis-careers/) also lists consulting roles involving technical analysis and analytical models.

The updated resume is two pages. Existing experience and projects are retained. Four projects were added, with GPU performance work first. Python, SQL, OCaml, PyTorch, and performance-analysis skills were added based on the reviewed implementations.

## Added projects and evidence

| Project | Reason to include | Evidence reviewed |
| --- | --- | --- |
| [GPU Napkin Math](https://github.com/gpu004/napkin-math-gpu) | Closest match to the podcast's performance projections and adjustable dashboards | Python estimator, typed profiles, Astro dashboard, PyTorch calibration harness, H100 raw results, methodology guide, and commit history |
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

Reviewed revision `be2d8652e4`. Ran the Python CLI using the checked-in H100 profile:

```text
dtype=bf16, FLOPs=2e14, HBM bytes=1e12, H2D bytes=2e9, launches=20
compute floor: 278.786 ms
memory floor: 333.370 ms
transfer: 36.068 ms
launches: 0.093 ms
total estimate: 369.531 ms, memory-bound
```

The resume's hardware figures come from the [checked-in H100 calibration](https://github.com/gpu004/napkin-math-gpu/blob/main/results/h100-sxm.json), captured August 8, 2026 on two Modal H100 GPUs. The profile records dense BF16 GEMM at 717.3949 TFLOP/s and HBM copy bandwidth at 2,999.6720 GB/s. It also records hardware, software versions, samples, and correctness checks.

No new GPU allocation or benchmark run was performed. These are recorded prototype microbenchmark results. The [evidence guide](https://github.com/gpu004/napkin-math-gpu/blob/main/BENCHMARKS.md) explicitly distinguishes them from canonical measurements using upstream NVIDIA tools. B200/B300 profiles use vendor ceilings; no measured Blackwell performance is claimed.

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

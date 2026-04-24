# Neotoi Coder v3.1

A Rust/Dioxus 0.7 specialist LLM — **94.81%** on a 103-question weighted exam.

**[HuggingFace — Download GGUF](https://huggingface.co/rockypod/neotoi-coder)**
**[Install via Ollama](https://ollama.com/rockypod/neotoi-coder)** — `ollama pull rockypod/neotoi-coder`
**[Read the whole story on RockyPod.com →](https://rockypod.com/blog/neotoi-coder-v2-release)**

## What's in this repo

- `dataset/` — Full 4,880-example RAFT training dataset used for v3.1
- `exam/` — Full 103-question weighted exam and scoring rubric
- `exam/results/` — Per-question v3.1 model outputs for every Q1–Q103
- `eval/` — Benchmark comparing Neotoi vs general models on Dioxus tasks
- `integration/` — Setup guides for Continue.dev, LM Studio, Ollama, Zed

Full transparency: dataset, exam questions, and per-question results are
published here alongside the weights on HuggingFace.

## Quick Start

### Ollama (any platform)
```bash
ollama pull rockypod/neotoi-coder
ollama run rockypod/neotoi-coder "Write a Dioxus 0.7 counter with use_signal"
```

Tags: `:v3.1` (current), `:latest` (tracks `:v3.1`), `:v3` and `:v2` (legacy).

### LM Studio
Download `neotoi-coder-v3.1-q4_k_m.gguf` from HuggingFace.
See `integration/lm_studio.md` for prompt template setup.

### Apple Silicon (mlx_lm)
```bash
pip install mlx-lm
mlx_lm.server --model rockypod/neotoi-coder --adapter-path mlx-v3.1 --port 8081
```
Or download the `mlx-v3.1/` directory from HuggingFace and point `--model` at the local path.

### llama.cpp
```bash
./llama-cli -m neotoi-coder-v3.1-q4_k_m.gguf -ngl 99 --temp 0.2 \
  -p "<|im_start|>user\nYour question<|im_end|>\n<|im_start|>assistant\n<think>"
```

## What's New in v3.1

- **T1 Fundamentals → 100%** (+8.3 pts vs v3.0)
- **T6 Hard Reasoning → 100%** (+25 pts vs v3.0, clean sweep)
- **T8 GlobalSignal/i18n → 100%** (+12.5 pts)
- **T10 Dioxus 0.7.4 → 100%** (+16.7 pts)
- **8 tiers at 100%** overall (T1, T5, T6, T7, T8, T9, T10, T11)
- **New dataset topics:**
  - **T39** — v3.0 exam-gap corrections
  - **T40** — DaisyUI 5 component coverage on Tailwind v4
  - **T41** — Signals deep-dive (`$state`, `Signal<T>`, `GlobalSignal`,
    `.peek()`, `.write()`, `ReadOnlySignal`, composition)
  - **T42** — Router patterns (`#[derive(Routable)]`, nested routes,
    layout routes, route guards, query parameters)
  - **T43** — Async / server-function composition (`use_resource`
    three-arm match, cancellation, streaming, `ServerFnError`)
- **Dataset:** **4,880 curated examples across 43 topics** (up from 4,535)

## Score

| Tier | Score | Max | Status |
|---|---|---|---|
| T1 Fundamentals | 12.0/12 | 12 | ✅ Perfect |
| T2 RSX Syntax | 10.0/12 | 12 | ⚠️ 83.3% |
| T3 Signal Hygiene | 11.0/12 | 12 | ✅ 91.7% |
| T4 WCAG/ARIA | 16.5/21 | 21 | ⚠️ 78.6% |
| T5 use_resource | 12.0/12 | 12 | ✅ Perfect |
| T6 Hard Reasoning | 20.0/20 | 20 | ✅ Perfect |
| T7 Primitives+CSS | 18.0/18 | 18 | ✅ Perfect |
| T8 GlobalSignal/i18n | 12.0/12 | 12 | ✅ Perfect |
| T9 Static Navigator | 9.0/9 | 9 | ✅ Perfect |
| T10 Dioxus 0.7.4 | 12.0/12 | 12 | ✅ Perfect |
| T11 Server Functions | 4.5/4.5 | 4.5 | ✅ Perfect |
| **Total** | **137.0/144.5** | **144.5** | **✅ 94.81%** |

**94.81%** — clears the 90% publication bar with 4.81 points to spare.
Raw: 97/103.

Remaining gaps — all 6 failures are `rsx!` macro drops or `cx.render`
carryover on RSX-heavy questions (Q17, Q22, Q30, Q37, Q39, Q43),
targeted for v3.2. Full rubric and per-question outputs in `exam/`.

## Version History

| Version | Score | Exam | Dataset |
|---|---|---|---|
| v1.0 | 51/60 (85.0%) | 60Q standard | — |
| v2.0 | 135.5/140 (96.8%) | 100Q weighted | 4,185 |
| v3.0 | 124.0/144.5 (85.8%) | 103Q weighted | 4,535 |
| **v3.1** | **137.0/144.5 (94.81%)** | **103Q weighted** | **4,880** |

## Benchmark

See `eval/dioxus_benchmark.md` for tasks where general models fail
and Neotoi succeeds.

## License

Neotoi Coder Community License v1.0 — commercial use of outputs
permitted, weight redistribution prohibited, mental health deployment
requires written permission. See `LICENSE`.

Built on a homelab RTX 3090 Ti in Washington State.

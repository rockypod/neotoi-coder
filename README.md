# Neotoi Coder v3.0

A Rust/Dioxus 0.7 specialist LLM — 85.8% on a 103-question weighted exam.

**[HuggingFace — Download GGUF](https://huggingface.co/rockypod/neotoi-coder)**
**[Install via Ollama](https://ollama.com/rockypod/neotoi-coder)** — `ollama pull rockypod/neotoi-coder`
**[Read the whole story on RockyPod.com →](https://rockypod.com/blog/neotoi-coder-v2-release)**

## What's in this repo

- `dataset/` — Full 4,535-example RAFT training dataset used for v3.0
- `exam/` — Full 103-question weighted exam and scoring rubric
- `exam/results/` — Per-question v3.0 model outputs for every Q1–Q103
- `eval/` — Benchmark comparing Neotoi v3.0 vs general models on Dioxus tasks
- `integration/` — Setup guides for Continue.dev, LM Studio, Ollama, Zed

Full transparency: dataset, exam questions, and per-question results are
published here alongside the weights on HuggingFace.

## Quick Start

### Ollama (any platform)
```bash
ollama pull rockypod/neotoi-coder
ollama run rockypod/neotoi-coder "Write a Dioxus 0.7 counter with use_signal"
```

### LM Studio
Download `neotoi-coder-v3-q4_k_m_patched.gguf` from HuggingFace.
See `integration/lm_studio.md` for prompt template setup.

### Apple Silicon (mlx_lm) — MLX build coming in v3.1
```bash
pip install mlx-lm
mlx_lm server --model /path/to/neotoi-v3-mlx --port 8081
```

### llama.cpp
```bash
./llama-cli -m neotoi-coder-v3-q4_k_m_patched.gguf -ngl 99 --temp 0.2 \
  -p "<|im_start|>user\nYour question<|im_end|>\n<|im_start|>assistant\n<think>"
```

## What's New in v3.0

- **T11 Server Functions** — clean sweep 4.5/4.5 on a brand-new tier
- **Scoped CSS** — `css!()` macro and native `.module.css` (0.7.3)
- **New event handlers** — `onauxclick`, `onscrollend` (0.7.3)
- **Real WebSocket Stream+Sink** — `stream.next()` / `sink.send()` (0.7.4)
- **GlobalSignal cache rebuild** — idiomatic `.write()` on pre-rsx! lets
- **v2.0 fixes** — Q8, Q16, Q21 now passing

## Score

| Tier | Score | Max |
|---|---|---|
| T1 Fundamentals | 11.0/12 | 12 |
| T2 RSX Syntax | 8.0/12 | 12 |
| T3 Signal Hygiene | 9.5/12 | 12 |
| T4 WCAG/ARIA | 19.5/21 | 21 |
| T5 use_resource | 12.0/12 | 12 |
| T6 Hard Reasoning | 15.0/20 | 20 |
| T7 Primitives+CSS | 15.0/18 | 18 |
| T8 GlobalSignal/i18n | 10.5/12 | 12 |
| T9 Static Navigator | 9.0/9 | 9 |
| T10 Dioxus 0.7.4 | 10.0/12 | 12 |
| T11 Server Functions | 4.5/4.5 | 4.5 |
| **Total** | **124.0/144.5** | **144.5** |

**85.8%** — above the 85% release threshold.

Known regression: T2 RSX attribute placement at Q14 / Q15 / Q22,
targeted for v3.1. Full rubric and per-question outputs in `exam/`.

## Version History

| Version | Score | Exam |
|---|---|---|
| v1.0 | 51/60 (85.0%) | 60Q standard |
| v2.0 | 135.5/140 (96.8%) | 100Q weighted |
| v3.0 | 124.0/144.5 (85.8%) | 103Q weighted |

## Benchmark

See `eval/dioxus_benchmark.md` for tasks where general models fail
and Neotoi v3.0 succeeds.

## License

Neotoi Coder Community License v1.0 — commercial use of outputs
permitted, weight redistribution prohibited, mental health deployment
requires written permission. See `LICENSE`.

Built on a homelab RTX 3090 Ti in Washington State.

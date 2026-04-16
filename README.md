# Neotoi Coder v2.0

A Rust/Dioxus 0.7 specialist LLM — 96.8% on a 100-question weighted exam.

**[HuggingFace — Download GGUF + MLX](https://huggingface.co/rockypod/neotoi-coder)**
**[Read the whole story on RockyPod.com →](https://rockypod.com/blog/neotoi-coder-v2-release)**

## What's in this repo

- `eval/` — Benchmark comparing Neotoi v2.0 vs general models on Dioxus tasks
- `integration/` — Setup guides for Continue.dev, LM Studio, Ollama, Zed
- `exam/` — Full 100-question weighted exam and scoring rubric

## Quick Start

### Apple Silicon (mlx_lm)
```bash
pip install mlx-lm
mlx_lm server --model /path/to/neotoi-v2.0-mlx --port 8081
```

### Linux (Ollama)
```bash
ollama create neotoi-coder-v2 -f integration/Modelfile
ollama run neotoi-coder-v2
```

### LM Studio
Download `neotoi-coder-v2.0-q4_k_m.gguf` from HuggingFace.
See `integration/lm_studio.md` for prompt template setup.

## Benchmark

See `eval/dioxus_benchmark.md` for 5 tasks where general models
fail and Neotoi v2.0 succeeds.

## Score

| Tier | Score | Max |
|---|---|---|
| T1 Fundamentals | 11/12 | 12 |
| T2 RSX Syntax | 10/12 | 12 |
| T3 Signal Hygiene | 12/12 | 12 |
| T4 WCAG/ARIA | 21/21 | 21 |
| T5 use_resource | 12/12 | 12 |
| T6 Hard Reasoning | 20/20 | 20 |
| T7 Primitives+CSS | 16.5/18 | 18 |
| T8 GlobalSignal/i18n | 12/12 | 12 |
| T9 Static Navigator | 9/9 | 9 |
| T10 Dioxus 0.7.4 | 12/12 | 12 |
| **Total** | **135.5/140** | **140** |

Built on a homelab RTX 3090 Ti in Washington State.

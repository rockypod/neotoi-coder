# Neotoi Coder

A Rust / Dioxus 0.7 specialist LLM. v3.1 ships in **three sizes** —
8B, 4B, and 14B — all fine-tuned via RAFT (Retrieval-Augmented
Fine-Tuning) on Qwen3 base models.

| Variant | Base | Params | Q4_K_M | Spec exam (104Q weighted, max 144.5) | HF repo |
|---|---|---|---|---|---|
| **8B** (flagship) | Qwen3-8B | 8.2B (6.95B non-embed) | 4.68 GB | **144.5 / 144.5 — 100.00%** | [`rockypod/neotoi-coder-8b`](https://huggingface.co/rockypod/neotoi-coder-8b) |
| 4B | Qwen3-4B | 4.0B (3.6B non-embed, tied) | 2.33 GB | 143.5 / 144.5 — 99.31% | [`rockypod/neotoi-coder-4b`](https://huggingface.co/rockypod/neotoi-coder-4b) |
| 14B (legacy) | Qwen3-Coder-14B | 14.8B (13.2B non-embed) | 8.40 GB | 137.0 / 144.5 — 94.81% | [`rockypod/neotoi-coder`](https://huggingface.co/rockypod/neotoi-coder) (family hub) |

All three clear the 90% publication bar and the 95% release bar with
all per-tier floors PASS. The 8B is the recommended default; pick the
4B if disk / RAM is tight, pick the 14B for the broadest coverage.

**HuggingFace:** [8B](https://huggingface.co/rockypod/neotoi-coder-8b) · [4B](https://huggingface.co/rockypod/neotoi-coder-4b) · [14B / family hub](https://huggingface.co/rockypod/neotoi-coder)
&nbsp; · &nbsp; **[Install via Ollama](https://ollama.com/rockypod/neotoi-coder)**
&nbsp; · &nbsp; **[Read the whole story on RockyPod.com →](https://rockypod.com/blog/neotoi-coder-v2-release)**

## What's in this repo

- `integration/` — Setup guides for Continue.dev, LM Studio, Ollama, Zed

The 4,880-example RAFT training dataset and the 104-question spec exam
are not published — only the integration guides and the model weights
(on HuggingFace) are public. Exam scorecards stay in this README so
you can compare variants without seeing the questions.

## Quick Start

### Ollama (any platform)

```bash
# 8B — recommended default
ollama pull rockypod/neotoi-coder:8b
ollama run rockypod/neotoi-coder:8b "Write a Dioxus 0.7 counter with use_signal"

# 4B — disk / RAM constrained, ~40% faster generation
ollama pull rockypod/neotoi-coder:4b

# 14B — legacy, broadest coverage
ollama pull rockypod/neotoi-coder:15b
```

Tags: `:8b`, `:4b`, `:15b`. Each Modelfile sets `num_ctx 8192`, `temperature 0.2`, and prefills `<think>` on the assistant turn so Qwen3 native chain-of-thought emits by default.

### LM Studio

Download the appropriate Q4_K_M GGUF from its dedicated HuggingFace repo:

- 8B → `neotoi-coder-v3.1-8b-q4_k_m_patched.gguf` (4.68 GB) at [`rockypod/neotoi-coder-8b`](https://huggingface.co/rockypod/neotoi-coder-8b)
- 4B → `neotoi-coder-v3.1-4b-q4_k_m_patched.gguf` (2.33 GB) at [`rockypod/neotoi-coder-4b`](https://huggingface.co/rockypod/neotoi-coder-4b)
- 14B → `neotoi-coder-v3.1-q4_k_m.gguf` (8.40 GB) at [`rockypod/neotoi-coder`](https://huggingface.co/rockypod/neotoi-coder) (family hub also hosts the 14B GGUFs)

See `integration/lm_studio.md` for prompt-template setup.

### llama.cpp

```bash
./llama-cli -m neotoi-coder-v3.1-8b-q4_k_m_patched.gguf -ngl 99 --temp 0.2 \
  -p "<|im_start|>user\nYour question<|im_end|>\n<|im_start|>assistant\n<think>"
```

## v3.1 Score — all three variants

Re-graded 2026-04-26 with the patched `run_grade_v31.py` (Q87 now also
accepts `LANG()` / `THEME()` GlobalSignal accessor calls in addition to
the literal `Signal` token — a false-negative fix that unlocked the
8B's perfect score).

| Tier | Max wt | 8B | 4B | 14B |
|---|---|---|---|---|
| T1 Fundamentals | 12.0 | 12.0 ✅ | 11.0 ⚠️ 91.7% | 12.0 ✅ |
| T2 RSX Syntax | 12.0 | 12.0 ✅ | 12.0 ✅ | 10.0 ⚠️ 83.3% |
| T3 Signal Hygiene | 12.0 | 12.0 ✅ | 12.0 ✅ | 11.0 ✅ 91.7% |
| T4 WCAG / ARIA | 21.0 | 21.0 ✅ | 21.0 ✅ | 16.5 ⚠️ 78.6% |
| T5 use_resource | 12.0 | 12.0 ✅ | 12.0 ✅ | 12.0 ✅ |
| T6 Hard Reasoning | 20.0 | 20.0 ✅ | 20.0 ✅ | 20.0 ✅ |
| T7 Primitives + CSS | 18.0 | 18.0 ✅ | 18.0 ✅ | 18.0 ✅ |
| T8 GlobalSignal / i18n | 12.0 | 12.0 ✅ | 12.0 ✅ | 12.0 ✅ |
| T9 Static Navigator | 9.0 | 9.0 ✅ | 9.0 ✅ | 9.0 ✅ |
| T10 Dioxus 0.7.4 | 12.0 | 12.0 ✅ | 12.0 ✅ | 12.0 ✅ |
| T11 Server Functions | 4.5 | 4.5 ✅ | 4.5 ✅ | 4.5 ✅ |
| **Total weighted** | **144.5** | **144.5** | **143.5** | **137.0** |
| **Total raw (of 103)** | — | **103** | **102** | **97** |
| **Percent** | — | **100.00%** | **99.31%** | **94.81%** |

Tier floors (82% on weight-1.0 / 1.5 tiers, 88% on weight-2.0 tiers): all PASS for all three variants.

The 4B's only miss is Q8 (T1 RSX conversion) — generation truncated mid-`<think>` block. The 14B drops on RSX-heavy questions (Q17, Q22, Q30, Q37, Q39, Q43); v3.2 target.

## What's new in v3.1 (vs v3.0)

- **Two new sizes**: 8B and 4B alongside the 14B base, both surpassing the 14B's score
- **T1 Fundamentals → 100%** on 8B and 14B, 91.7% on 4B (+8.3 pts)
- **T6 Hard Reasoning → 100%** clean sweep, all three variants (+25 pts on 14B)
- **T8 GlobalSignal / i18n → 100%** all three variants (+12.5 pts on 14B)
- **T10 Dioxus 0.7.4 → 100%** all three variants (+16.7 pts on 14B)
- **8 tiers at 100%** on the 14B; 11 tiers at 100% on the 8B (perfect)
- **New dataset topics:**
  - T39 — v3.0 exam-gap corrections
  - T40 — DaisyUI 5 components on Tailwind v4
  - T41 — Signals deep-dive (`use_signal`, `Signal<T>`, `GlobalSignal`, `.peek()`, `.write()`, `ReadOnlySignal`, composition)
  - T42 — Router patterns (`#[derive(Routable)]`, nested routes, layout routes, route guards, query parameters)
  - T43 — Async / server-function composition (`use_resource` three-arm match, cancellation, streaming, `ServerFnError`)
- **Dataset:** 4,880 curated examples across 43 topics (up from 4,535)

## Version history

| Version | Base (params) | Score | Exam | Dataset |
|---|---|---|---|---|
| v1.0 | Qwen3-Coder-14B (14.8B) | 51/60 (85.0%) | 60Q standard | — |
| v2.0 | Qwen3-Coder-14B (14.8B) | 135.5/140 (96.8%) | 100Q weighted | 4,185 |
| v3.0 | Qwen3-Coder-14B (14.8B) | 124.0/144.5 (85.8%) | 103Q weighted | 4,535 |
| v3.1 14B | Qwen3-Coder-14B (14.8B) | 137.0/144.5 (94.81%) | 103Q weighted | 4,880 |
| **v3.1 8B** | **Qwen3-8B (8.2B)** | **144.5/144.5 (100.00%)** | **103Q weighted** | **4,880** |
| v3.1 4B | Qwen3-4B (4.0B, tied) | 143.5/144.5 (99.31%) | 103Q weighted | 4,880 |

## License

Neotoi Coder Community License v1.0 — commercial use of outputs permitted, weight redistribution prohibited, mental health deployment requires written permission. See `LICENSE`.

Built on a homelab RTX 3090 Ti in Washington State.

# LM Studio Setup

1. Download neotoi-coder-v2.0-q4_k_m.gguf from HuggingFace
2. Load in LM Studio
3. Set prompt template:

| Field | Value |
|---|---|
| Before System | `<|im_start|>system` |
| After System | `<|im_end|>` |
| Before User | `<|im_start|>user` |
| After User | `<|im_end|>` |
| Before Assistant | `<|im_start|>assistant\n<think>` |

4. Recommended settings:
- Temperature: 0.2
- Repeat penalty: 1.15
- Max tokens: 4096
- Context length: 16384

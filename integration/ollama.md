# Ollama Setup (Linux)

Create a Modelfile:

FROM neotoi-coder-v2.0-q4_k_m.gguf
PARAMETER temperature 0.2
PARAMETER num_predict 4096
PARAMETER repeat_penalty 1.15
SYSTEM You are Neotoi, an expert Rust and Dioxus 0.7 developer.


Then:
```bash
ollama create neotoi-coder-v2 -f Modelfile
ollama run neotoi-coder-v2
```

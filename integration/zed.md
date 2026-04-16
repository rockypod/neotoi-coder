# Zed Editor Setup

Add to ~/.config/zed/settings.json:

```json
{
  "language_models": {
    "openai": {
      "api_url": "http://localhost:8081/v1",
      "available_models": [
        {
          "name": "neotoi-v2.0-mlx",
          "display_name": "Neotoi Coder v2",
          "max_tokens": 16384
        }
      ]
    }
  },
  "assistant": {
    "default_model": {
      "provider": "openai",
      "model": "neotoi-v2.0-mlx"
    }
  }
}
```

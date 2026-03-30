---
name: stepfun
description: Use this skill when working with Stepfun LLMs (Step-1, Step-2). Triggers when user mentions Stepfun or uses the Stepfun API endpoint.
---

# Stepfun

## What this is
Stepfun provides a suite of large-scale language models including Step-1 (text), Step-1V (multimodal/vision), and Step-2. It offers an OpenAI-compatible API interface, allowing developers to integrate high-performance Chinese-centric LLMs with context windows up to 256k.

## Installation
Stepfun uses the standard OpenAI SDK for integration:
```bash
pip install openai
```

## Key concepts
- **API Compatibility**: Uses the OpenAI client but requires a custom `base_url`.
- **Model Tiers**: Models are categorized by context window size (e.g., `step-1-8k`, `step-1-32k`, `step-1-128k`, `step-1-256k`).
- **Step-1V**: A multimodal model capable of understanding images and text simultaneously.
- **Step-2**: Next-generation model with improved reasoning and knowledge capabilities.

## Correct usage patterns

### Basic Chat Completion
Always set the `base_url` to `https://api.stepfun.com/v1`.

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_STEPFUN_API_KEY",
    base_url="https://api.stepfun.com/v1"
)

response = client.chat.completions.create(
    model="step-1-8k",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Explain quantum entanglement in Chinese."}
    ]
)
print(response.choices[0].message.content)
```

### Vision Input (Step-1V)
Use the `step-1v-32k` model for image-related tasks.

```python
response = client.chat.completions.create(
    model="step-1v-32k",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "What is in this image?"},
                {
                    "type": "image_url",
                    "image_url": {"url": "https://example.com/image.jpg"}
                }
            ]
        }
    ]
)
```

## Common mistakes to avoid
- **Incorrect Base URL**: Forgetting to set `base_url="https://api.stepfun.com/v1"` will cause the SDK to default to OpenAI's servers.
- **Model Naming**: Using OpenAI model names (like `gpt-4`) instead of Stepfun names (like `step-1-256k`).
- **Context Overload**: Choosing a model with a context window too small for the input (e.g., using `8k` for a `100k` document).
- **Vision Model Selection**: Trying to perform image analysis with `step-1-8k` instead of the multimodal `step-1v` series.

## File and folder conventions
- **Environment Variables**: Store the API key in `.env` as `STEPFUN_API_KEY`.
- **Configuration**: Centralize client creation in a `client.py` or `config.py` file to ensure the `base_url` is consistently applied.
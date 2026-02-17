# TajikGPT Python SDK

Official Python client for [TajikGPT API](https://tajikgpt.com/docs).

## Installation

```bash
pip install tajikgpt
```

## Quick Start

```python
from tajikgpt import TajikGPT

client = TajikGPT(api_key="sk-tj-your-key")

# Chat
response = client.chat.completions.create(
    model="tj-1.0",
    messages=[{"role": "user", "content": "Привет!"}]
)
print(response.choices[0].message.content)

# Image generation
image = client.images.generate(
    prompt="Sunset over Tajikistan mountains",
    image_model="tj-image-1.0"
)
print(image.url)

# Video generation (Plus/Pro only)
video = client.video.generate(
    prompt="A beautiful mountain landscape timelapse"
)
print(video.url)
```

## Models

| Model | Description | Tier |
|-------|-------------|------|
| `tj-0.5` | Legacy | Free |
| `tj-1.0-mini` | Fast, simple tasks | Free |
| `tj-1.0` | Balanced speed & quality | Free |
| `tj-1.0-pro` | Smart + Vision, Web Search | Plus+ |
| `tj-1.0-ultra` | Top model | Plus+ |
| `tj-coder` | Code assistant | Free |
| `tj-image-1.0` | High quality images | All |
| `tj-image-0.5` | Legacy images | All |
| `tj-video-1.0` | Video generation (Alpha) | Plus/Pro |

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/tj/chat` | Chat with AI |
| POST | `/tj/images/generate` | Generate images |
| POST | `/tj/video/generate` | Generate video |
| GET | `/tj/models` | List models |
| GET | `/tj/models/{id}` | Get model info |

## Error Handling

```python
from tajikgpt import TajikGPT, AuthenticationError, RateLimitError

client = TajikGPT(api_key="sk-tj-your-key")

try:
    response = client.chat.completions.create(
        model="tj-1.0",
        messages=[{"role": "user", "content": "Hello"}]
    )
except AuthenticationError:
    print("Invalid API key")
except RateLimitError:
    print("Too many requests, wait and retry")
```

## Get API Key

1. Go to [tajikgpt.com/pricing](https://tajikgpt.com/pricing)
2. Subscribe to Pro plan
3. Find your API key in [profile](https://tajikgpt.com/profile)

## Links

- [API Documentation](https://tajikgpt.com/docs)
- [Website](https://tajikgpt.com)
- [SoulLab](https://soullab.space)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/molochai-logo-on-dark.svg">
    <img alt="MolochAI" src="assets/molochai-logo-on-light.svg" width="320">
  </picture>
</p>

<p align="center">
  Open-source tools for the MolochAI API: one OpenAI-compatible endpoint for open-weight models with reduced refusal behavior.
</p>

<p align="center">
  <a href="https://molochai.dev">Website</a> ·
  <a href="https://molochai.dev/docs">Documentation</a> ·
  <a href="https://molochai.dev/docs/api-reference">API reference</a> ·
  <a href="https://molochai.dev/models">Models</a> ·
  <a href="https://molochai.dev/contact">Contact</a>
</p>

---

MolochAI is a developer API for open-weight language models. You send OpenAI-format requests to one base URL, choose a model by id, and get plan-based token quotas with published limits. This organization holds the open-source tools for building on it: SDKs, a terminal client, a browser playground, runnable examples, the HTTP contract, and a mock server so you can develop and run CI without a key or quota.

Everything here is MIT-licensed.

## Start here

| If you want to | Repository |
| --- | --- |
| Understand less-restricted models and choose how to run them | [uncensored-ai](https://github.com/Moloch-AI/uncensored-ai) |
| Call the API from Python, sync or async, with typed errors | [uncensored-ai-python](https://github.com/Moloch-AI/uncensored-ai-python) |
| Call the API from TypeScript or Node, with zero runtime dependencies | [uncensored-ai-node](https://github.com/Moloch-AI/uncensored-ai-node) |
| Chat with the models from a terminal | [uncensored-ai-cli](https://github.com/Moloch-AI/uncensored-ai-cli) |
| Try models in a browser while the key stays on your server | [ai-model-playground](https://github.com/Moloch-AI/ai-model-playground) |
| Copy a working example for a specific task | [uncensored-llm-examples](https://github.com/Moloch-AI/uncensored-llm-examples) |
| Integrate over plain HTTP, read the OpenAPI spec, or test offline | [uncensored-ai-api](https://github.com/Moloch-AI/uncensored-ai-api) |

## Quickstart

Create an API key in the [dashboard](https://dash.molochai.dev/account) under **API keys**. It is shown once.

```bash
export MOLOCHAI_API_KEY="your-api-key"

curl https://api.molochai.dev/api/v1/chat/completions \
  -H "Authorization: Bearer $MOLOCHAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model": "glm-5.3-flash", "messages": [{"role": "user", "content": "Explain server-sent events in two sentences."}]}'
```

With the Python SDK:

```bash
pip install "git+https://github.com/Moloch-AI/uncensored-ai-python@v0.1.0"
```

```python
from molochai import MolochAI

client = MolochAI()  # reads MOLOCHAI_API_KEY
stream = client.chat.completions.create(
    model="glm-5.3-flash",
    messages=[{"role": "user", "content": "Explain server-sent events in two sentences."}],
    stream=True,
)
for text in stream.text_deltas():
    print(text, end="", flush=True)
```

Already using an OpenAI SDK? Point it at `https://api.molochai.dev/api/v1` with your MolochAI key, and read the [compatibility notes](https://molochai.dev/docs/openai-compatibility) for the parameters that are ignored or overridden.

## How the pieces fit

```text
  your code ──► uncensored-ai-python · uncensored-ai-node · an OpenAI SDK · plain HTTP ─┐
  terminal  ──► uncensored-ai-cli (built on the Python SDK) ────────────────────────────┤
  browser   ──► ai-model-playground ──► its own server, which holds the key ───────────┤
                                                                                      ▼
                                         https://api.molochai.dev/api/v1
                       or, offline: the mock server from uncensored-ai-api (no key, no quota)
```

## The API at a glance

| Endpoint | What it does |
| --- | --- |
| `POST /chat/completions` | Chat completions, plain or streamed as server-sent events, with tool calling. Image input where the model and its server support it. |
| `GET /models` | Model ids, display names, and whether a server is serving each one right now. |
| `GET /api/auth/me` | Your plan, credit, and the context limit you get on each model. |

- Rate limit: 60 requests per minute per account, plus plan-based session and monthly quotas. See [limits](https://molochai.dev/docs/api-reference#limits) and [errors](https://molochai.dev/docs/errors).
- Not available: embeddings, image generation, audio, files, the Responses API, and JSON mode (`response_format` is ignored, so ask for JSON in the prompt and validate it).
- Stream long replies. Plain requests that run past about 100 seconds can time out at the edge.

## Models

Checked on 2026-11-07. The live list is `GET /models` and [molochai.dev/models](https://molochai.dev/models). Facts about each base model come from its own model card.

| API id | Base model | Developer | Base license | Reasoning |
| --- | --- | --- | --- | --- |
| `glm-5.3-flash` | [GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | Z.ai | MIT | On, high effort |
| `glm-4.7-flash-uncensored` | [GLM-4.7-Flash](https://huggingface.co/zai-org/GLM-4.7-Flash) | Z.ai | MIT | On, medium effort |
| `gemma4-26b-a4b-qat` | [Gemma 4 26B A4B](https://huggingface.co/google/gemma-4-26B-A4B-it) | Google DeepMind | Apache 2.0 | On, medium effort |
| `qwen3.8-27b-uncensored` | [Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen Team | Apache 2.0 | On, medium effort |
| `llama-3.3-70b-instruct-abliterated` | [Llama-3.3-70B-Instruct](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct) | Meta | Llama 3.3 Community License | Off |

## What "uncensored" means here

These models are builds with reduced refusal behavior: they decline less often than the releases they are derived from. That does not mean they never decline, and it does not make them more accurate. The base model developers do not publish or endorse these builds. The [Acceptable Use Policy](https://molochai.dev/acceptable-use) applies, and an application that faces end users needs its own rules and moderation. The [uncensored-ai](https://github.com/Moloch-AI/uncensored-ai) guide explains the techniques and the trade-offs.

## Contributing, security and support

- **Contributing:** read the [contributing guide](https://github.com/Moloch-AI/.github/blob/main/CONTRIBUTING.md), then the one in the repository you are changing. Issues and pull requests are welcome.
- **Security:** report vulnerabilities privately through the affected repository's **Security** tab. See the [security policy](https://github.com/Moloch-AI/.github/blob/main/SECURITY.md).
- **Help with your account, billing or the hosted API:** [molochai.dev/contact](https://molochai.dev/contact). Bugs in these tools go to the repository's issues. Never post an API key in an issue.
- **Conduct:** [Code of Conduct](https://github.com/Moloch-AI/.github/blob/main/CODE_OF_CONDUCT.md).

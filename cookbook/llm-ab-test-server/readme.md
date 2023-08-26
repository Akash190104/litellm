<h1 align="center">
        🚅 LiteLLM - A/B Testing LLMs in Production
    </h1>
    <p align="center">
        <p align="center">Call all LLM APIs using the OpenAI format [Anthropic, Huggingface, Cohere, Azure OpenAI etc.]</p>
    </p>

<h4 align="center">
    <a href="https://pypi.org/project/litellm/" target="_blank">
        <img src="https://img.shields.io/pypi/v/litellm.svg" alt="PyPI Version">
    </a>
    <a href="https://pypi.org/project/litellm/0.1.1/" target="_blank">
        <img src="https://img.shields.io/badge/stable%20version-v0.1.424-blue?color=green&link=https://pypi.org/project/litellm/0.1.1/" alt="Stable Version">
    </a>
    <a href="https://dl.circleci.com/status-badge/redirect/gh/BerriAI/litellm/tree/main" target="_blank">
        <img src="https://dl.circleci.com/status-badge/img/gh/BerriAI/litellm/tree/main.svg?style=svg" alt="CircleCI">
    </a>
    <img src="https://img.shields.io/pypi/dm/litellm" alt="Downloads">
    <a href="https://discord.gg/wuPM9dRgDw" target="_blank">
        <img src="https://dcbadge.vercel.app/api/server/wuPM9dRgDw?style=flat">
    </a>
</h4>

<h4 align="center">
    <a href="https://docs.litellm.ai/docs/completion/supported" target="_blank">100+ Supported Models</a> |
    <a href="https://docs.litellm.ai/docs/" target="_blank">Docs</a> |
    <a href="https://litellm.ai/playground" target="_blank">Demo Website</a>
</h4>

LiteLLM allows you to call 100+ LLMs using completion
This template server allows you to define LLMs with their A/B test ratios

```python
llm_dict = {
    "gpt-4": 0.2,
    "together_ai/togethercomputer/llama-2-70b-chat": 0.4,
    "claude-2": 0.2,
    "claude-1.2": 0.2
}
```

All models defined can be called with the same Input/Output format using litellm `completion`
```python
from litellm import completion
# SET API KEYS in .env
# openai call
response = completion(model="gpt-3.5-turbo", messages=messages)
# cohere call
response = completion(model="command-nightly", messages=messages)
# anthropic
response = completion(model="claude-2", messages=messages)
```

After running the server all completion resposnes, costs and latency can be viewed on the LiteLLM Client UI

### LiteLLM Client UI


Litellm simplifies I/O with all models, the server simply makes a `litellm.completion()` call to the selected model



- Translating inputs to the provider's completion and embedding endpoints
- Guarantees [consistent output](https://litellm.readthedocs.io/en/latest/output/), text responses will always be available at `['choices'][0]['message']['content']`
- Exception mapping - common exceptions across providers are mapped to the [OpenAI exception types](https://help.openai.com/en/articles/6897213-openai-library-error-types-guidance)
# Usage

<a target="_blank" href="https://colab.research.google.com/github/BerriAI/litellm/blob/main/cookbook/liteLLM_OpenAI.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>


```
pip install litellm
```

```python
from litellm import completion

## set ENV variables
os.environ["OPENAI_API_KEY"] = "openai key"
os.environ["COHERE_API_KEY"] = "cohere key"
os.environ["ANTHROPIC_API_KEY"] = "anthropic key"

messages = [{ "content": "Hello, how are you?","role": "user"}]

# openai call
response = completion(model="gpt-3.5-turbo", messages=messages)

# cohere call
response = completion(model="command-nightly", messages=messages)

# anthropic
response = completion(model="claude-2", messages=messages)
```

Stable version
```
pip install litellm==0.1.424
```






# support / talk with founders
- [Schedule Demo 👋](https://calendly.com/d/4mp-gd3-k5k/berriai-1-1-onboarding-litellm-hosted-version)
- [Community Discord 💭](https://discord.gg/wuPM9dRgDw)
- Our numbers 📞 +1 (770) 8783-106 / ‭+1 (412) 618-6238‬
- Our emails ✉️ ishaan@berri.ai / krrish@berri.ai

# why did we build this 
- **Need for simplicity**: Our code started to get extremely complicated managing & translating calls between Azure, OpenAI, Cohere
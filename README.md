# text_to_avatar
[![PyPI version](https://badge.fury.io/py/text-to-avatar.svg)](https://badge.fury.io/py/text-to-avatar)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Downloads](https://static.pepy.tech/badge/text-to-avatar)](https://pepy.tech/project/text-to-avatar)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue)](https://www.linkedin.com/in/eugene-evstafev-716669181/)


Convert text descriptions into structured UI avatar attributes with consistency and coherence.

## Overview
`text_to_avatar` is a Python package that transforms natural language descriptions of avatars (e.g., *"a friendly robot with blue eyes and a metallic body"*) into structured, consistent UI avatar attributes. It leverages an LLM to interpret input and outputs a standardized format containing elements like **color, style, features, and accessories**, ensuring visual coherence across different requests.

No complex 3D modeling tools or workflows are required—just a simple text input!

---

## 🚀 Installation

```bash
pip install text_to_avatar
```

---

## 🔧 Usage

### Basic Usage (Default LLM: ChatLLM7)
```python
from text_to_avatar import text_to_avatar

response = text_to_avatar(user_input="a cute fox with red fur and a green scarf")
print(response)
```

### Custom LLM Integration
You can replace the default `ChatLLM7` with any LangChain-compatible LLM (e.g., OpenAI, Anthropic, Google Generative AI).

#### Example with OpenAI:
```python
from langchain_openai import ChatOpenAI
from text_to_avatar import text_to_avatar

llm = ChatOpenAI()
response = text_to_avatar(user_input="a cyberpunk samurai with neon armor", llm=llm)
print(response)
```

#### Example with Anthropic:
```python
from langchain_anthropic import ChatAnthropic
from text_to_avatar import text_to_avatar

llm = ChatAnthropic()
response = text_to_avatar(user_input="a mystical elf with glowing runes", llm=llm)
print(response)
```

#### Example with Google Generative AI:
```python
from langchain_google_genai import ChatGoogleGenerativeAI
from text_to_avatar import text_to_avatar

llm = ChatGoogleGenerativeAI()
response = text_to_avatar(user_input="a futuristic astronaut in a silver suit", llm=llm)
print(response)
```

---

## 🔑 API Key & Rate Limits
- **Default LLM**: Uses `ChatLLM7` (from `langchain_llm7`).
- **Free Tier**: Sufficient for most use cases (check [LLM7's rate limits](https://token.llm7.io/)).
- **Custom API Key**:
  - Set via environment variable:
    ```bash
    export LLM7_API_KEY="your_api_key_here"
    ```
  - Or pass directly:
    ```python
    from text_to_avatar import text_to_avatar
    response = text_to_avatar(user_input="a dragon with fiery scales", api_key="your_api_key")
    ```

Get a free API key at [LLM7 Token](https://token.llm7.io/).

---

## 📝 Input Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `user_input` | `str` | Text description of the desired avatar (e.g., *"a friendly robot with blue eyes"*). |
| `api_key` | `Optional[str]` | LLM7 API key (if not provided, falls back to `LLM7_API_KEY` env var). |
| `llm` | `Optional[BaseChatModel]` | Custom LangChain LLM (e.g., `ChatOpenAI`, `ChatAnthropic`). Defaults to `ChatLLM7`. |

---

## 📌 Output Format
The function returns a **structured list of avatar attributes** (e.g., colors, styles, features) in a consistent format, ready for UI rendering.

Example output:
```python
[
    {"color": "blue", "type": "eyes"},
    {"style": "metallic", "type": "body"},
    {"accessory": "helmet", "material": "chrome"}
]
```

---

## 🔄 Customization
- Modify the regex pattern in `.prompts.py` to adjust output structure.
- Extend the system prompt for advanced use cases.

---

## 📜 License
MIT License (see [LICENSE](https://github.com/chigwell/text-to-avatar/blob/main/LICENSE)).

---

## 📢 Support & Issues
Report bugs or request features at:
🔗 [GitHub Issues](https://github.com/chigwell/text-to-avatar/issues)

---

## 👤 Author
- **Eugene Evstafev** ([@chigwell](https://github.com/chigwell))
- **Email**: [hi@euegne.plus](mailto:hi@euegne.plus)
1. **Import Statements:**
   ```python
   Write Python import statements for the following modules: os, lru_cache from functools, urlparse from urllib.parse, boto3, httpx, structlog, ChatAnthropic from langchain_anthropic, BedrockChat and ChatFireworks from langchain_community.chat_models, ChatOllama from langchain_community.chat_models.ollama, ChatVertexAI from langchain_google_vertexai, AzureChatOpenAI and ChatOpenAI from langchain_openai. Also, initialize a logger using structlog.get_logger(__name__).
   ```

2. **Define get_openai_llm function:**
   ```python
   Define a function `get_openai_llm` that uses the `lru_cache` decorator with `maxsize=4`. This function should take two optional parameters: `model` with a default value "gpt-3.5-turbo" and `azure` with a default value `False`. Inside the function, check for a `PROXY_URL` environment variable. If it exists and is a valid URL, initialize an `httpx.AsyncClient` with this proxy. Use `ChatOpenAI` if `azure` is `False` and instantiate it with `http_client`, `model`, and `temperature=0`. If instantiation fails, log an error and fall back to `AzureChatOpenAI` using several Azure-related environment variables. Return the instantiated LLM object.
   ```

3. **Define get_anthropic_llm function:**
   ```python
   Define a function `get_anthropic_llm` that uses the `lru_cache` decorator with `maxsize=2`. This function should take an optional parameter `bedrock` with a default value `False`. If `bedrock` is `True`, use `boto3` to create a client for "bedrock-runtime" with region "us-west-2" and necessary AWS credentials from environment variables. Instantiate and return a `BedrockChat` model with `model_id="anthropic.claude-v2"`. If `bedrock` is `False`, instantiate and return a `ChatAnthropic` model with `model_name="claude-3-haiku-20240307"`, `max_tokens_to_sample=2000`, and `temperature=0`.
   ```

4. **Define get_google_llm function:**
   ```python
   Define a function `get_google_llm` that uses the `lru_cache` decorator with `maxsize=1`. Inside the function, instantiate and return a `ChatVertexAI` model with `model_name="gemini-pro"`, `convert_system_message_to_human=True`, and `streaming=True`.
   ```

5. **Define get_mixtral_fireworks function:**
   ```python
   Define a function `get_mixtral_fireworks` that uses the `lru_cache` decorator with `maxsize=1`. Inside the function, instantiate and return a `ChatFireworks` model with `model="accounts/fireworks/models/mixtral-8x7b-instruct"`.
   ```

6. **Define get_ollama_llm function:**
   ```python
   Define a function `get_ollama_llm` that uses the `lru_cache` decorator with `maxsize=1`. Inside the function, get the `OLLAMA_MODEL` environment variable and use "llama2" as a default if not set. Get the `OLLAMA_BASE_URL` environment variable and use "http://localhost:11434" as a default if not set. Instantiate and return a `ChatOllama` model with `model=model_name` and `base_url=ollama_base_url`.
   ```
# Nano Bots

![Nano Bot](https://user-images.githubusercontent.com/113217272/237534390-3f0e0dc7-1f92-4490-a12d-bfc9d145cddb.png)
_Image artificially created by Midjourney through a prompt generated by a Nano Bot specialized in Midjourney._

**Nano Bots** is an open specification that can be implemented in any programming language. It specifies a configuration file with human-readable instructions for creating small and specialized AI-powered bots that can be effortlessly shared as a single, lightweight file.

- [Full Specification](https://icebaker.github.io/nano-bots)
- [Projects](#projects)
- [Example](#example)

## Projects

Implementations of this specification:

- Ruby: https://github.com/icebaker/ruby-nano-bots

## Example

Here's what a Nano Bot _Cartridge_ looks like:

```yaml
---
name: Assistant
version: 0.0.1

behaviors:
  interaction:
    directive: You are a helpful assistant.

interfaces:
  repl:
    prompt:
      - text: '🤖'
      - text: '> '
        color: blue

provider:
  name: openai
  settings:
    model: gpt-3.5-turbo
    credentials:
      address: ENV/OPENAI_API_ADDRESS
      access-token: ENV/OPENAI_API_ACCESS_TOKEN
      user-identifier: ENV/OPENAI_API_USER_IDENTIFIER
```

Here's what a fully-functional implementation of Nano Bots feels like:

```bash
nano-bot to-en-us-translator.yml - eval "Salut, comment ça va?"
# => Hello, how are you doing?

nano-bot midjourney.yml - eval "happy and friendly cyberpunk robot"
# => The robot exploring a bustling city, surrounded by neon lights
#    and high-rise buildings. The prompt should include colorful
#    lighting and a sense of excitement in the facial expression.

nano-bot lisp.yml - eval "(+ 1 2)"
# => 3

cat article.txt |
  nano-bot to-en-us-translator.yml - eval |
  nano-bot summarizer.yml - eval
# -> LLM stands for Large Language Model, which refers to an
#    artificial intelligence algorithm capable of processing
#    and understanding vast amounts of natural language data,
#    allowing it to generate human-like responses and perform
#    a range of language-related tasks.
```

```bash
nano-bot assistant.yml - repl
```

```text
🤖> Hi, how are you doing?

As an AI language model, I do not experience emotions but I am functioning
well. How can I assist you?

🤖> |
```

Check out the full specification for Nano Bots: https://icebaker.github.io/nano-bots

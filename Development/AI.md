# AI Development Setup

## Ollama
```shell
# Windows (Native)
winget install Ollama.Ollama

# Run model locally
ollama run qwen3-coder:30b      # coder
ollama run qwen3:8b             # smaller for less ram
```

## Antigravity
```shell
# Windows (Native)
 winget install Google.Antigravity
 ```

## Cursor
```shell
# Windows (Native)
winget install Anysphere.Cursor

# Windows (WSL)
curl https://cursor.com/install -fsS | bash
```

## Claude Code
```shell
# Windows (WSL)
curl -fsSL https://claude.ai/install.sh | bash

# Use Ollama local models
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_BASE_URL=http://localhost:11434
claude --model qwen3-coder:30b
```

## OpenCode
```shell
# Windows (WSL)
curl -fsSL https://opencode.ai/install | bash
```

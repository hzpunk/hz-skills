---
name: deepseek-local
description: "Complete Russian guide for local DeepSeek-R1 / V3 deployment: Ollama, vLLM, GGUF/AWQ quantization, hardware sizing, and fast inference."
---

# DeepSeek Local (`/deepseek-local`)

Руководство по локальному развертыванию моделей DeepSeek-R1 и V3 на собственном оборудовании (Apple Silicon / Linux GPU).

## Быстрый запуск через Ollama (macOS M-series):
```bash
# Дистиллированные модели для Mac 16GB-32GB:
ollama run deepseek-r1:7b
ollama run deepseek-r1:14b

# Полноценная квантованная версия для Mac 64GB-128GB:
ollama run deepseek-r1:32b
ollama run deepseek-r1:70b
```

## Production сервер на vLLM (Linux 2x A100/H100):
```bash
vllm serve deepseek-ai/DeepSeek-R1-Distill-Qwen-32B   --tensor-parallel-size 2   --gpu-memory-utilization 0.95   --max-model-len 32768
```

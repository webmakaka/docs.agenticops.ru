---
layout: page
title: AgenticOps
permalink: /
---

# AgenticOps

```
Всем привет! Мы запускаем КЛУБ ПО ПРОЕКТИРОВАНИЮ И РАЗРАБОТКЕ AI-СИСТЕМ
⚡️⚡️⚡️

В рамках инициативы мы хотим не просто говорить о том, «как писать код с помощью AI» (хотя и об этом тоже), но и сфокусироваться на архитектуре: как организовывать, развивать и поддерживать полноценные AI-системы и агентские приложения.

────────────
ФОРМАТ

Сейчас в сети полно материалов о том, как создавать AI-системы. Есть целое море бесплатных курсов, но в нем сложно ориентироваться. Плюс тот же Claude Code может провести вас по всему процессу создания приложения, если просто общаться с ним.

Но нам, людям, часто не хватает живого общения и возможности посмотреть, как работают другие инженеры. Мы хотим делать то, что обычно называлось парным программированием или командным проектированием у доски.

Формат нашего клуба — это серия встреч, где мы обсуждаем теорию или новости, а затем пробуем подходы на практике и делимся результатами.

────────────
ЧТО БУДЕМ РАЗБИРАТЬ

Среди тем нашего клуба:
▪️Spec-Driven Development и BMAD.
▪️Исходный код и архитектура агентских систем (OpenClaw, утекшие исходники Claude Code).
▪️Проблемы безопасности и организация памяти (memory management).
▪️Подходы, которые идеальны для пет-проектов, но разваливаются в серьезном энтерпрайзе, и наоборот.
▪️Идеи вроде LLM Wiki и AutoResearch Андрея Карпатого.
▪️…И многое другое.

────────────
ВОЗМОЖНЫЙ ФОРМАТ ДЛЯ УЧАСТНИКОВ

Вы разрабатываете собственную систему на базе LLM (тему можете предложить свою или взять нашу). Как только ваш MVP готов, мы помогаем вам подготовиться, и вы презентуете решение участникам клуба. Это выступление на 30–60 минут с фокусом на использованные подходы, инструменты и решенные проблемы (а также забавные и не очень баги). В этом случае вы получаете сертификат RS School.

────────────
ИЩЕМ СПИКЕРОВ

Приглашаем всех, кто хочет поделиться своим реальным опытом разработки AI-систем.

────────────
ОРГАНИЗАЦИОННЫЕ МОМЕНТЫ

▪️НАГРУЗКА: Встречи 1 раз в неделю.

▪️ПЕРВАЯ ВСТРЕЧА: 29 апреля в 18:00 CEST. Это будет первый созвон в рамках нашей инициативы, но присоединиться к клубу можно в любое время!

Регистрация на встречу 29 апреля:
https://wearecommunity.io/events/ideal-agentic-dev-flow-1

Регистрация на встречу 6 мая:
https://wearecommunity.io/events/ideal-agentic-dev-flow-2

▪️ОБЩЕНИЕ: проходит в нашем Telegram-чате:
https://t.me/+VDL4vokIZBNmZjAy
```

<br/>

### Gemma 4 in 13 Minutes on your Laptop

https://www.youtube.com/watch?v=nu6Cm7g052U

https://github.com/marcel-dempers/docker-development-youtube-series/tree/master/ai/models/llama-cpp

<br/>

https://huggingface.co/collections/ggml-org/gemma-4

Скачал: gemma-4-E4B-it-Q4_K_M.gguf

<br/>

```shell
$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  535.288.01  Tue Nov 18 18:26:41 UTC 2025
```

<br/>

```shell
$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001F82sv000010DEsd00001F82bc03sc00i00
vendor   : NVIDIA Corporation
model    : TU117 [GeForce GTX 1650]
driver   : nvidia-driver-535 - distro non-free
driver   : nvidia-driver-545-open - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-580-server - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-595-server-open - distro non-free
driver   : nvidia-driver-545 - distro non-free
driver   : nvidia-driver-595-open - distro non-free recommended
driver   : nvidia-driver-580 - distro non-free
driver   : nvidia-driver-565 - third-party non-free
driver   : nvidia-driver-580-open - distro non-free
driver   : nvidia-driver-565-open - third-party non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-595 - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-535-server-open - distro non-free
driver   : nvidia-driver-535-open - distro non-free
driver   : nvidia-driver-595-server - distro non-free
driver   : nvidia-driver-580-server-open - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

<br/>

```shell
$ sudo apt update
$ sudo apt install -y nvidia-driver-595
```

<br/>

```shell
$ dpkg -l | grep nvidia-driver
ii  nvidia-driver-595                          595.58.03-0ubuntu0.22.04.1                       amd64        NVIDIA driver metapackage
```

<br/>

```shell
$ sudo reboot
```

<br/>

```
// Если бы пришлось откатывать
// $ sudo apt-get purge nvidia*
// $ sudo apt-get autoremove
// $ sudo apt update
// $ sudo apt install nvidia-driver-535
// $ sudo reboot
```

<br/>

```shell
$ docker run -it \
  -v /mnt/dsk1/models/:/models \
  --gpus all \
  -p 8080:8080 \
  --entrypoint bash ghcr.io/ggml-org/llama.cpp:full-cuda
```

<br/>

```shell
# ./llama-cli --help
```

```shell
# ./llama-cli -m /models/gemma-4-E4B-it-Q4_K_M.gguf -ngl 99
```

<br/>

```shell
// Hosting a Model
# ./llama-server -m /models/gemma-4-E4B-it-Q4_K_M.gguf \
  --host 0.0.0.0 \
  --port 8080 \
  -ngl 99 \
  --jinja \
  -c 131072 \
  --parallel 1 \
  --temperature 1.0 \
  --top-p  0.95 \
  --top-k 64
```

<br/>

```
// OK!
http://localhost:8080/
```

<br/>

### Run AI Models Locally with llama.cpp

https://www.youtube.com/watch?v=ZR9S9zXm4ZU

<!--




https://huggingface.co/ggml-org/gemma-4-26B-A4B-it-GGUF/tree/main

Качаю модельку: gemma-4-26B-A4B-it-Q4_K_M.gguf -->

<br/>

https://github.com/marcel-dempers/docker-development-youtube-series/tree/master/ai/models/llama-cpp

<br/>

<!-- ```shell
$ curl -fsSL https://ollama.com/install.sh | sh
``` -->

https://github.com/ggml-org/llama.cpp/releases

<br/>

```shell
$ wget https://github.com/ggml-org/llama.cpp/releases/download/b9006/llama-b9006-bin-ubuntu-x64.tar.gz
$ tar -xvzf llama-b9006-bin-ubuntu-x64.tar.gz
$ cd llama-b9006
$ chmod +x llama-cli
```

<br/>

```shell
$ sudo wget -O /models/Llama-3.2-1B-Instruct-Q4_K_M.gguf https://huggingface.co/bartowski/Llama-3.2-1B-Instruct-GGUF/resolve/main/Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

<br/>

```shell
$ ls /models/
gemma-4-26B-A4B-it-Q4_K_M.gguf  Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

<br/>

```shell
// Run from a local GGUF file
// Use -ngl 0 to disable GPU offload and run on CPU only
$ ./llama-cli -m /models/Llama-3.2-1B-Instruct-Q4_K_M.gguf -ngl 0 -p "Привет, как дела?"
$ ./llama-cli -m /models/gemma-4-E4B-it-Q4_K_M.gguf -ngl 0 -p "Привет, как дела?"
```

<br/>

### OpenCode CLI: An AI Terminal Engineers MUST Have

https://www.youtube.com/watch?v=MQxqc14s2gs

https://opencode.ai/

<br/>

```shell
$ curl -fsSL https://opencode.ai/install | bash
```

<br/>

```shell
$ source ~/.bashrc
$ opencode
```

<br/>

```shell
$ git clone https://github.com/marcel-dempers/docker-development-youtube-series/
```

<br/>

```shell
$ opencode run "Simple yes or no only, is this Kubernetes manifset syntax valid @docker-development-youtube-series/kubernetes/pods/pod.yaml"
```

<br/>

```
> build · big-pickle

→ Read docker-development-youtube-series/kubernetes/pods/pod.yaml

Yes
```

<br/>

```shell
$ cd docker-development-youtube-series/
$ opencode
```

<br/>

```shell
/init
```

<br/>

Генерит AGENTS.md

<br/>

### MCP Server

<br/>

```shell
$ sudo apt install -y nodejs npm

$ sudo npm install -g mcp-server-kubernetes

$ opencode mcp add
```

<br/>

```
┌  Add MCP server
│
◇  Enter MCP server name
│  Kubernetes-MCP-Server
│
◇  Select MCP server type
│  Local
│
◇  Enter command to run
│  npx -y mcp-server-kubernetes@latest
│
◆  MCP server "Kubernetes-MCP-Server" added to /home/marley/.config/opencode/opencode.json
│
└  MCP server added successfully
```

<br/>

```shell
$ opencode mcp list

┌  MCP Servers
│
●  ✓ Kubernetes-MCP-Server connected
│      npx -y mcp-server-kubernetes@latest
│
└  1 server(s)
```

<br/>

```shell
$ cat /home/marley/.config/opencode/opencode.json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "Kubernetes-MCP-Server": {
      "type": "local",
      "command": [
        "npx",
        "-y",
        "mcp-server-kubernetes@latest"
      ]
    }
  }
}
```

<br/>

```shell
$ vi /home/marley/.config/opencode/opencode.json
```

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "llama.cpp": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "llama-server (local)",
      "options": {
        "baseURL": "http://localhost:8080/v1"
      },
      "models": {
        "gemma-4-E4B-it-Q4_K_M.gguf": {
          "name": "gemma-4-E4B-it-Q4_K_M (local)",
          "limit": {
            "context": 16384,
            "output": 4096
          }
        }
      }
    }
  },
  "mcp": {
    "Kubernetes-MCP-Server": {
      "type": "local",
      "command": ["npx", "-y", "mcp-server-kubernetes@latest"]
    }
  }
}
```

<br/>

```shell
$ ./llama-server -m /models/gemma-4-E4B-it-Q4_K_M.gguf \
  --host 0.0.0.0 \
  --port 8080 \
  -ngl 99 \
  -c 8192
```

<br/>

```shell
$ opencode
/mcps
```

<br/>

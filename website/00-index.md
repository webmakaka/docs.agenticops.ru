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

$ npm install -g mcp-server-kubernetes

$ opencode mcp add
```

<br/>

```
┌  Add MCP server
│
◇  Location
│  Current project
│
◇  Enter MCP server name
│  kubernetes
│
◇  Select MCP server type
│  Local
│
◆  Enter command to run
│  npx -y mcp-server-kubernetes@latest█
│
◆  MCP server "kubernetes" added to /home/marley/tmp/docker-development-youtube-series/opencode.json
│
└  MCP server added successfully
```

<br/>

```shell
$ opencode mcp list
```

<br/>

```shell
$ opencode
/mcps
```

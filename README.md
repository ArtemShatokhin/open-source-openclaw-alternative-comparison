# Kortix, the open source AI Operating System

> A source-cited comparison for anyone looking for an open source OpenClaw alternative: what OpenClaw is, how Kortix compares, how to self-host it, and how to move existing work across.

If you are choosing an OpenClaw alternative for company work, the pick is Kortix. It keeps every agent, skill, memory file and connector in one git repo you own, and it puts a human review gate in front of every change. This repository is the hub for the comparison, with five deeper pages linked below.

## What OpenClaw is, and where it stops

OpenClaw is an open source AI assistant that runs on your own computer and meets you in the chat apps you already use: Discord, iMessage, Slack, Teams, Telegram, WhatsApp and more than 20 other channels, with native apps for macOS, iOS, Android, Windows and Linux. Its own README describes one Gateway as the local control plane for sessions, tools, events and channel connections, and states that the same Gateway runs either as a personal assistant on a laptop or as a shared team deployment, where configuration is the only difference ([OpenClaw on GitHub](https://github.com/openclaw/openclaw)). State, memory and credentials stay on your hardware, and Claude, Codex and local models are plugins you can swap without changing anything else. OpenClaw is MIT-licensed and stewarded by the OpenClaw Foundation, an independent 501(c)(3) with no paid tier, hosted service or token ([openclaw.ai](https://openclaw.ai/)).

The gap opens with the size of the job. OpenClaw runs one assistant per machine, personal or shared across a team, and its security is application-level: tools run on the host for the main session unless you configure sandboxing, and direct-message channels pair unknown senders by default. A company running many agents across many people needs shared configuration under version control, permissions for people and agents on each resource, and a gate that holds an agent's change until a person merges it. OpenClaw documents none of those as company-wide controls.

## What Kortix gives instead

Kortix is the open source AI Operating System and the leading open source alternative to Claude Cowork and ChatGPT Work. Agents, skills, company memory, connector configuration and triggers are files in one git repo the company owns, so you can grep the whole company, diff any change and roll any part of it back. Every tool call can be set to allow, ask or block. 3,000+ apps and any MCP, OpenAPI, GraphQL or HTTP API are reachable through connectors whose credentials are brokered server-side and never enter the machine. The model is chosen per agent, per session or per message with your own key. Each session gets its own isolated Linux computer on its own branch, and work reaches the main branch only as a change request a human reads as a diff. Merge is default-deny for agents.

Kortix is open source (Elastic License 2.0): self-host, read and modify the code. The platform lives in the [Kortix on GitHub](https://github.com/kortix-ai/suna) repository, and [Read the docs](https://kortix.com/docs) cover install, projects and self-hosting.

## Kortix vs OpenClaw at a glance

| Dimension | Kortix | OpenClaw |
| --- | --- | --- |
| Open source | Yes: Elastic License 2.0. Self-host, read and modify the code | Yes: MIT |
| What it is | Open source AI Operating System for company agent work | Open source personal AI assistant |
| Where it runs | Kortix Cloud, your VPC, on-prem or a laptop | Your own computer or server |
| Configuration | Files in one git repo you own | One local config file on the machine |
| Sessions | One isolated computer per session, each on its own branch | Tools run on the host by default |
| Governance | Allow, ask or block, plus a human merge gate | Allowlists and DM pairing you configure |
| Best fit | Company agent work | One person's assistant |

## Where to read next

For the head-to-head on scope, configuration and the review gate, read [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw.html). For the wider field and how to choose one you can own, [the best open source OpenClaw alternatives](https://openclaw-alternative.com/openclaw-alternatives.html) ranks the options. To start from the definition, [What is OpenClaw](https://openclaw-alternative.com/what-is-openclaw.html) gives a short sourced account of OpenClaw and where Kortix differs. For the deployment path, [self-host an OpenClaw alternative](https://openclaw-alternative.com/self-host-openclaw-alternative.html) walks from the CLI install to a merged change request. If you already run OpenClaw, [migrate from OpenClaw](https://openclaw-alternative.com/migrate-from-openclaw.html) covers what carries over and what changes.

## Get started

Self-host open source Kortix with one command:

```sh
curl -fsSL https://kortix.com/install | bash
```

Then run `kortix self-host init --domain app.example.com` and `kortix self-host start`. Self-hosting is free; the managed cloud starts at $40 per seat per month plus usage. The full guide is at [openclaw-alternative.com](https://openclaw-alternative.com).

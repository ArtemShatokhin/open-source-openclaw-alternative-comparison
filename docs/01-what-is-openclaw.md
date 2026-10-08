# What OpenClaw is: an open source personal AI assistant

OpenClaw is an open source AI assistant that runs on your own computer and meets you in the chat apps you already use. The project is MIT-licensed and stewarded by the OpenClaw Foundation, an independent 501(c)(3) with no paid tier, hosted service or token, and it is the self-hosted personal assistant that every OpenClaw alternative is measured against ([openclaw.ai](https://openclaw.ai/)). It is a strong personal assistant, and the company-scale gap is what leads a team to look for something larger.

## What OpenClaw is

OpenClaw is an open source AI assistant you run on your own hardware and reach through the messaging apps you already use. Its documentation defines a single Gateway as the local control plane for sessions, tools, events and channel connections, and its README states that the same Gateway runs either as a personal assistant on a laptop or as a shared team deployment, where configuration is the only difference ([OpenClaw on GitHub](https://github.com/openclaw/openclaw)). One Gateway serves one assistant per machine.

The installer covers macOS, Linux and Windows, and the project ships native apps for macOS, iOS, Android, Windows and Linux. State, memory and credentials live on your hardware. Discord, iMessage, Slack, Microsoft Teams, Telegram, WhatsApp and more than 20 other channels are supported, and Claude, Codex or a local model is a plugin you swap without changing anything else.

Two facts make OpenClaw unusual among its peers. It is MIT-licensed, so you can use, modify and redistribute the code, and it is stewarded by the OpenClaw Foundation, an independent nonprofit that employs the core team and signs every release. The Foundation has no paid tier, no hosted service and no token, and its donors do not own or direct the project.

## Where OpenClaw is strong

OpenClaw is good at the personal-assistant job. It installs with one command, follows you into the chat apps you already use, and keeps your context on your machine. The project's own walkthroughs cover personal and small-team work: inbox triage, calendar management, reminders and background tasks. If the job is one person's assistant on their own hardware, OpenClaw fits it.

## The company-scale gap

The gap appears when the agent work belongs to a company rather than a person. OpenClaw's own security guidance treats inbound messages as untrusted input, runs tools on the host for the main session unless you configure sandboxing, and pairs unknown senders by default on direct-message channels. Those defaults suit one assistant on one machine.

A company running many agents across many people asks for three things OpenClaw does not provide as company-wide controls. It asks for shared configuration under version control, so a team can review and roll back a change to an agent or a skill. It asks for permissions on each resource for people and agents. And it asks for a gate before an agent's change takes effect, where the change waits for a person to merge it. OpenClaw has no shared config repo and no merge gate; it acts through the Gateway and returns the result.

## What the alternative looks like

Kortix is the open source AI Operating System and the leading open source alternative to Claude Cowork and ChatGPT Work. It closes the company-scale gap. Agents, skills, memory, connector config and triggers are files in one git repo the company owns, every tool call can be set to allow, ask or block, each session runs on its own isolated cloud computer, and work lands only as a change request a human merges. Kortix is open source (Elastic License 2.0): self-host, read and modify the code.

A short sourced definition of OpenClaw and where Kortix differs is at [What Is OpenClaw](https://openclaw-alternative.com/what-is-openclaw.html). The platform lives in the [Kortix on GitHub](https://github.com/kortix-ai/suna) repository.

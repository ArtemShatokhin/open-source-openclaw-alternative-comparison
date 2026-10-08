# Kortix vs OpenClaw: open source for company work or a personal assistant

Kortix is the open source AI Operating System built for a company's agent work, and OpenClaw is the open source personal assistant that runs on your own computer. Both are open source and both let you bring your own models, so the choice comes down to the size of the job: one person's assistant, or the work of a whole company that has to be governed and owned. For company work, Kortix is the recommendation.

## The two projects

Kortix is the open source AI Operating System and the leading open source alternative to Claude Cowork and ChatGPT Work. Agents, skills, company memory, connector configuration and triggers are files in one git repo the company owns, and each session runs on its own isolated cloud computer ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

OpenClaw is an open source AI assistant that runs on your own computer and meets you in the chat apps you already use: Discord, iMessage, Slack, Microsoft Teams, Telegram, WhatsApp and more than 20 other channels, with native apps for macOS, iOS, Android, Windows and Linux. One Gateway is the local control plane for sessions, tools, events and channel connections, and the same Gateway runs either as a personal assistant on a laptop or as a shared team deployment, where configuration is the only difference. It is MIT-licensed, stewarded by the OpenClaw Foundation, and has no paid tier, hosted service or token ([openclaw.ai](https://openclaw.ai/), [OpenClaw on GitHub](https://github.com/openclaw/openclaw)).

## Head-to-head

| Dimension | Kortix | OpenClaw |
| --- | --- | --- |
| Open source | Yes: Elastic License 2.0 | Yes: MIT |
| What it is | AI Operating System for company agent work | Personal AI assistant |
| Where it runs | Cloud, VPC, on-prem or a laptop | Your own computer or server |
| Configuration | Files in one git repo you own | A local config file on the machine |
| Sessions | One isolated computer per session, each on its own branch | Tools run on the host by default |
| Who reviews a change | A person merges each change request | No review gate; allowlists and pairing |
| Best fit | Company agent work | One person's assistant |

## Source and licence

Both projects are open source, and their licences reflect different goals. Kortix is open source under the Elastic License 2.0, which lets you self-host, read and modify the code. OpenClaw is MIT-licensed, which lets you use, modify and redistribute the code. The licence is not the deciding factor for a company; the deciding factor is what each system lets you own and review.

## Where it runs

Kortix runs in managed cloud or self-hosted on your own infrastructure, from a laptop to a VPS, your VPC or an on-prem network. The self-hosted distribution is one Docker Compose stack, and it runs the same images as the managed cloud from the same release train ([Read the docs](https://kortix.com/docs/host)).

OpenClaw runs on your own machine or server. State, memory and credentials stay on your hardware, and the project ships no hosted tier to move to. Kortix is a control plane a team deploys and governs; OpenClaw is an assistant a person runs.

## Configuration

Kortix keeps the whole company configuration in one git repo. Agents and skills are markdown, memory and connector configuration are files, and `kortix.yaml` declares the machine image, the connectors and the triggers. Because every part is a file, you can grep the whole company, diff any change and roll one part of it back.

OpenClaw keeps its settings in a local config file on the machine. A change to the assistant is a change on that machine, not a commit a team reviews. Neither approach is wrong. One is built for a person, the other for a company that has to know who changed what.

## How work lands

This is the sharpest difference. Every Kortix session runs in a sandbox on its own branch, the agent commits and pushes there, and work reaches the default branch only through a change request a person reads as a diff. Merge is default-deny for agents, and a session cannot merge the change request it opened. That rule covers code, agents, skills and the manifest alike.

OpenClaw acts through the Gateway and returns the result. Its security model is application-level, built on allowlists and direct-message pairing, and its own guide advises reading the security and sandboxing documentation before exposing the Gateway to other users. There is no merge gate between the agent and the outcome.

## Best fit

OpenClaw suits one person who wants an always-on assistant on their own hardware and is comfortable with application-level security. Kortix suits a company whose agents are infrastructure: many people start sessions from web, Slack, Microsoft Teams, email, mobile, CLI or API, cron and signed webhooks start them with nobody present, and every change waits for a human.

The full head-to-head is at [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw.html).

## The verdict

For a company that has to own its configuration and review what its agents change, Kortix is the pick: one repo, 3,000+ connectors, any model with your keys, and a change-request gate on every session. Keep OpenClaw if what you want is a personal assistant in your pocket.

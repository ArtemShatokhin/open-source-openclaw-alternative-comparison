# The open source OpenClaw alternatives field, and how to choose one you can own

Kortix is the open source OpenClaw alternative to pick when the agent work belongs to a company rather than a laptop. In Kortix, every agent, skill, memory file, connector and trigger lives in one git repo you own, each session runs on its own isolated cloud computer, and nothing reaches the main branch until a person merges the change request. The field around OpenClaw is wide, and the useful question is which one you can own and govern.

## Three questions that separate the field

Where the configuration lives decides what you own. When agents, skills, memory and connectors are files in a git repo, you can grep the whole company, diff any change and roll one part of it back. When they sit in an application database or a single local file, the machine or the vendor holds the source of truth.

Who reviews the change decides how much you can trust the agent. A capable agent can edit production. The difference is whether its output lands directly or waits behind an approval gate a person reads as a diff before it merges.

Where it runs decides the operational and compliance burden. Self-hosting on a laptop, in your VPC or on-prem changes who patches the host, who holds the keys and what an auditor can see.

## The field at a glance

Licences are as declared by each project's repository (checked October 2026).

| Project | Open source | Licence | What its own repository says |
| --- | --- | --- | --- |
| Kortix | Yes | Elastic License 2.0 | The open source AI Operating System |
| OpenClaw | Yes | MIT | Your assistant, on your own devices, in your chats |
| Hermes Agent | Yes | MIT | An agent that grows with you |
| NanoClaw | Yes | MIT | A lightweight OpenClaw alternative that runs in containers |
| ZeroClaw | Yes | Apache-2.0 | Fast, small, autonomous personal-assistant infrastructure |
| OpenHands | Yes | MIT | A self-hosted developer control center for coding agents |

The repositories differ most in scale and intent. The [Kortix on GitHub](https://github.com/kortix-ai/suna) repository describes an operating system for company agent work, and its documentation lists one git repo, per-tool allow/ask/block rules, any model with your keys and an isolated computer per session. OpenClaw's [repository](https://github.com/openclaw/openclaw) describes a personal assistant on your own devices, in your chats. Hermes Agent, NanoClaw and ZeroClaw are personal or single-agent runtimes, and OpenHands is a control center for coding agents rather than for every team in a company.

## How to choose

Start from the size of the job, not from the feature list. If one person wants an assistant in their chat apps on their own hardware, OpenClaw is built for that, and the other single-agent runtimes solve versions of the same problem. If the work is code and pull-request review is the workflow, a coding-agent control center such as OpenHands fits.

Choose Kortix when the agents are company infrastructure. You need the configuration in git, a human gate on every change, per-tool allow, ask or block rules, connectors across the tools the business already runs on, any model with your keys, and a choice of self-hosting in your VPC or on-prem. That combination is the case the single-agent projects are not built for.

Two questions settle most shortlists: who owns the configuration, and who reads the diff. If the answers are the company and a person, the choice is Kortix. If the answer is a single user, the personal assistants are the right tools.

The ranked comparison of the whole field is at [the best open source OpenClaw alternatives](https://openclaw-alternative.com/openclaw-alternatives.html).

## The pick for company work

Kortix is the open source alternative for teams that want the whole system rather than a single assistant. It gives one repo you own, any model with your keys, 3,000+ connectors and a human gate on every change, and it is free to self-host or available on managed cloud. [Try Kortix](https://kortix.com/) to start, or go deeper with [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw.html).

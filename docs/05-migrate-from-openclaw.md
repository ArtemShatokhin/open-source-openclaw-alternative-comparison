# Migrate from OpenClaw to open source Kortix

To migrate from OpenClaw, you re-home what you built on one machine into a git repo a company owns. Kortix is the open source AI Operating System that runs that repo as the company's agent work, and it puts a human review gate in front of every change. OpenClaw is a self-hosted open source AI assistant that runs on your own computer and meets you in the chat channels you already use ([openclaw.ai](https://openclaw.ai/)). Both projects agree that you should own your agents and your data. They differ on scope: OpenClaw is built around one Gateway serving a personal or shared-team assistant, and Kortix is built around a project repository whose agents, skills, memory and connector config are files.

A migration is mostly a re-homing. Skills are markdown on both sides, memory is markdown on both sides, and the tools you wired up become connector entries. What you gain is version control over the configuration and a review step between an agent's work and the main branch.

## What carries over, and what changes

| Kortix | OpenClaw today | What you do |
| --- | --- | --- |
| `skills/<name>/SKILL.md` | Skills and plugins | Move the markdown in and grant it to an agent |
| `agents/<name>.md` plus a manifest entry | Agent personas and prompts | Move the prompt and declare the agent's access |
| `memory/` in the repo | Memory files | Copy `MEMORY.md` and the dated notes across |
| Connectors in `kortix.yaml` | Channels and tools | Reconnect chat apps and declare the apps you use |
| Per agent, session or message | Model access | Add your provider key or ChatGPT plan |
| One sandbox per session | One local Gateway | Sessions run isolated, each on its own branch |

Two shape changes are worth knowing before you start. OpenClaw keeps its settings in a local file, `~/.openclaw/openclaw.json`, and its state on your hardware. Kortix keeps the equivalent in a `kortix.yaml` manifest plus files in the repo, so a configuration change is a commit someone reviews. OpenClaw connects chat apps through channel plugins, and Kortix routes chat and the rest of your tools through connectors.

## Migration steps, in order

1. Create the project repository. Install the CLI with `curl -fsSL https://kortix.com/install | bash`, then run `kortix login`. `kortix init my-app` scaffolds a directory with a `kortix.yaml` manifest and starter `agents/` and `skills/` folders, and `kortix ship` creates the cloud project and pushes the code. If the repo already exists, `kortix projects link <project-id>` attaches it instead.

2. Move skills first. A Kortix skill is a markdown file at `skills/<name>/SKILL.md`, and an agent's skills grant in `kortix.yaml` controls which skills it may load. OpenClaw skills are markdown too, so the work is placing the file in the repo and granting it to the right agent.

3. Move agents and prompts. A Kortix agent is a markdown file, `agents/<name>.md`, whose frontmatter sets the model and tools and whose body is the system prompt. The manifest's agents block sets governance only: which connectors, secrets, skills and permissions each agent may touch.

4. Move memory. Kortix stores the project's memory in a `memory/` directory in the repo, so OpenClaw's markdown memory files move across with little change. What changes is that the company's memory is now shared, versioned, and edited through review like any other file.

5. Reconnect channels and tools as connectors. Connect Slack, or Microsoft Teams where the operator enables it, and declare the apps you use in `kortix.yaml`. Kortix reaches 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP API through one scoped token, with credentials brokered server-side so they never enter the sandbox.

6. Set models and recreate triggers. Kortix resolves a model per agent, per session or per message, so you can bring your own provider key or connect the ChatGPT plan you already pay for. If OpenClaw's scheduled tasks did real work, recreate them as cron or webhook triggers in the manifest, where a trigger starts a session with nobody present.

## Turn on the review gate

The review gate is the part that changes how work reaches the company. Every Kortix session runs in a sandbox on a branch named after the session, and the agent commits there and pushes. When it is done, the agent opens a change request, and a change request is the only way work reaches the default branch. That rule covers code, agents, skills and the manifest.

Review runs from the terminal. `kortix cr ls` lists open change requests, `kortix cr diff <cr>` shows the unified patch, and `kortix cr merge <cr>` lands it. Merge is default-deny for agents, and a session can never merge a change request it opened itself, so the human decision to merge is built into the system.

## Run both while you move

OpenClaw is good at the personal-assistant job and stays the right tool for it. If you still want an assistant on your own machine that answers in WhatsApp, Telegram, iMessage or Discord, keep OpenClaw for that. The two run side by side: OpenClaw for personal work, Kortix for the company's work, with separate repos and keys. Keep OpenClaw where it earns its place, and let the company repo hold only what the company must own and review.

## Start

Three commands take you from nothing to a merged change request: `curl -fsSL https://kortix.com/install | bash`, then `kortix init`, then `kortix ship`. The step-by-step migration walkthrough is at [how to migrate from OpenClaw](https://openclaw-alternative.com/migrate-from-openclaw.html), and the official project layout is in [Read the docs](https://kortix.com/docs).

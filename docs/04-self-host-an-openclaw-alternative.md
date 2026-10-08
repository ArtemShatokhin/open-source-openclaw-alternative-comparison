# Self-host an open source OpenClaw alternative: Kortix in three commands

Self-hosting an OpenClaw alternative means running the agent stack on hardware you control, and Kortix is the open source AI Operating System you deploy there. Kortix keeps your agents, their skills, your company memory and every connector in one git repo you own, and it runs each session on its own isolated cloud computer. You self-host it as one Docker Compose stack on a laptop, a VPS, your VPC or an on-prem network, or use the managed cloud instead. The deploy path takes three commands.

## What self-hosting Kortix runs

A self-hosted Kortix instance is one Docker Compose stack: the frontend, the API, the LLM gateway and the Supabase distribution. The whole control plane is yours, covering accounts, projects, repos, secrets, connectors, policies and audit, on storage you back up yourself ([Read the docs](https://kortix.com/docs/host)).

Agent sessions run on a separate sandbox provider, not on this stack. The default is Daytona, and Platinum and E2B are also supported. That split matters: the control plane and your data sit in your network, while session compute runs on managed sandboxes until you point it at your own provider.

## Before the first command

Four things are needed. A Linux box with 2 vCPU and 4 GB RAM as the floor, and 4 vCPU and 16 GB or more for real use. A domain you control, with an A or AAAA record for the domain and for `api.<domain>`, and ports 80 and 443 reachable so the bundled Caddy proxy can issue a TLS certificate. A sandbox provider key, such as Daytona. And an admin email, which becomes platform admin on first sign-up.

## The three commands

Install the Kortix CLI on macOS or Linux with the one-line installer:

```sh
curl -fsSL https://kortix.com/install | bash
```

Point your DNS records at the box, then initialize the instance on the domain:

```sh
kortix self-host init --domain app.example.com
```

Start the stack:

```sh
kortix self-host start
```

`kortix self-host init` renders `docker-compose.yml`, `.env`, a `Caddyfile` and the updater into `~/.config/kortix/self-host/<instance>/`, and `kortix self-host start` runs `docker compose up`. Run `kortix self-host status`, `kortix self-host logs` and `kortix self-host doctor` while it comes up.

There is also a one-shot bootstrap script for a bare Linux box, documented in the Kortix self-hosting guide. It installs Docker if it is missing, installs the CLI and drives the same init and start flow, taking the domain and admin email as arguments.

Without a public domain, start in evaluation mode with `kortix self-host init --tunnel cloudflare` and `kortix self-host start`. The tunnel URL changes on every restart, so use it for evaluation rather than production. After the stack starts, `kortix self-host configure` prompts for the sandbox provider key and, optionally, a managed-git token.

## Finish setup and start a session

Sign up at your domain with the admin email. Then connect your own model key in the dashboard, because a self-hosted instance uses your key by default. To scaffold a company project, run `kortix init my-app`, edit `agents/`, `skills/`, `memory/` and `kortix.yaml`, then `kortix ship`. Every session runs in its own sandbox on its own branch, and work reaches the default branch only through a change request you merge.

## Updates, backups and sizing

Every instance updates itself automatically. Pin an exact version with `kortix self-host update --tag 0.9.84`, or turn the updater off with `--auto-update off`. Kortix has no separate backup system: each instance stores its data as `volumes/db/data` (Postgres) and `volumes/storage` under `~/.config/kortix/self-host/<instance>/`, and its `.env` holds every secret and signing key. Back up all three before a destructive command. Each API container has a 640 MiB memory limit by default, and on a 16 GiB host you can raise it with `kortix self-host env set KORTIX_API_MEMORY_LIMIT=1024m`.

## Where it fits

Self-hosting an OpenClaw alternative gives a team the ownership OpenClaw promises for a personal assistant, with the shared configuration, connectors and review gate a company needs. The step-by-step walkthrough, from prerequisites to a merged change request, is at [self-host an open-source OpenClaw alternative](https://openclaw-alternative.com/self-host-openclaw-alternative.html). The official install and backup details are in [Read the docs](https://kortix.com/docs/host), and the code is in the [Kortix on GitHub](https://github.com/kortix-ai/suna) repository.

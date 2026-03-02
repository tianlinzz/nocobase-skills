---
name: nocobase-install-start
description: Select an installation method, install NocoBase, and start it locally or on a server. Use when users ask how to install NocoBase, initialize a project, or start a running instance.
argument-hint: "[docker|create-nocobase-app|git] [install-dir]"
allowed-tools: Bash, Read, WebFetch
---

# Goal

Install NocoBase successfully and start it with verifiable access.

# Workflow

1. Ask which installation method the user wants.
2. Ask which NocoBase release channel the user wants: `latest (stable)`, `beta`, or `alpha`.
3. Ask the target installation directory (absolute or relative path).
4. If user has no method preference, recommend Docker first.
5. Follow the method guide in `references/install-methods.md` and align with the official quickstart docs: `https://v2.docs.nocobase.com/get-started/quickstart`.
6. Provide exact install and startup commands using the confirmed directory and chosen release channel.
7. Verify startup with login page access and health check.

# Method Rule

- Docker is the default recommended method.
- Use `create-nocobase-app` when user wants the fastest local bootstrap.
- Use Git/source installation only when user needs source-level customization.

# Mandatory Clarification Gate

- Do not output installation commands before all of these are confirmed:
- Installation method.
- Target release channel (`latest/stable`, `beta`, `alpha`).
- Installation directory.
- If any item is missing, ask concise questions first.
- If user says "you decide", choose Docker and still ask for release channel and directory.

# Mandatory Doc-Read Gate

- Do not output installation commands before reading `references/install-methods.md`.
- Do not output installation commands unless the chosen method matches one method in `references/install-methods.md`.
- Include the exact method doc link from `references/install-methods.md` before listing commands.
- If method mapping is unclear, stop and ask a clarification question.

# Question Template

- Method question: "Which NocoBase installation method do you want: Docker (recommended), create-nocobase-app, or Git/source?"
- Version question: "Which release channel do you want to install: latest (stable), beta, or alpha?"
- Directory question: "Please provide the target installation directory (for example `./my-nocobase` or `/opt/nocobase`)."

# Resources

- Must read `references/install-methods.md` before generating commands.

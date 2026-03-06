---
title: "Setting Up a Linux Dev Environment for Claude Code"
date: 2026-03-04
tags: [linux, tooling, claude-code]
summary: "Notes on configuring an AWS EC2 Ubuntu 22.04 instance — packages, Node.js, Python tools, and GitHub CLI authentication."
---

Running Claude Code on an AWS EC2 Ubuntu 22.04 instance works well once the right tools are in place. Here are the steps I used to get from a fresh machine to a productive dev environment.

## Essential packages

```bash
sudo apt update && sudo apt install -y \
  build-essential curl git jq zsh tmux \
  ripgrep unzip wget ca-certificates gnupg
```

## Node.js (via NodeSource)

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
sudo npm install -g pnpm typescript ts-node nodemon
```

## Python tools

```bash
# uv — fast pip/venv replacement
curl -LsSf https://astral.sh/uv/install.sh | sh

# standard pip extras
pip install --upgrade pip virtualenv
```

## GitHub CLI

```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg \
  | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] \
  https://cli.github.com/packages stable main" \
  | sudo tee /etc/apt/sources.list.d/github-cli.list
sudo apt update && sudo apt install -y gh
```

Authenticate with a fine-grained personal access token:

```bash
gh auth login --with-token <<< "your_token_here"
gh auth status
```

## Tips

- Claude Code runs bash non-interactively — avoid commands that need a TTY (e.g. `gh auth login` without `--with-token`)
- Use `gh auth setup-git` to avoid embedding tokens in remote URLs
- Docker works fine on 2 GB RAM for 1–2 lightweight containers

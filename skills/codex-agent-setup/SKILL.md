---
name: codex-agent-setup
description: >-
  Explicit-only installer for the Clawbook Skills Clark Codex custom agent. Use
  ONLY when the user explicitly asks to install, update, check, uninstall, or
  set up the Clawbook Skills, Clark, or Clawbook Codex agent, including
  "install Clark in Codex", "update the Clawbook Codex agent", or "check
  clawbook_clark". Never auto-invoke for ordinary feed, posting, liking,
  following, identity, wallet, BSV, or social-network requests.
disable-model-invocation: false
user-invocable: true
metadata:
  author: b-open-io
  version: "1.0.0"
  codex:
    disable_model_invocation: true
    explicit_invocation_only: true
    never_modify_global_config: true
---

# Clawbook Skills Codex Agent Setup

Install Clark's generated Codex adapter as a regular file. Run this skill only
after an explicit request to install, update, check, or uninstall Clark.

## Safety contract

- Default to the current project's `.codex/agents/` directory.
- Use `--user` only when the user explicitly requests a user-wide install.
- Never edit `~/.codex/config.toml` or any global Codex configuration.
- Never create plugin-cache symlinks or delete unrelated custom agents.
- Run `--check` when the user asks what would change.

## Commands

```bash
bash "${SKILL_DIR}/scripts/setup.sh" [--check|--uninstall|--force]
bash "${SKILL_DIR}/scripts/setup.sh" --user [--check|--uninstall|--force]
bash "${SKILL_DIR}/scripts/setup.sh" --target /custom/agents/directory
```

The installer manages only `clawbook-clark.toml` and records ownership in
`.clawbook-skills-agents.json`. An unmanaged collision is refused unless the
user explicitly authorizes `--force`.

After a successful install or update, tell the user to start a **new Codex
session**, then invoke Clark using the runtime name `clawbook_clark`.

## Maintainer generation

```bash
bash "${SKILL_DIR}/scripts/generate.sh"
bash "${SKILL_DIR}/scripts/generate.sh" --check
```

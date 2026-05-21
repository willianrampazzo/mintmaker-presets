# AGENTS.md

## Project overview

This repository contains a collection of Renovate configuration presets that can be added to a `renovate.json` file using the `extends` directive (see `README.md` for a usage example).

## Commands

- **Validate**: Use Podman or Docker locally to validate a config preset (replace `<filename.json>` with the file you are editing) and fix any reported issues: 
  `podman run --rm -v "$(pwd)/<filename.json>:/workspace/<filename.json>:Z" -w /workspace quay.io/konflux-ci/mintmaker-renovate-image:latest renovate-config-validator --no-global --strict <filename.json>`. 
  *(Note: You can replace `podman` with `docker` in the command above depending on the available local container engine).* Requires network access to pull `quay.io/konflux-ci/mintmaker-renovate-image:latest`.

## Agent Directives

- **Commits**: Do NOT commit unless asked. Use conventional commits (e.g., `feat:`, `fix:`, `chore:`).
- **Formatting**: New presets must be valid JSON and must contain the Renovate schema (`"$schema": "https://docs.renovatebot.com/renovate-schema.json"`).
- **Layout**: All presets live as top-level `*.json` files and follow hyphen-case naming convention.
- **Patterns**: Try to follow the patterns used in the existing presets.
- **Scope**: Do not modify files other than the presets and documentation unless explicitly instructed to do so.
- **Secrets**: Presets are public config and must not contain any tokens or credentials.
- **Style**: New presets should ideally be short, modular, and reusable. Prefer a small new preset over growing an unrelated existing one.

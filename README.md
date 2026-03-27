# WinUI 3 Microsoft Docs Skill

This repository holds the `winui3-microsoft-docs` Codex skill—curated routing and references to Microsoft Learn material for WinUI 3 and the Windows App SDK. The skill is intentionally narrow: it points to official docs for controls, navigation, system integration, deployment, App Services, and other Windows-native capabilities without re-encoding the tutorials themselves.

## Layout

- `SKILL.md` defines the skill metadata, workflow, and routing guidance that Codex uses to decide when to load the skill.
- `agents/openai.yaml` supplies the UI metadata (display name, short description, default prompt).
- `references/` contains focused reference files (`doc-map.md`, `core-development.md`, `advanced-scenarios.md`, `platform-capabilities.md`, `system-and-shell-integration.md`, `deployment-and-migration.md`) that Codex loads on demand.

## Installation

1. **Via local `skill-installer` helper** (recommended):
   ```bash
   cd $CODEX_HOME/skills
   python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py --repo zyt-code/winui3-microsoft-docs --path .
   ```
   This downloads the skill and installs it under `$CODEX_HOME/skills/winui3-microsoft-docs`.

2. **Manual install**:
   Copy the repository into `$CODEX_HOME/skills/<skill-name>` or `~/.codex/skills/<skill-name>` if `CODEX_HOME` is unset. Ensure the directory contains `SKILL.md`, `agents/`, and `references/`, then restart Codex.

## Usage Example

Once installed, invoke the skill with `$winui3-microsoft-docs` when the user wants Microsoft Learn guidance for WinUI 3 controls, deployment, notifications, authentication, background tasks, or system integration. Start with:
```
Use $winui3-microsoft-docs to map official Microsoft Learn references for handling WinUI 3 app themes and scheduling tasks.
```

Restart Codex after installing to ensure the new skill is active.

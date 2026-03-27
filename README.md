# WinUI 3 Microsoft Docs Skill

This repository publishes the `winui3-microsoft-docs` Codex skill: curated routing and reference files for official Microsoft Learn documentation about WinUI 3 and the Windows App SDK.

The skill is designed for questions about controls, navigation, deployment, authentication, background tasks, system integration, tray interop, activation, packaging, Store publishing, and related Windows-native app behavior.

## Repository Layout

This repository is structured to work directly with the local `skill-installer` helper:

```text
skills/
  winui3-microsoft-docs/
    SKILL.md
    agents/openai.yaml
    references/
```

The installable skill lives in `skills/winui3-microsoft-docs/`.

## Installation

1. Via the local `skill-installer` helper (recommended):

   ```powershell
   python C:\Users\zhangyutong\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --repo zyt-code/winui3-microsoft-docs --path skills/winui3-microsoft-docs
   ```

2. Via GitHub URL:

   ```powershell
   python C:\Users\zhangyutong\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --url https://github.com/zyt-code/winui3-microsoft-docs/tree/main/skills/winui3-microsoft-docs
   ```

3. Manual install:

   Copy `skills/winui3-microsoft-docs` into `~/.codex/skills/winui3-microsoft-docs`.

Restart Codex to pick up new skills.

## Coverage

- Core WinUI 3 development, XAML, controls, and navigation
- MVVM Toolkit, WebView2, notifications, activation, and app instancing
- Authentication, app data, camera, media, accessibility, share, and print
- Dark or light mode handling, timers, background tasks, Task Scheduler, and tray interop
- Packaging, MSIX signing, CI/CD, Store publishing, and UWP migration

## Usage Example

Example:

```
Use $winui3-microsoft-docs to map official Microsoft Learn references for WinUI 3 dark mode changes, startup tasks, and tray integration.
```

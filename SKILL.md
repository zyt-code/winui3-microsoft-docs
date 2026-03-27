---
name: winui3-microsoft-docs
description: Curated Microsoft Learn reference and workflow for WinUI 3 and the Windows App SDK. Use when Codex needs official Microsoft documentation for WinUI 3 desktop development, XAML controls, navigation, binding, MVVM Toolkit, WebView2, notifications, app instancing, protocol or file activation, authentication, app data, camera or media, accessibility, sharing, printing, dark or light mode handling, RequestedTheme or ActualThemeChanged, in-app timers, background tasks, Task Scheduler, startup tasks, tray or notification area icons, resident app behavior, App Services, C++ or C++/WinRT templates, packaging, MSIX signing, CI/CD, Store publishing, Windows App SDK versions, or UWP migration. Also use when a user asks for WinUI 3 docs, Microsoft Learn links, or answers grounded only in official Microsoft sources.
---

# WinUI 3 Microsoft Docs

## Overview

Use this skill to answer WinUI 3 and Windows App SDK questions from official Microsoft Learn documentation. Keep `SKILL.md` lean, start with `references/doc-map.md`, and load only the reference file that matches the user's task.

## Working Rules

- Prefer `learn.microsoft.com` pages and Microsoft-owned GitHub repositories only when a Learn page explicitly points to them.
- Keep WinUI 3 / Windows App SDK separate from legacy UWP / WinUI 2 docs.
- Treat pages under `https://learn.microsoft.com/en-us/windows/winui/api/` or with `view=winui-2.*` as WinUI 2 for UWP API reference, not WinUI 3 API reference.
- Treat pages under `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/` as shared XAML concept docs unless the page says otherwise. They are useful for concepts such as `ResourceDictionary`, `ControlTemplate`, and dependency properties.
- When the user asks for the latest version, downloads, release notes, or current tooling requirements, re-check the release pages in `references/deployment-and-migration.md` because those values change over time.
- When answering deployment questions, say whether the guidance applies to packaged apps, unpackaged apps, or both.
- When answering migration questions, call out desktop-app differences explicitly instead of assuming UWP behavior still applies.

## Workflow

1. Open `references/doc-map.md`.
2. Route to the narrowest relevant file.
3. Use only the official pages listed there unless the task clearly requires a fresh Microsoft Learn lookup.
4. If no single page answers the question, combine the closest official pages and clearly mark any inference.

## Routing

- Use `references/core-development.md` for project setup, controls, navigation, binding, XAML resources, control templates, dependency properties, title bar customization, and AppWindow usage.
- Use `references/advanced-scenarios.md` for WebView2, app notifications, MVVM Toolkit, dependency injection, unit testing, WinRT UI interop, app instancing, rich activation, and language-specific guidance.
- Use `references/platform-capabilities.md` for OAuth2Manager, MSAL or Entra auth, Credential Locker, Windows Hello, passkeys, app data, camera, media, Windows Share, printing, accessibility, widgets, and other Windows integration topics.
- Use `references/system-and-shell-integration.md` for dark or light mode behavior, `RequestedTheme`, `ActualThemeChanged`, `DispatcherQueueTimer`, background tasks, Task Scheduler, startup tasks, launch-to-settings flows, and tray or notification area integration.
- Use `references/deployment-and-migration.md` for packaged vs unpackaged tradeoffs, MSIX, framework-dependent vs self-contained deployment, runtime bootstrapper guidance, app lifecycle, release channels, downloads, and UWP migration.
- Stay on `references/doc-map.md` when the user is asking for a broad reading list, a docs collection, or "where should I start?" guidance.

## API Reference Safety

- Prefer the Windows App SDK API landing pages:
  - `https://learn.microsoft.com/en-us/windows/apps/api-reference/`
  - `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/`
- Prefer namespace and type pages under `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/`.
- If you find a control article plus an API page, use the control article for behavior and patterns, then use the API page for exact type or member names.
- If a result looks correct but is clearly labeled WinUI 2 for UWP, do not use it as the primary source for WinUI 3 behavior.

## References

- `references/doc-map.md`
- `references/core-development.md`
- `references/advanced-scenarios.md`
- `references/platform-capabilities.md`
- `references/system-and-shell-integration.md`
- `references/deployment-and-migration.md`

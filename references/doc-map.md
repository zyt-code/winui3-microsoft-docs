# WinUI 3 Microsoft Learn Doc Map

Collected on `2026-03-27`.

Use this file as the entry point. It is a compact routing map, not a full tutorial.

## Start Here

- WinUI 3 overview: `https://learn.microsoft.com/en-us/windows/apps/winui/winui3/`
  - Use for: what WinUI 3 is, supported OS floor, official starting links, WinUI 3 Gallery, and samples.
  - Notes: WinUI 3 is part of the Windows App SDK and targets Windows 10 version 1809 and later.
- Quick start: Set up your environment and create a WinUI 3 project: `https://learn.microsoft.com/en-us/windows/apps/get-started/start-here`
  - Use for: required tooling, Visual Studio workloads, Developer Mode, and the recommended packaged template.
  - Notes: At collection time the page asks for Visual Studio 2026 and recommends `WinUI Blank App (Packaged)`.
- Windows developer platform overview: `https://learn.microsoft.com/en-us/windows/apps/get-started/`
  - Use for: framework choice, why WinUI is the recommended native framework, and how WinUI fits inside the Windows App SDK.
- Samples and resources: `https://learn.microsoft.com/en-us/windows/apps/get-started/samples`
  - Use for: Windows App SDK samples, WinUI 3 Gallery, Community Toolkit pointers, and MVVM Toolkit discovery.

## Route By Task

- New app, project templates, install prerequisites:
  - Start with `references/core-development.md`
  - Read the quick start and samples pages first.
- Controls, layouts, `NavigationView`, gallery examples:
  - Open `references/core-development.md`
- Binding, `x:Bind`, resources, styles, templates, dependency properties:
  - Open `references/core-development.md`
- Title bar, multi-window, `AppWindow`, desktop lifecycle:
  - Open `references/core-development.md`
- WebView2, notifications, MVVM Toolkit, dependency injection, unit tests:
  - Open `references/advanced-scenarios.md`
- C++/WinRT templates, WinRT components, mixed-language guidance:
  - Open `references/advanced-scenarios.md`
- OAuth2Manager, Microsoft identity platform, Credential Locker, Windows Hello, passkeys:
  - Open `references/platform-capabilities.md`
- App data, local settings, camera, media, sharing, printing:
  - Open `references/platform-capabilities.md`
- Accessibility, keyboard access, Store accessibility checks, widgets:
  - Open `references/platform-capabilities.md`
- Dark or light mode, `RequestedTheme`, `ActualTheme`, theme-change events:
  - Open `references/system-and-shell-integration.md`
- App instancing, rich activation, file or protocol activation:
  - Open `references/system-and-shell-integration.md`
- In-app timers, recurring work, background tasks, startup at logon:
  - Open `references/system-and-shell-integration.md`
- Task Scheduler, maintenance tasks, tray icons, notification area:
  - Open `references/system-and-shell-integration.md`
- Single-instance behavior, activation redirection, protocol handlers, file associations:
  - Open `references/system-and-shell-integration.md`
- Resident desktop app patterns, hide to tray, restore window, `HWND` interop:
  - Open `references/system-and-shell-integration.md`
- App Services and UI-less app-to-app communication:
  - Open `references/system-and-shell-integration.md`
- Packaged vs unpackaged, MSIX, deployment model, runtime bootstrapper:
  - Open `references/deployment-and-migration.md`
- App Installer, certificate signing, sideloading, Microsoft Store submission:
  - Open `references/deployment-and-migration.md`
- `SignTool`, package certificates, Azure Key Vault signing, Azure DevOps MSIX packaging:
  - Open `references/deployment-and-migration.md`
- Release channels, latest downloads, stable version checks:
  - Open `references/deployment-and-migration.md`
- UWP to Windows App SDK migration:
  - Open `references/deployment-and-migration.md`

## API Lookup Entry Points

- API reference for Windows desktop apps: `https://learn.microsoft.com/en-us/windows/apps/api-reference/`
- Windows App SDK namespaces: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/`
- Example WinUI namespace page: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml`

## Current Version Snapshot

Treat this section as stale unless re-checked.

- Release channels page: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/release-channels`
- Downloads page: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/downloads`
- At collection time:
  - Stable: `1.8.6 (1.8.260317003)`, released `2026-03-18`
  - Preview: `2.0 Preview (2.0-preview)`, released `2026-02-13`
  - Experimental: `2.0 Experimental 6 (2.0.0-experimental6)`, released `2026-03-13`
  - Current servicing branch: `1.8`, end of servicing `2026-09-09`
  - Maintenance branch: `1.7`, end of servicing `2026-03-18`

## Avoid These Traps

- Do not treat pages under `https://learn.microsoft.com/en-us/windows/winui/api/` as WinUI 3 API reference. Those are WinUI 2 for UWP unless the page explicitly says otherwise.
- Do not assume old UWP guidance about suspension, `Window.Current`, `CoreDispatcher`, or package identity still applies to WinUI 3 desktop apps.
- Do use shared XAML concept pages under `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/` for concepts such as `ResourceDictionary`, control templates, and dependency properties.
- Do distinguish between WinUI 3 APIs and Win32 interop. There is no first-party Windows App SDK tray icon API; tray guidance is still Win32 Shell documentation.
- Do re-open the release pages for any "latest" answer. The release snapshot in this skill is only a bookmark, not a source of truth.
- Do distinguish packaged, unpackaged, and packaged-with-external-location guidance before quoting deployment steps.

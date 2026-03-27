# Deployment, Releases, And Migration

Collected on `2026-03-27`.

Use this file for packaging, deployment, runtime initialization, lifecycle, release/version checks, and UWP migration guidance.

## Packaging And Deployment Foundations

- Packaging overview: `https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/packaging/`
  - Use for: packaged vs unpackaged tradeoffs, package identity, and why packaging changes available Windows features.
- Package and deploy Windows apps overview: `https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/`
  - Use for: the broad install/update/servicing model and the reasons packaging matters.
- Windows App SDK deployment overview: `https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/deploy-overview`
  - Use for: framework-dependent vs self-contained deployment choices.

## MSIX And Runtime Deployment

- Package your app using single-project MSIX: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/single-project-msix`
  - Use for: the default modern packaged WinUI 3 workflow, one-project packaging, and build automation notes.
- Package a desktop or UWP app in Visual Studio: `https://learn.microsoft.com/en-us/windows/msix/package/packaging-uwp-apps`
  - Use for: package signing, bundles, manifest packaging settings, and Store upload package guidance.
- Windows App SDK deployment guide for framework-dependent packaged apps: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/deploy-packaged-apps`
  - Use for: packaged apps that use Windows App SDK runtime packages.
- Windows App SDK deployment guide for framework-dependent apps packaged with external location or unpackaged: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/deploy-unpackaged-apps`
  - Use for: unpackaged or external-location apps, installer/runtime prerequisites, and Bootstrapper/Dynamic Dependencies requirements.
- Use the Windows App SDK runtime for apps packaged with external location or unpackaged: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/use-windows-app-sdk-run-time`
  - Use for: runtime initialization requirements and the `<WindowsPackageType>None</WindowsPackageType>` path.
- App Installer file overview: `https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview`
  - Use for: `.appinstaller` update feeds, direct web or share-based installs, and automatic update behavior outside the Store.
- Building an MSIX package from your code: `https://learn.microsoft.com/en-us/windows/msix/desktop/source-code-overview`
  - Use for: deciding between Visual Studio packaging and build-environment packaging from source.
- Package from the command line: `https://learn.microsoft.com/en-us/windows/msix/package/manual-packaging-root`
  - Use for: `MakeAppx.exe`, `SignTool`, and non-Visual-Studio packaging flows.

## Lifecycle And Desktop Behavior

- Windows App SDK app lifecycle: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/applifecycle/applifecycle`
  - Use for: desktop lifecycle semantics.
  - Notes: Windows App SDK apps are desktop apps; they do not use UWP suspend/resume semantics.
- App lifecycle, background tasks, and system services in Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/app-lifecycle-and-system-services`
  - Use for: a broader index when lifecycle questions branch into activation, background tasks, or notifications.

## Release Management

- Windows App SDK release channels: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/release-channels`
  - Use for: stable vs preview vs experimental policy, support level, and the latest release in each channel.
- Latest Windows App SDK downloads: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/downloads`
  - Use for: exact installer/download links and current runtime build numbers.
- Snapshot at collection time:
  - Stable: `1.8.6 (1.8.260317003)`, released `2026-03-18`
  - Preview: `2.0 Preview (2.0-preview)`, released `2026-02-13`
  - Experimental: `2.0 Experimental 6 (2.0.0-experimental6)`, released `2026-03-13`
- Support lifecycle snapshot:
  - `1.8` is the current release family and is serviced through `2026-09-09`
  - `1.7` is the maintenance release family and ends servicing on `2026-03-18`
- Rule: never trust the snapshot for a "latest" question without re-opening the release pages.

## Publishing And Distribution

- Publish your app in the Microsoft Store: `https://learn.microsoft.com/en-us/windows/apps/publish/`
  - Use for: Partner Center workflow, Store submission, app reservations, listings, updates, and monitoring.
- Distribute your packaged desktop app: `https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/desktop-to-uwp-distribute`
  - Use for: Store versus sideload distribution and packaged desktop app rollout options.
- Distribute your MSIX in a consumer environment: `https://learn.microsoft.com/en-us/windows/msix/desktop/managing-your-msix-deployment-retail`
  - Use for: direct web distribution and consumer-facing MSIX delivery notes outside the Store.

## Signing, Certificates, And CI/CD

- Create a certificate for package signing: `https://learn.microsoft.com/en-us/windows/msix/package/create-certificate-package-signing`
  - Use for: creating a self-signed test certificate, exporting PFX files, and importing trust locally.
- Sign a Windows 10 app package: `https://learn.microsoft.com/en-us/windows/msix/package/signing-package-overview`
  - Use for: signing requirements, trust chain expectations, and why timestamping matters.
- Sign an app package using SignTool: `https://learn.microsoft.com/en-us/windows/msix/package/sign-app-package-using-signtool`
  - Use for: exact `SignTool` syntax after package creation.
- Sign packages with Azure Key Vault: `https://learn.microsoft.com/en-us/windows/msix/desktop/sign-with-akv-cert`
  - Use for: keeping the signing key out of the build machine and using Visual Studio with Azure Key Vault-backed certificates.
- MSIX and CI/CD Pipeline Overview: `https://learn.microsoft.com/en-us/windows/msix/desktop/cicd-overview`
  - Use for: Azure Pipelines strategy and command-line packaging or signing in CI.
- MSIX Packaging Extension: `https://learn.microsoft.com/en-us/windows/msix/desktop/msix-packaging-extension`
  - Use for: Azure DevOps task-based packaging, signing, and deployment automation.
- Rule: if the user asks for GitHub Actions, start with the automation notes in the single-project MSIX article. If the user asks for Azure DevOps, start with the CI/CD overview and MSIX Packaging Extension pages.

## UWP To Windows App SDK Migration

- Migrate from UWP to the Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/migrate-to-windows-app-sdk-ovw`
  - Use for: overall migration strategy, supported-feature review, and migration topic index.
- User interface migration (including WinUI 3): `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/guides/winui3`
  - Use for: `Window.Current` replacements, `DispatcherQueue`, `XamlRoot`, content dialogs, pickers, and WinUI UI refactors.
- Windowing functionality migration: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/guides/windowing`
  - Use for: moving from UWP windowing concepts to `Microsoft.UI.Windowing.AppWindow`.
- What's supported when migrating from UWP to WinUI 3: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/what-is-supported`
  - Use for: a current support matrix before committing to a migration plan.
- Mapping UWP features to the Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/feature-mapping-table`
  - Use for: side-by-side comparison across packaging, APIs, app model, and migration notes.

## Migration Pitfalls To Call Out

- `Window.Current` does not carry over directly; use the Windows App SDK guidance instead.
- `CoreDispatcher` patterns often migrate to `DispatcherQueue`, not `Window.Dispatcher`.
- `ContentDialog` and `Popup` often need `XamlRoot` to be set explicitly.
- Packaged and unpackaged apps have different runtime initialization and deployment requirements.
- A new WinUI 3 template gives you `MainWindow`; it does not automatically give you a UWP-style page navigation shell.
- Do not plan a migration from the happy path alone. Check the support matrix first for controls, media, printing, authentication, and platform-specific APIs.

# Advanced WinUI 3 Scenarios

Collected on `2026-03-27`.

Use this file for higher-level app architecture and platform integration: WebView2, notifications, MVVM Toolkit, dependency injection, unit testing, activation, and interop edge cases.

## MVVM Toolkit, Dependency Injection, And Testing

- Data binding, dependency injection, and unit testing in WinUI: `https://learn.microsoft.com/en-us/windows/apps/tutorials/winui-mvvm-toolkit/intro`
  - Use for: the end-to-end Microsoft tutorial that introduces MVVM Toolkit, DI, and tests in a WinUI 3 app.
- Implement MVVM with the MVVM Toolkit: `https://learn.microsoft.com/en-us/windows/apps/tutorials/winui-mvvm-toolkit/mvvm-implementation`
  - Use for: `ObservableObject`, `RelayCommand`, source generators, and view model structure.
- Add dependency injection: `https://learn.microsoft.com/en-us/windows/apps/tutorials/winui-mvvm-toolkit/dependency-injection`
  - Use for: `Microsoft.Extensions.DependencyInjection`, `ServiceCollection`, `ActivatorUtilities`, and app-level service registration.
- Add unit tests: `https://learn.microsoft.com/en-us/windows/apps/tutorials/winui-mvvm-toolkit/unit-testing`
  - Use for: isolating view models and services, fake implementations, and MSTest-based validation.
- Rule: use these pages for architecture and workflow, not as the only authority for WinUI API details. Pair them with API or XAML concept pages when answering exact framework questions.

## WebView2 In WinUI 3

- Get started with WebView2 in WinUI 3 (Windows App SDK) apps: `https://learn.microsoft.com/en-us/microsoft-edge/webview2/get-started/winui`
  - Use for: creating a first WinUI 3 app that hosts WebView2, environment setup, and the default packaged template flow.
- WebView2 in WinUI 3 (Windows App SDK) apps: `https://learn.microsoft.com/en-us/microsoft-edge/webview2/platforms/winui3-windows-app-sdk`
  - Use for: platform-specific behavior, custom environments, and WinUI 3-specific considerations.
- WinUI 3 (Windows App SDK) sample app: `https://learn.microsoft.com/en-us/microsoft-edge/webview2/samples/webview2-winui3-sample`
  - Use for: a reference sample and fixed-version runtime distribution patterns.
- Rule: WebView2 docs live under Microsoft Edge documentation on Microsoft Learn. They are still official Microsoft sources and are appropriate for WinUI 3 WebView2 guidance.

## Notifications, Instancing, And Rich Activation

- App notifications overview: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/notifications/app-notifications/`
  - Use for: the current Windows App SDK app-notification model, terminology, and local versus cloud-sourced flows.
- App notifications overview: `https://learn.microsoft.com/en-us/windows/apps/develop/notifications/app-notifications/toast-notifications-overview`
  - Use for: notification terminology, scenarios, and implementation entry points.
- Quickstart: App notifications in the Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/notifications/app-notifications/app-notifications-quickstart`
  - Use for: local notifications in desktop Windows App SDK apps and sample code.
- Push notifications overview: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/notifications/push-notifications/`
  - Use for: raw notifications, cloud-sourced app notifications, Azure app-registration requirements, and support limits.
- Quickstart: Push notifications in the Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/notifications/push-notifications/push-quickstart`
  - Use for: end-to-end setup of WNS push notifications in desktop Windows App SDK apps.
- App lifecycle, background tasks, and system services: `https://learn.microsoft.com/en-us/windows/apps/develop/app-lifecycle-and-system-services`
  - Use for: the index page for lifecycle features such as app instancing, background tasks, rich activation, and power management.
- Rich activation with the app lifecycle API: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/applifecycle/applifecycle-rich-activation`
  - Use for: file activation, protocol activation, startup activation, and activation registration for packaged and unpackaged apps.
- AppInstance API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.windows.applifecycle.appinstance`
  - Use for: exact members such as `FindOrRegisterForKey`, `RedirectActivationToAsync`, `GetCurrent`, and `GetActivatedEventArgs`.
- ActivationRegistrationManager API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.windows.applifecycle.activationregistrationmanager`
  - Use for: exact activation registration methods for unpackaged or external-location scenarios.
- Rule: when answering activation or notifications questions, always say whether the app is packaged, unpackaged, or packaged with external location because the setup steps differ.
- Rule: for push notifications, call out that Azure app registration is required and that self-contained or elevated apps may not be supported.

## Interop And Desktop-Only Edge Cases

- Display WinRT UI objects that depend on CoreWindow: `https://learn.microsoft.com/en-us/windows/apps/develop/ui/display-ui-objects`
  - Use for: pickers, dialogs, and other WinRT UI objects that need `IInitializeWithWindow` or related HWND interop in desktop apps.
- Rule: if the user asks why a picker or WinRT dialog works in UWP but fails in WinUI 3 desktop, check this page before assuming the API is unsupported.

## C++, C++/WinRT, And Mixed-Language Guidance

- Visual Studio for Windows app development: `https://learn.microsoft.com/en-us/windows/apps/dev-tools/visual-studio`
  - Use for: current C++ and C# template names, Windows Runtime Component templates, and test project templates.
- Tutorial: Create a simple photo viewer with WinUI 3: `https://learn.microsoft.com/en-us/windows/apps/get-started/simple-photo-viewer-winui3`
  - Use for: a current tutorial with both C# and C++/WinRT tabs.
- Walkthrough: Create a C# component with WinUI 3 controls, and consume it from a C++/WinRT app that uses the Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/csharp-winrt/create-winrt-component-winui-cswinrt`
  - Use for: mixed-language interop and authoring reusable WinUI components.
- Rule: some broader C++/WinRT concept docs still live under the UWP documentation tree. Use them carefully for language projection concepts, but anchor WinUI 3 behavior in Windows App SDK docs first.

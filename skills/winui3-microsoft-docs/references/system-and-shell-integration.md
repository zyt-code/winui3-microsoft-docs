# System And Shell Integration

Collected on `2026-03-27`.

Use this file for system-facing desktop integration topics that commonly come up in WinUI 3 apps: dark or light mode behavior, theme change detection, timers and scheduled work, startup and background execution, activation routing, resident-window behavior, Task Scheduler, App Services, and tray or notification area interop.

## Theme And System Appearance

- Theming in Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/ui/theming`
  - Use for: the official conceptual guide to light and dark themes, theme brushes, accent colors, and color APIs in Windows apps.
- Color in Windows: `https://learn.microsoft.com/en-us/windows/apps/design/style/color`
  - Use for: design guidance on system color modes, accent colors, and how app theme aligns with Windows visual language.
- Application.RequestedTheme API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml.application.requestedtheme?view=windows-app-sdk-1.8`
  - Use for: the exact rule set for app-wide theme selection in WinUI 3.
  - Notes: Microsoft explicitly says `RequestedTheme` can only be set when the app starts. Changing it while the app is running throws an exception in .NET.
- FrameworkElement.ActualTheme API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml.frameworkelement.actualtheme?view=windows-app-sdk-1.8`
  - Use for: reading the currently effective theme on a specific element.
- FrameworkElement.ActualThemeChanged API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml.frameworkelement.actualthemechanged?view=windows-app-sdk-1.8`
  - Use for: reacting to theme changes while the app is running.
- UISettings.GetColorValue API reference: `https://learn.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.uisettings.getcolorvalue?view=winrt-26100`
  - Use for: reading system foreground, background, and accent-related colors when the problem crosses from XAML theme state into OS color state.
- UISettings.ColorValuesChanged API reference: `https://learn.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.uisettings.colorvalueschanged?view=winrt-26100`
  - Use for: detecting OS color-mode changes for non-XAML surfaces or Win32 interop scenarios.
- Support Dark and Light themes in Win32 apps: `https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/ui/apply-windows-themes`
  - Use for: Win32-level theme guidance, especially when the question involves standard title bars, DWM attributes, or non-XAML surfaces.
- System backdrops (Mica/Acrylic): `https://learn.microsoft.com/en-us/windows/apps/develop/ui/system-backdrops`
  - Use for: system material behavior that follows user theme and desktop personalization.
- Rule: for pure WinUI 3 XAML, prefer `RequestedTheme`, `ActualTheme`, `ActualThemeChanged`, and `{ThemeResource}` guidance.
- Rule: when the question is really about title bar color or native non-XAML surfaces, pair WinUI docs with the Win32 dark-mode article.

## In-App Timers And Repeating Work

- DispatcherQueueTimer API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.dispatching.dispatcherqueuetimer?view=windows-app-sdk-1.8`
  - Use for: repeating UI-thread or dispatcher-thread work while the app is running.
- DispatcherQueue.CreateTimer API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.dispatching.dispatcherqueue.createtimer?view=windows-app-sdk-1.8`
  - Use for: creating periodic timers on the current dispatcher queue.
- DispatcherQueue API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.dispatching.dispatcherqueue?view=windows-app-sdk-1.8`
  - Use for: dispatching, thread affinity, and queue lifetime constraints around timers.
- Rule: `DispatcherQueueTimer` is for work while your app is alive. It is not a replacement for a system-scheduled task that must run after the app exits.

## Background Tasks, Startup, And Scheduled Work

- Launching Windows apps and managing background tasks: `https://learn.microsoft.com/en-us/windows/apps/develop/launch/`
  - Use for: the official entry point for URI activation, launch flows, and background task topics.
- Using background tasks in Windows apps: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/applifecycle/background-tasks`
  - Use for: Windows App SDK background-task architecture in WinUI 3 apps, COM-based task entry points, trigger types, and manifest requirements.
  - Notes: Microsoft explicitly states that Task Scheduler helps desktop apps achieve similar functionality to UWP `BackgroundTaskBuilder`.
- Background task migration strategy: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/guides/background-task-migration-strategy`
  - Use for: understanding the difference between UWP `BackgroundTaskBuilder` and Windows App SDK `BackgroundTaskBuilder`, especially during migration.
- Working with background tasks in Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/launch/create-and-register-a-background-task`
  - Use for: concrete background-task registration patterns including recurring 15-minute `TimeTrigger` examples.
- StartupTask API reference: `https://learn.microsoft.com/en-us/uwp/api/windows.applicationmodel.startuptask?view=winrt-26100`
  - Use for: startup-at-logon behavior for packaged desktop apps.
  - Notes: this page lives under the WinRT API docs but its remarks explicitly mention desktop applications in a Windows app package.
- Launch Windows Settings: `https://learn.microsoft.com/en-us/windows/apps/develop/launch/launch-settings`
  - Use for: opening system settings pages from a WinUI 3 app, including settings pages relevant to privacy or user-controlled startup behavior.
- Rule: if the requirement is "run when the app is open", prefer `DispatcherQueueTimer`.
- Rule: if the requirement is "run even when the app is not running", check whether Windows App SDK background tasks are enough; if not, move to Task Scheduler.
- Rule: startup tasks require package identity. If the app is unpackaged, do not assume `StartupTask` is available.

## App Instancing, Protocols, And File Activation

- App lifecycle, background tasks, and system services: `https://learn.microsoft.com/en-us/windows/apps/develop/app-lifecycle-and-system-services`
  - Use for: the official index page that calls out app instancing, background tasks, and rich activation as supported Windows App SDK system-service features.
- AppInstance class: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.windows.applifecycle.appinstance?view=windows-app-sdk-1.8`
  - Use for: the supported members involved in single-instance or multi-instance coordination, including `GetCurrent`, `GetInstances`, `FindOrRegisterForKey`, `RedirectActivationToAsync`, and `Restart`.
- AppInstance.FindOrRegisterForKey: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.windows.applifecycle.appinstance.findorregisterforkey?view=windows-app-sdk-1.8`
  - Use for: exact single-instance key-registration semantics.
- AppInstance.RedirectActivationToAsync: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.windows.applifecycle.appinstance.redirectactivationtoasync?view=windows-app-sdk-1.8`
  - Use for: redirecting activation payloads from a new process to an existing instance.
- Rich activation with the app lifecycle API: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/applifecycle/applifecycle-rich-activation`
  - Use for: file activation, protocol activation, startup activation, and the packaged versus unpackaged registration model.
  - Notes: the current Windows App SDK article says unpackaged apps support four common activation kinds: `Launch`, `File`, `Protocol`, and `StartupTask`.
- Handle URI activation: `https://learn.microsoft.com/en-us/windows/apps/develop/launch/handle-uri-activation`
  - Use for: manifest registration of protocol handlers, reserved scheme constraints, and how WinUI apps read activation args.
- Handle file activation in a Windows app: `https://learn.microsoft.com/en-us/windows/apps/develop/launch/handle-file-activation`
  - Use for: file association registration and handling the activated payload in a Windows app.
- Rule: if the user wants a true single-instance WinUI 3 app, start with `AppInstance.FindOrRegisterForKey` plus `RedirectActivationToAsync`.
- Rule: if the user wants one primary instance with secondary documents or actions, preserve multi-instance design options and redirect only specific activation kinds.
- Rule: for unpackaged apps, registration is done through app lifecycle registration APIs or traditional registry keys; for packaged apps, use the app manifest.

## Resident App Patterns, Window Hide Or Restore, And Interop

- Windowing overview for WinUI and Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/develop/ui-input/windowing-overview`
  - Use for: the conceptual relationship between `Window`, `HWND`, and `AppWindow`.
- Manage app windows: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/windowing/windowing-overview`
  - Use for: `AppWindow` behavior, `Changed` events, and WinUI-to-AppWindow interop.
- AppWindow class: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.windowing.appwindow?view=windows-app-sdk-1.8`
  - Use for: the set of top-level window methods and properties available for WinUI 3 desktop apps.
- AppWindow.Hide: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.windowing.appwindow.hide?view=windows-app-sdk-1.8`
  - Use for: hiding a top-level window while keeping the object alive.
- AppWindow.Show: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.windowing.appwindow.show?view=windows-app-sdk-1.6`
  - Use for: restoring or showing a previously hidden window.
- AppWindow.Changed: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.windowing.appwindow.changed?view=windows-app-sdk-1.8`
  - Use for: responding to visibility, size, z-order, or presenter changes while the app stays resident.
- Retrieve a window handle (HWND): `https://learn.microsoft.com/en-us/windows/apps/develop/ui/retrieve-hwnd`
  - Use for: getting the `HWND` needed for tray interop, Win32 menus, or Shell APIs from a WinUI 3 window.
- Inference from current Microsoft docs: modern WinUI resident-app behavior is usually a hybrid. Use `AppWindow` for hide or show and general window state, then drop to `HWND` and Win32 Shell APIs for tray interactions.
- Rule: if the user says "minimize to tray", do not answer with only minimize logic. Decide whether they want `AppWindow.Hide`, whether the window should disappear from Alt+Tab, and whether tray restore should activate the window.

## Task Scheduler And Long-Lived Scheduling

- Task Scheduler for developers: `https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page`
  - Use for: the top-level guide to Task Scheduler, triggers, actions, interfaces, and XML.
- About the Task Scheduler: `https://learn.microsoft.com/en-us/windows/win32/taskschd/about-the-task-scheduler`
  - Use for: conceptual background, task components, security contexts, and scheduling model.
- Using the Task Scheduler: `https://learn.microsoft.com/en-us/windows/win32/taskschd/using-the-task-scheduler`
  - Use for: examples such as scheduled launch at a time, daily, weekly, boot, or logon.
- Automatic maintenance (Task Scheduler): `https://learn.microsoft.com/en-us/windows/win32/taskschd/task-maintenence`
  - Use for: opportunistic maintenance tasks that run when the machine is idle and on AC power.
- Taskschd.h header reference: `https://learn.microsoft.com/en-us/windows/win32/api/taskschd/`
  - Use for: the COM interfaces and concrete trigger or action types once you know the pattern you need.
- Rule: Task Scheduler is the right official path when the app needs true system scheduling independent of app lifetime.
- Rule: when the user asks for "every X minutes even after reboot" or "at logon/system boot", steer toward Task Scheduler or `StartupTask`, not `DispatcherQueueTimer`.

## Tray And Notification Area

- Notifications and the Notification Area: `https://learn.microsoft.com/en-us/windows/win32/shell/notification-area`
  - Use for: official UX guidance and lifecycle expectations for tray or notification area icons.
- The Taskbar: `https://learn.microsoft.com/en-us/windows/win32/shell/taskbar`
  - Use for: how the taskbar and notification area behave, including add, modify, delete, and focus handling.
- Shell_NotifyIcon function: `https://learn.microsoft.com/en-us/windows/win32/api/shellapi/nf-shellapi-shell_notifyicona`
  - Use for: add, modify, delete, and focus operations for a tray icon.
- NOTIFYICONDATA structure: `https://learn.microsoft.com/en-us/windows/win32/api/shellapi/ns-shellapi-notifyicondataa`
  - Use for: callback messages, icon metadata, balloon content, GUID identity, and tooltip fields.
- Inference from current Microsoft docs: there is no first-party Windows App SDK or WinUI 3 tray icon API documented on Microsoft Learn. For WinUI 3 tray behavior, use Win32 shell interop.
- Rule: if the user wants a tray icon in a WinUI 3 app, answer from Win32 shell docs and clearly say that this part is interop, not WinUI-native API.
- Rule: Microsoft says the user should control whether a non-transient icon remains visible in the notification area. Respect that guidance in UX recommendations.

## App Services And Headless IPC

- Create and consume an app service: `https://learn.microsoft.com/en-us/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service`
  - Use for: the only detailed Microsoft Learn walkthrough that shows an app service implemented as a background task, connection setup, manifest extensions, and request or response flow.
  - Notes: this article is UWP-specific, but it still documents the core `Windows.ApplicationModel.AppService` model and background-task hosting behavior.
- Windows.ApplicationModel.AppService namespace: `https://learn.microsoft.com/en-us/uwp/api/windows.applicationmodel.appservice?view=winrt-26100`
  - Use for: the full type inventory when you need exact names.
- AppServiceConnection class: `https://learn.microsoft.com/en-us/uwp/api/windows.applicationmodel.appservice.appserviceconnection?view=winrt-26100`
  - Use for: connection lifecycle, `OpenAsync`, `SendMessageAsync`, `RequestReceived`, and `ServiceClosed`.
- Rule: treat App Services as package-identity-centered IPC. If the user is building an unpackaged WinUI 3 app, do not assume App Services are the best fit without checking packaging constraints.
- Rule: if the requirement is simply "background companion process" or "tray helper talks to main app", compare App Services against plain local IPC before recommending it.

## Decision Shortcuts

- Theme changes in a running XAML app:
  - Start with the theming article, then use `ActualThemeChanged`.
- App-specific light or dark preference:
  - Start with `Application.RequestedTheme`, then persist the choice in app settings and apply on restart.
- Repeat something every few seconds while a window is open:
  - Use `DispatcherQueueTimer`.
- Run on a 15-minute schedule or on system changes while the app is not foregrounded:
  - Check Windows App SDK background tasks first.
- Run at a specific time, boot, logon, or maintenance window:
  - Use Task Scheduler docs.
- Show a tray icon or context menu:
  - Use `Shell_NotifyIcon` and notification-area guidance.
- Open the app via `myapp://` or a custom file extension:
  - Start with rich activation plus the protocol or file-activation articles.
- Keep one main instance and forward later launches into it:
  - Use `AppInstance.FindOrRegisterForKey` and `RedirectActivationToAsync`.
- Hide the main window and restore it from the tray:
  - Combine `AppWindow.Hide`, `AppWindow.Show`, `HWND` retrieval, and Win32 notification-area APIs.
- Build UI-less IPC between packaged Windows apps:
  - Check App Services, but say clearly when the guidance comes from UWP docs rather than Windows App SDK-first docs.

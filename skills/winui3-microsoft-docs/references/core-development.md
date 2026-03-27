# Core WinUI 3 Development

Collected on `2026-03-27`.

Use this file for day-to-day WinUI 3 development work: project creation, controls, navigation, binding, XAML resources, customization, and API lookup.

## Project Setup And Discovery

- Quick start: Set up your environment and create a WinUI 3 project: `https://learn.microsoft.com/en-us/windows/apps/get-started/start-here`
  - Use for: required tooling, workloads, Developer Mode, the first project template, and the recommendation to start with a packaged template.
- WinUI 3 overview: `https://learn.microsoft.com/en-us/windows/apps/winui/winui3/`
  - Use for: official framing, capabilities, links to WinUI 3 Gallery, samples, and Windows App SDK release notes.
- Samples and resources: `https://learn.microsoft.com/en-us/windows/apps/get-started/samples`
  - Use for: the Windows App SDK samples repo, WinUI 3 Gallery repo and Store app, Community Toolkit, and MVVM Toolkit discovery.
- Visual Studio for Windows app development: `https://learn.microsoft.com/en-us/windows/apps/dev-tools/visual-studio`
  - Use for: current WinUI project templates, item templates, templated controls, resource dictionaries, test projects, and the recommended Visual Studio workflow.
- Tutorial: Create a simple photo viewer with WinUI 3: `https://learn.microsoft.com/en-us/windows/apps/get-started/simple-photo-viewer-winui3`
  - Use for: a modern end-to-end tutorial in both C# and C++/WinRT that exercises layout, models, binding, and assets.

## Controls And Navigation

- Controls for Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/`
  - Use for: the master index of WinUI controls and patterns, including links to individual control articles.
- NavigationView: `https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/navigationview`
  - Use for: adaptive navigation shell behavior, item invocation, top vs left navigation, and built-in back button behavior.
- Navigation history and backwards navigation for Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/ui/navigation/navigation-history-and-backwards-navigation`
  - Use for: `Frame`, `Page`, `GoBack`, and background rules for back-stack behavior.
  - Notes: Microsoft explicitly recommends `NavigationView` for most multi-page apps.
- ItemsRepeater: `https://learn.microsoft.com/en-us/windows/apps/design/controls/items-repeater`
  - Use for: custom virtualized collection UIs when `ListView` or `GridView` are too opinionated.
  - Notes: `ItemsRepeater` does not provide built-in selection, scrolling, or accessibility policy; you own those pieces.

## Data Binding, XAML Resources, And Customization

- Windows data binding in depth: `https://learn.microsoft.com/en-us/windows/apps/develop/data-binding/data-binding-in-depth`
  - Use for: `Binding` vs `x:Bind`, one-time / one-way / two-way behavior, `DataContext`, and `INotifyPropertyChanged`.
- `{x:Bind}` markup extension: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/x-bind-markup-extension`
  - Use for: compiled binding syntax, performance tradeoffs, function bindings, and `x:DataType`.
  - Notes: `x:Bind` defaults to `OneTime`; `Binding` defaults differ.
- ResourceDictionary and XAML resource references: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/xaml-resource-dictionary`
  - Use for: `ResourceDictionary`, `StaticResource`, `ThemeResource`, merged dictionaries, theme dictionaries, and app-wide styling structure.
- XAML platform: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/`
  - Use for: the concept index for XAML topics that apply broadly to WinUI 3 and shared Windows XAML development.
- Dependency properties overview: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/dependency-properties-overview`
  - Use for: property-system behavior, defaults, and why dependency properties matter for styling, binding, and animation.
- Custom dependency properties: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/custom-dependency-properties`
  - Use for: implementing custom dependency properties in custom controls or reusable components.
- Control templates: `https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/xaml-control-templates`
  - Use for: retemplating controls, `TemplateBinding`, visual states, and custom visuals.
- Localize strings in your UI and the app package manifest: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/mrtcore/localize-strings`
  - Use for: `.resw` files, `ms-resource:` identifiers, and package manifest localization in Windows App SDK apps.

## Windowing And Desktop-Specific Behavior

- Windowing overview for WinUI and Windows App SDK: `https://learn.microsoft.com/en-us/windows/apps/develop/ui-input/windowing-overview`
  - Use for: how `Window` and `AppWindow` fit together conceptually in WinUI 3 desktop apps.
- Title bar customization: `https://learn.microsoft.com/en-us/windows/apps/develop/title-bar`
  - Use for: title bar customization, `Window.SetTitleBar`, `ExtendsContentIntoTitleBar`, and the newer `TitleBar` control.
  - Notes: the article explicitly covers Windows App SDK apps with or without WinUI 3.
- Manage app windows: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/windowing/windowing-overview`
  - Use for: `AppWindow`, presenters, top-level HWND abstraction, and when to use Windows App SDK windowing APIs alongside WinUI.
- Windows App SDK app lifecycle: `https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/applifecycle/applifecycle`
  - Use for: desktop lifecycle differences from UWP, `Application.Current`, `Window.Activated`, `Window.Closed`, and state-save guidance.
- Access files and folders with WinUI 3 and WinRT APIs: `https://learn.microsoft.com/en-us/windows/apps/develop/files/winrt-files`
  - Use for: file and folder access, WinRT storage APIs, system libraries, file properties, and packaged-app storage scenarios.

## API Lookup Pattern

- API reference for Windows desktop apps: `https://learn.microsoft.com/en-us/windows/apps/api-reference/`
  - Use for: deciding whether you need Windows App SDK WinRT APIs, Win32 APIs, or .NET APIs.
- Windows App SDK namespaces: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/`
  - Use for: namespace discovery before drilling into specific types.
- Microsoft.UI.Xaml namespace: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml`
  - Use for: a canonical example of the correct WinUI 3 / Windows App SDK API reference family.

## Practical Interpretation Rules

- Prefer control articles for usage patterns and API pages for exact names and signatures.
- If the page says `Applies to: WinUI 3` or clearly targets the Windows App SDK, treat it as authoritative for WinUI 3.
- If the page is a shared XAML concept page, use it for concepts, then verify any version-specific API behavior against Windows App SDK pages.
- If a search result lands on `windows/winui/api` with `view=winui-2.*`, do not use it as your primary WinUI 3 API source.
- If the user needs a working scaffold in either C# or C++/WinRT, prefer the current tutorials and Visual Studio template docs over older blog-style samples.

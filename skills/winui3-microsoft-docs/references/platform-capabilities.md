# Platform Capabilities And Integration

Collected on `2026-03-27`.

Use this file for Windows platform features that WinUI 3 apps commonly integrate with: authentication, secure storage, app data, media and camera, Windows Share, printing, accessibility, and widgets.

## Security, Authentication, And Identity

- Security and identity: `https://learn.microsoft.com/en-us/windows/apps/develop/security/`
  - Use for: the official Windows app security index across OAuth, Credential Locker, Windows Hello, biometrics, certificates, passkeys, and WinRT or Win32 security APIs.
- Implement OAuth 2.0 in Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/security/oauth2`
  - Use for: the modern Windows App SDK `OAuth2Manager` guidance for desktop apps such as WinUI 3.
  - Notes: Microsoft explicitly recommends authorization code with PKCE and explains why `WebAuthenticationBroker` is awkward in desktop apps.
- OAuth2Manager API reference: `https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.security.authentication.oauth.oauth2manager`
  - Use for: exact method names and types after reading the conceptual OAuth article.
- Credential locker for Windows apps: `https://learn.microsoft.com/en-us/windows/apps/develop/security/credential-locker`
  - Use for: secure storage of user credentials in WinUI and other packaged desktop apps.
  - Notes: the article warns not to store passwords in app settings and states a limit of 20 credentials per app.
- Windows Hello: `https://learn.microsoft.com/en-us/windows/apps/develop/security/windows-hello`
  - Use for: biometric or PIN-backed authentication and migration from password-based flows.
- Tutorial: Create a Windows Hello login app: `https://learn.microsoft.com/en-us/windows/apps/develop/security/windows-hello-login`
  - Use for: a concrete WinUI 3 walkthrough when the user wants a packaged desktop sign-in sample.
- Fingerprint biometrics: `https://learn.microsoft.com/en-us/windows/apps/develop/security/fingerprint-biometrics`
  - Use for: `UserConsentVerifier`-style biometric confirmation for sensitive actions.
- Intro to passkeys: `https://learn.microsoft.com/en-us/windows/apps/develop/security/intro`
  - Use for: passkey concepts, why they matter, and when they replace password flows.
- Implement passkeys: `https://learn.microsoft.com/en-us/windows/apps/develop/security/implement`
  - Use for: deployment guidance when a WinUI app or its companion service needs passkey authentication.
- Desktop application authentication documentation: `https://learn.microsoft.com/en-us/entra/identity-platform/index-desktop`
  - Use for: Microsoft identity platform desktop-app guidance when the question is specifically about Entra ID, Microsoft accounts, Graph, or MSAL.
- Overview of the Microsoft Authentication Library (MSAL): `https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview`
  - Use for: choosing MSAL and understanding token acquisition patterns for Microsoft identity flows.

## App Data And Local Storage

- Store and retrieve settings and other app data: `https://learn.microsoft.com/en-us/windows/apps/design/app-settings/store-and-retrieve-app-data`
  - Use for: `ApplicationData`, local settings, local folders, temporary data, and app-owned files.
  - Notes: the page explicitly warns not to store irreplaceable user data in app data and notes that roaming data is no longer supported on Windows 11.
- Access files and folders with WinUI 3 and WinRT APIs: `https://learn.microsoft.com/en-us/windows/apps/develop/files/winrt-files`
  - Use for: user-selected file access, app libraries, and filesystem operations through WinRT in desktop apps.

## Media, Camera, And Capture

- Audio, video, and camera: `https://learn.microsoft.com/en-us/windows/apps/develop/audio-video-camera`
  - Use for: the official feature index for playback, capture, camera, and related media APIs.
- Camera: `https://learn.microsoft.com/en-us/windows/apps/develop/camera/camera`
  - Use for: the camera topic index for WinUI apps, including preview and capture tasks.
- Show the camera preview in a WinUI 3 app: `https://learn.microsoft.com/en-us/windows/apps/develop/camera/camera-quickstart-winui3`
  - Use for: a focused WinUI 3 camera-preview walkthrough.
- Basic photo, video, and audio capture with MediaCapture in a WinUI 3 app: `https://learn.microsoft.com/en-us/windows/apps/develop/camera/basic-photo-capture`
  - Use for: custom camera flows that need more control than `CameraCaptureUI`.
- Capture photos and video in a desktop app with the Windows built-in camera UI: `https://learn.microsoft.com/en-us/windows/apps/develop/camera/cameracaptureui`
  - Use for: low-code photo or video capture in desktop apps.
  - Notes: this desktop article uses `Microsoft.Windows.Media.Capture`; the older `Windows.Media.Capture.CameraCaptureUI` guidance is for UWP.
- Media players: `https://learn.microsoft.com/en-us/windows/apps/design/controls/media-playback`
  - Use for: `MediaPlayerElement` UI usage and playback controls in XAML.

## Sharing And Printing

- Integrate with Windows: `https://learn.microsoft.com/en-us/windows/apps/develop/windows-integration/`
  - Use for: the integration index for widgets, share sheet, search providers, and other Windows shell features.
- Integrate Share options in your Windows app: `https://learn.microsoft.com/en-us/windows/apps/develop/windows-integration/integrate-sharesheet-overview`
  - Use for: deciding whether the app is a share source or share target, and whether the app is packaged or unpackaged.
- Integrate packaged apps with Windows Share: `https://learn.microsoft.com/en-us/windows/apps/develop/windows-integration/integrate-sharesheet-packaged`
  - Use for: packaged WinUI or Win32 apps that need share-target activation.
- Integrate unpackaged apps with Windows Share: `https://learn.microsoft.com/en-us/windows/apps/develop/windows-integration/integrate-sharesheet-unpackaged`
  - Use for: unpackaged or external-location apps that need package identity before share-target registration.
- Print from your app: `https://learn.microsoft.com/en-us/windows/apps/develop/devices-sensors/print-from-your-app`
  - Use for: desktop printing with `PrintManagerInterop.ShowPrintUIForWindowAsync` and `PrintDocument`.

## Accessibility And Keyboard Support

- Accessibility: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility`
  - Use for: the current accessibility hub page and links to the major accessibility topics.
- Accessibility overview: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-overview`
  - Use for: the conceptual overview of screen readers, accessible names, automation peers, media accessibility, and text accessibility.
- Keyboard accessibility: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/keyboard-accessibility`
  - Use for: tab order, focus behavior, and keyboard-only usability checks.
- Accessibility checklist: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-checklist`
  - Use for: pre-release verification of names, descriptions, labels, focus, and assistive-technology support.
- Accessibility testing: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-testing`
  - Use for: test tools and procedures before Store submission.
- Accessibility in the Store: `https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-in-the-store`
  - Use for: Microsoft Store accessibility declaration criteria.
- Access keys: `https://learn.microsoft.com/en-us/windows/apps/design/input/access-keys`
  - Use for: `AccessKey` behavior, keytips, and keyboard discoverability in WinUI apps.

## Widgets And Other Windows Integration Features

- Windows Widgets overview: `https://learn.microsoft.com/en-us/windows/apps/design/widgets/`
  - Use for: product and design overview when the app wants a Windows widget companion.
- Widget providers: `https://learn.microsoft.com/en-us/windows/apps/develop/widgets/widget-providers`
  - Use for: provider implementation guidance for packaged desktop apps and PWAs.

## Interpretation Rules

- Prefer Windows App SDK pages first when a feature has both a modern desktop page and an older UWP page.
- Use Entra or MSAL docs only when the user is specifically solving Microsoft identity platform sign-in, tenant, or token questions.
- Treat UWP-tree pages as conceptual fallback when Microsoft has not yet published an equivalent Windows apps page, and say that explicitly.
- When a feature depends on package identity, state that requirement directly in the answer.

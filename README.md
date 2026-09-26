# Dockwave

Native PostgreSQL client for macOS, with a Windows preview, for connecting,
running SQL, inspecting read-only results, and exporting CSV or JSON Lines.

[Website](https://dockwave.dev/) · [Download](https://dockwave.dev/download/) ·
[Guide](https://dockwave.dev/guide/) · [Issues](https://github.com/Rommel96/dockwave/issues)

![Dockwave PostgreSQL workspace showing a schema, SQL editor, export controls, and a completed result grid.](https://dockwave.dev/assets/workspace-complete.png)

Dockwave is a native desktop app—not Electron, a browser runtime, or a WebView.

## What it does

- Connect to PostgreSQL with saved connection profiles.
- Run selected SQL or the full editor buffer.
- Toggle SQL line comments and copy or cut whole lines in the editor.
- Inspect read-only query results.
- Export fresh results as CSV or JSON Lines.

## Status

`v0.2.0` is the current stable public release. Download it from
[Dockwave](https://dockwave.dev/download/) or
[GitHub Releases](https://github.com/Rommel96/dockwave/releases/latest).

A **Windows preview**, `v0.3.0-beta.1`, is available as a separate prerelease
on [GitHub Releases](https://github.com/Rommel96/dockwave/releases/tag/v0.3.0-beta.1).
It is not a stable release and does not include a macOS build.

## Requirements

- Available build: macOS universal binary.
- Deployment target and bundle minimum: macOS 11.0.
- Validated support: macOS 26.6.2 on Apple Silicon (arm64), with x86_64
  execution under Rosetta also verified on that host.
- macOS 11–25 are best-effort/unverified. Native Intel hardware has not been
  verified.
- Windows preview: portable x86_64 ZIP, validated on Windows 11 Pro
  (version 10.0.26200). Windows 10, other Windows 11 builds, and Windows on
  ARM are untested. The build is not code-signed, so SmartScreen warns on
  first launch.
- Linux builds are not currently available.
- A PostgreSQL server to connect to. Nothing is bundled or provisioned for
  you.

## Install

### macOS

1. Download and unzip the latest stable release.
2. Drag `Dockwave.app` to `/Applications` in Finder. Do not move it with a
   terminal command.
3. Open Dockwave once. If macOS blocks it, go to **System Settings → Privacy &
   Security**, choose **Open Anyway**, and confirm.

See the full [installation guide](https://dockwave.dev/guide/installation/) for
the first-launch flow.

Dockwave is currently not signed with a paid Apple Developer ID and is not
notarized, so macOS may block the first launch. Do not strip the quarantine
attribute; it is a useful macOS security protection.

### Windows preview

1. Download `Dockwave-0.3.0-beta.1-windows-x64.zip` from the
   [prerelease](https://github.com/Rommel96/dockwave/releases/tag/v0.3.0-beta.1)
   and unzip it into a folder of your choice.
2. Run `dockwave.exe`. If SmartScreen shows "Windows protected your PC",
   choose **More info → Run anyway**.

The preview is portable: there is no installer or auto-update. To remove it,
delete the folder and `%APPDATA%\com.dockwave.desktop\`.

## Report a problem

Open an [issue](https://github.com/Rommel96/dockwave/issues) with your macOS
version, Apple Silicon or Intel architecture, Dockwave version, and PostgreSQL
server version.

On Windows, include your Windows version and, if the app crashed, the
contents of `%APPDATA%\com.dockwave.desktop\crash.log` (secrets are redacted).

## License and notices

Use of Dockwave is subject to the [license terms](https://dockwave.dev/legal/license/).
See the [third-party notices](https://dockwave.dev/legal/third-party/) for
included dependencies.

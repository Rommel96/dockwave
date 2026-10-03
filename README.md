# Dockwave

Native PostgreSQL client for macOS and Windows, for connecting,
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

`v0.3.0` is the current stable public release, for macOS and Windows. Download
it from [Dockwave](https://dockwave.dev/download/) or
[GitHub Releases](https://github.com/Rommel96/dockwave/releases/latest).

## Requirements

- macOS: universal binary (`Dockwave-0.3.0-universal.zip`).
  - Deployment target and bundle minimum: macOS 11.0.
  - Validated support: macOS 26.6.2 on Apple Silicon (arm64), with x86_64
    execution under Rosetta also verified on that host.
  - macOS 11–25 are best-effort/unverified. Native Intel hardware has not been
    verified.
- Windows: portable x86_64 ZIP (`Dockwave-0.3.0-windows-x64.zip`), validated
  on Windows 11 Pro (build 26200). Windows 10, other Windows 11 builds, and
  Windows on ARM are untested. The build is not code-signed, so SmartScreen
  warns on first launch.
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

### Windows

1. Download `Dockwave-0.3.0-windows-x64.zip` from the
   [latest release](https://github.com/Rommel96/dockwave/releases/latest)
   and unzip it into a folder of your choice.
2. Run `dockwave.exe`. If SmartScreen shows "Windows protected your PC",
   choose **More info → Run anyway**.

The Windows build is portable: there is no installer or auto-update. To remove it,
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

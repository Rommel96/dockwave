# Dockwave

Native PostgreSQL client for macOS and Windows, with a Linux preview, for
connecting, running SQL, inspecting read-only results, and exporting CSV or JSON Lines.

[Website](https://dockwave.dev/) · [Download](https://dockwave.dev/download/) ·
[Guide](https://dockwave.dev/guide/) · [Issues](https://github.com/Rommel96/dockwave/issues)

![Dockwave PostgreSQL workspace showing a schema, SQL editor, export controls, and a completed result grid.](https://dockwave.dev/assets/workspace-complete.png)

Dockwave is a native desktop app—not Electron, a browser runtime, or a WebView.

## What it does

- Connect to PostgreSQL with saved connection profiles.
- Run selected SQL or the full editor buffer.
- Toggle SQL line comments and copy or cut whole lines in the editor.
- Inspect read-only query results.
- Export fresh results as CSV or JSON Lines, with an optional
  spreadsheet-safe CSV mode.

## Status

`v0.3.1` is the current stable public release, for macOS and Windows. Download
it from [Dockwave](https://dockwave.dev/download/) or
[GitHub Releases](https://github.com/Rommel96/dockwave/releases/latest).

A **Linux preview**, `v0.4.0-beta.1`, is available as a separate prerelease
on [GitHub Releases](https://github.com/Rommel96/dockwave/releases/tag/v0.4.0-beta.1).
It is not a stable release and contains only the Linux AppImage.

## Requirements

- macOS: universal binary (`Dockwave-0.3.1-universal.zip`).
  - Deployment target and bundle minimum: macOS 11.0.
  - Validated support: macOS 26.6.2 on Apple Silicon (arm64), with x86_64
    execution under Rosetta also verified on that host.
  - macOS 11–25 are best-effort/unverified. Native Intel hardware has not been
    verified.
- Windows: portable x86_64 ZIP (`Dockwave-0.3.1-windows-x64.zip`), validated
  on Windows 11 Pro (build 26300). Windows 10, other Windows 11 builds, and
  Windows on ARM are untested. The build is not code-signed, so SmartScreen
  warns on first launch.
- Linux preview: x86_64 AppImage (`Dockwave-0.4.0-beta.1-linux-x86_64.AppImage`),
  validated only on Omarchy with Hyprland (Wayland). It needs glibc 2.35 or
  newer. Every other distribution and desktop, including X11 sessions, is
  untested. The AppImage is not signed.
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

1. Download `Dockwave-0.3.1-windows-x64.zip` from the
   [latest release](https://github.com/Rommel96/dockwave/releases/latest)
   and unzip it into a folder of your choice.
2. Run `dockwave.exe`. If SmartScreen shows "Windows protected your PC",
   choose **More info → Run anyway**.

The Windows build is portable: there is no installer or auto-update. To remove it,
delete the folder, `%APPDATA%\com.dockwave.desktop\`, and
`%LOCALAPPDATA%\com.dockwave.desktop\`.

### Linux preview

1. Download `Dockwave-0.4.0-beta.1-linux-x86_64.AppImage` and its `.sha256`
   file from the
   [prerelease](https://github.com/Rommel96/dockwave/releases/tag/v0.4.0-beta.1).
2. Verify and run it:

   ```bash
   sha256sum -c Dockwave-0.4.0-beta.1-linux-x86_64.AppImage.sha256
   chmod +x Dockwave-0.4.0-beta.1-linux-x86_64.AppImage
   ./Dockwave-0.4.0-beta.1-linux-x86_64.AppImage
   ```

The AppImage needs FUSE 3. Without it, run it with
`APPIMAGE_EXTRACT_AND_RUN=1 ./Dockwave-0.4.0-beta.1-linux-x86_64.AppImage`.
Passwords are stored through the Secret Service (verified with GNOME
Keyring), so a Secret Service provider must be running.

The AppImage is portable: there is no installer or auto-update. To remove it,
delete the file, `~/.local/share/com.dockwave.desktop/`, and
`~/.cache/com.dockwave.desktop/` (or the same folders under
`$XDG_DATA_HOME` and `$XDG_CACHE_HOME` when set).

## Security and privacy

- **Encrypted connections by default.** New connections use TLS (`require`).
  A connection string without `sslmode` also requires TLS; to reach a local
  server without TLS, add `sslmode=disable`. Saved profiles keep the TLS mode
  you chose; switch them to `require` where your server supports it.
- **Passwords stay in the system's secret store** (macOS Keychain, Windows
  Credential Manager, the Secret Service on Linux), never in Dockwave's files.
- **Your work stays on your device.** Query history, saved queries and open
  tabs are stored locally, unencrypted, in your user folders. Anything you
  type into SQL, including secrets, is saved as written. To let you inspect
  long values, the full text of result cells on screen is also cached on
  disk and removed when the result is replaced or the app quits.
- **Spreadsheet-safe CSV.** The first CSV export asks whether to write
  formula-like values (starting with `=`, `+`, `-` or `@`) as text, so
  spreadsheets don't evaluate them. Change it anytime in General Settings
  (`⌘ + ,` on macOS, `Ctrl + ,` on Windows and Linux); it also applies when copying
  from the result grid. JSON Lines exports never change.
- **SSH host keys.** The first time you connect through an SSH host, compare
  its fingerprint with one from the server's administrator before accepting.

## Report a problem

Open an [issue](https://github.com/Rommel96/dockwave/issues) with your macOS
version, Apple Silicon or Intel architecture, Dockwave version, and PostgreSQL
server version.

On Windows, include your Windows version and, if the app crashed, the
contents of `%APPDATA%\com.dockwave.desktop\crash.log`. Passwords in it are
redacted, but open it first and remove any SQL, host names, user names, or
data values before attaching it.

On Linux, include your distribution and version, desktop session (Wayland or
X11), and, if the app crashed, the contents of
`~/.local/share/com.dockwave.desktop/crash.log`, cleaned up the same way.

## License and notices

Use of Dockwave is subject to the [license terms](https://dockwave.dev/legal/license/).
See the [third-party notices](https://dockwave.dev/legal/third-party/) for
included dependencies.

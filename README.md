# Dockwave

Native PostgreSQL client for macOS, Windows, and Linux, for connecting,
running SQL, editing eligible result cells, and exporting CSV or JSON Lines.

[Website](https://dockwave.dev/) · [Download](https://dockwave.dev/download/) ·
[Guide](https://dockwave.dev/guide/) · [Issues](https://github.com/Rommel96/dockwave/issues)

![Dockwave PostgreSQL workspace showing a schema, SQL editor, export controls, and a completed result grid.](https://dockwave.dev/assets/workspace-complete.png)

Dockwave is a native desktop app—not Electron, a browser runtime, or a WebView.

## What it does

- Connect to PostgreSQL with saved connection profiles.
- Run selected SQL or the full editor buffer.
- Toggle SQL line comments and copy or cut whole lines in the editor.
- Inspect query results and edit eligible result cells, with staged changes
  and a SQL preview before saving. Other results remain read-only, including
  joined results.
- Export fresh results as CSV or JSON Lines, with an optional
  spreadsheet-safe CSV mode.

## Status

`v0.4.0` is the current stable public release for macOS, Windows, and Linux.
Download it from [GitHub Releases](https://github.com/Rommel96/dockwave/releases/latest).

## Requirements

- macOS: universal binary (`Dockwave-0.4.0-universal.zip`).
  - Deployment target and bundle minimum: macOS 11.0; these are declarations,
    not validated support for every version.
  - Validated only on macOS 27.2 arm64. Other macOS 11–27 versions are
    best-effort/unverified; x86_64 is unverified.
- Windows: portable x86_64 ZIP (`Dockwave-0.4.0-windows-x64.zip`), validated
  only on Windows 11 Pro build 26300 x64. Windows 10, other builds, and
  Windows on ARM are untested. The build is unsigned, so SmartScreen warns
  on first launch.
- Linux: x86_64 AppImage (`Dockwave-0.4.0-linux-x86_64.AppImage`), validated
  only on Omarchy 4.0.6 x86_64 with Hyprland on Wayland and glibc 2.35 or
  newer. Other distributions, desktops, and sessions are untested. The
  AppImage is unsigned.
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

Dockwave is ad-hoc signed, not signed with a paid Apple Developer ID, and not
notarized, so macOS may block the first launch. Do not strip the quarantine
attribute; it is a useful macOS security protection.

### Windows

1. Download `Dockwave-0.4.0-windows-x64.zip` from the
   [latest release](https://github.com/Rommel96/dockwave/releases/latest)
   and unzip it into a folder of your choice.
2. Run `dockwave.exe`. If SmartScreen shows "Windows protected your PC",
   choose **More info → Run anyway**.

The Windows build is portable: there is no installer or auto-update. To remove it,
delete the folder, `%APPDATA%\com.dockwave.desktop\`, and
`%LOCALAPPDATA%\com.dockwave.desktop\`.

### Linux

1. Download `Dockwave-0.4.0-linux-x86_64.AppImage` and its `.sha256`
   file from the
   [latest release](https://github.com/Rommel96/dockwave/releases/latest).
2. Verify and run it:

   ```bash
   sha256sum -c Dockwave-0.4.0-linux-x86_64.AppImage.sha256
   chmod +x Dockwave-0.4.0-linux-x86_64.AppImage
   ./Dockwave-0.4.0-linux-x86_64.AppImage
   ```

The AppImage needs FUSE 3. Without it, run it with
`APPIMAGE_EXTRACT_AND_RUN=1 ./Dockwave-0.4.0-linux-x86_64.AppImage`.
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

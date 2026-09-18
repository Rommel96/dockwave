# Dockwave

Native macOS PostgreSQL client for connecting, running SQL, inspecting
read-only results, and exporting CSV or JSON Lines.

[Website](https://dockwave.dev/) · [Download](https://dockwave.dev/download/) ·
[Guide](https://dockwave.dev/guide/) · [Issues](https://github.com/Rommel96/dockwave/issues)

![Dockwave PostgreSQL workspace showing a schema, SQL editor, export controls, and a completed result grid.](https://dockwave.dev/assets/workspace-complete.png)

Dockwave is a native macOS app—not Electron, a browser runtime, or a WebView.

## What it does

- Connect to PostgreSQL with saved connection profiles.
- Run selected SQL or the full editor buffer.
- Inspect read-only query results.
- Export fresh results as CSV or JSON Lines.

## Status

`v0.1.0-beta.5` is the latest public prerelease for testing, not a stable
release. Download it from [Dockwave](https://dockwave.dev/download/) or
[GitHub Releases](https://github.com/Rommel96/dockwave/releases).

## Requirements

- Deployment target and bundle minimum: macOS 11.0.
- Validated support: macOS 26.6.2 on Apple Silicon (arm64), with x86_64
  execution under Rosetta also verified on that host.
- macOS 11–25 are best-effort/unverified. Native Intel hardware has not been
  verified.
- A PostgreSQL server to connect to. Nothing is bundled or provisioned for
  you.

## Install

1. Download and unzip the latest release.
2. Drag `Dockwave.app` to `/Applications` in Finder. Do not move it with a
   terminal command.
3. Open Dockwave once. If macOS blocks it, go to **System Settings → Privacy &
   Security**, choose **Open Anyway**, and confirm.

See the full [installation guide](https://dockwave.dev/guide/installation/) for
the first-launch flow.

Dockwave is currently not signed with a paid Apple Developer ID and is not
notarized, so macOS may block the first launch. Do not strip the quarantine
attribute; it is a useful macOS security protection.

## Report a problem

Open an [issue](https://github.com/Rommel96/dockwave/issues) with your macOS
version, Apple Silicon or Intel architecture, Dockwave version, and PostgreSQL
server version.

## License and notices

Use of Dockwave is subject to the [license terms](https://dockwave.dev/legal/license/).
See the [third-party notices](https://dockwave.dev/legal/third-party/) for
included dependencies.

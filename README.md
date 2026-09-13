# Dockwave

An ultralight native macOS PostgreSQL client, built for bounded memory usage,
responsive interaction, session correctness and predictable performance.

Not an Electron app, a browser runtime or a WebView. The interface is native
GPUI; the database work runs on its own runtime, never on the UI thread.

**This repository holds no source code.** It exists to carry releases, to give
you somewhere to report problems, and to serve as the project's public face.
Dockwave is not an open-source project — see [Terms](#terms) below.

## Status

`v0.1.0-beta.2` is available as a public prerelease for testing, not a stable
release. It is published under [Releases](https://github.com/Rommel96/dockwave/releases),
and the download page at [dockwave.dev](https://dockwave.dev/download/) points
at the current release.

Packaging is a universal, ad-hoc-signed `.app` bundle. Watch this repository
if you want to know when another release is published.

## Requirements

- Deployment target and bundle minimum: macOS 11.0.
- Validated support: macOS 26.6.2 on Apple Silicon (arm64), with x86_64 execution under Rosetta also verified on that host.
- macOS 11–25 are best-effort/unverified. Native Intel hardware has not been verified.
- A PostgreSQL server to connect to. Nothing is bundled or provisioned for
  you.

## Installing

Dockwave is not signed with a paid Apple Developer ID and is not notarized, so macOS will refuse to open it the first time. That is expected.

1. Download and unzip the archive.
2. **Drag `Dockwave.app` to `/Applications` in Finder.** Do this in Finder, not from a terminal — a quarantined app moved with `mv` gets run by macOS from a read-only temporary copy instead of from where you put it.
3. Open it. macOS blocks it with:

   > **"Dockwave" Not Opened**
   > Apple could not verify "Dockwave" is free of malware that may harm your Mac or compromise your privacy.

   The only buttons are **Move to Trash** and **Done**. Click **Done**. There is no "Open Anyway" here — it lives in System Settings, and it only appears after a launch has been blocked, so this step is required rather than redundant.
4. Go to **System Settings → Privacy & Security** and scroll to the bottom. A line about Dockwave being blocked now appears, with an **Open Anyway** button. Click it.
5. Confirm in the prompt that reappears.

Once only.

**Do not run commands that strip the quarantine attribute.** Removing it disables a protection that exists for good reasons, and nothing here needs it.

## Reporting problems

Use [Issues](https://github.com/Rommel96/dockwave/issues) on this repository.
Because the source is not published, this is the only channel.

When reporting, please include your macOS version, whether you are on Apple
Silicon or Intel, the Dockwave version, and the PostgreSQL server version.

## Terms

Dockwave is free to download and run, for personal or commercial purposes, on
macOS computers you own or control. You receive no rights over the source
code, which is not published: no redistribution, no modification, no right to
the source itself.

The full terms ship inside the application at
`Dockwave.app/Contents/Resources/LICENSE`.

## Third-party components

Dockwave incorporates third-party software under its own licences, chiefly MIT
and Apache-2.0, alongside BSD-3-Clause, ISC, Zlib, MPL-2.0, Unicode-3.0 and
others. Their required notices ship with the application at
`Dockwave.app/Contents/Resources/THIRD_PARTY_NOTICES.md`, and are also
available at [dockwave.dev/legal/THIRD_PARTY_NOTICES.md](https://dockwave.dev/legal/THIRD_PARTY_NOTICES.md).

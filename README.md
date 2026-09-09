# Dockwave

An ultralight native macOS PostgreSQL client, built for bounded memory usage,
responsive interaction, session correctness and predictable performance.

Not an Electron app, a browser runtime or a WebView. The interface is native
GPUI; the database work runs on its own runtime, never on the UI thread.

**This repository holds no source code.** It exists to carry releases, to give
you somewhere to report problems, and to serve as the project's public face.
Dockwave is not an open-source project — see [Terms](#terms) below.

## Status

There is no public release yet. Packaging landed recently: the application now
builds as a universal, signed `.app` bundle, but it has not been published.
When the first release exists it will appear under
[Releases](https://github.com/Rommel96/dockwave/releases), and the download
page at `dockwave.dev` will point at it.

Watch this repository if you want to know when that happens.

## Requirements

- macOS 11.0 (Big Sur) or later, on Apple Silicon or Intel. The release is a
  universal binary, so a single download serves both.
- A PostgreSQL server to connect to. Nothing is bundled or provisioned for
  you.

## Installing

Dockwave is distributed outside the Mac App Store and is not signed with a
paid Apple Developer ID, so macOS will refuse to open it on first launch and
report that it is from an unidentified developer. This is expected, and the
step to get past it is Apple's own documented one:

1. Download the archive from the release and unpack it.
2. Move `Dockwave.app` to `/Applications`.
3. Open it once. macOS will refuse.
4. Go to **System Settings → Privacy & Security**, scroll down, and choose
   **Open Anyway**.
5. Confirm again in the prompt that reappears.

You only do this once. Do not run commands that strip the quarantine
attribute: that disables a protection that exists for good reasons, and it is
not needed here.

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
`Dockwave.app/Contents/Resources/THIRD_PARTY_NOTICES.md`, and will also be
reachable from the download page.

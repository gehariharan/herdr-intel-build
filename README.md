# Herdr for Intel Mac

Unofficial, reproducible source-build workflow for [Herdr](https://github.com/herdrdev/herdr-app), an Apache-2.0 open-source application. This repository is independent of the Herdr maintainers and does not modify the app source.

## Download

Open [Releases](https://github.com/gehariharan/herdr-intel-build/releases/latest) and download `herdr-app-macos-x86_64.tar.gz`. Extract it and move `Herdr.app` into `~/Applications`. Requires an Intel Mac running macOS 15 or newer.

To verify the download, save `SHA256SUMS` in the same folder as the archive and run `shasum -a 256 -c SHA256SUMS` there.

The app is ad-hoc signed, not Apple notarized. If macOS blocks it, use System Settings → Privacy & Security → Open Anyway after attempting to open it. Herdr needs herdr-core; the app can help install the official core. Source builds do not auto-update.

## Build

Run **Build Herdr for Intel Mac** from the Actions tab. All compilation happens on GitHub's `macos-15-intel` VM. The workflow fetches upstream v0.1.12 at commit `4aa3460749947e7771aa39a8a2cec58d46649926`, including its submodules, and uses Rust 1.95.0 and Zig 0.16.0.

It builds with `cargo build --release --locked`, verifies the command-line executable, creates and verifies an ad-hoc app signature, and publishes an archive with a SHA-256 checksum. It does not test the graphical interface on a physical Intel Mac.

The archive includes upstream's LICENSE and THIRD-PARTY-NOTICES. Workflow code in this repository is licensed under Apache-2.0; upstream and dependency licenses remain applicable.

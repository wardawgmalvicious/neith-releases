# Neith

A small Windows app for viewing and editing the files you open every day:
markdown rendered beside a list of its folder, with a plain-text editor
that highlights markdown, JSON, YAML, PowerShell and other languages, and
follows the Windows light or dark theme.

This repository holds Neith's installers and update feed only.

## What it opens

Any UTF-8 text file up to 20 MB opens in the editor. Preview shows
these as more than text:

| Files | Preview |
| --- | --- |
| Markdown (`.md`, `.markdown`) | rendered, with frontmatter as a card, code blocks highlighted and images shown |
| JSON, YAML, TOML | a collapsible tree |
| CSV, TSV | a table |
| TMDL | an outline of its tables, columns, measures and other objects |
| PNG, JPEG, GIF, WebP, AVIF, BMP, ICO | the picture, to zoom and pan |
| SVG | the picture, and its source in edit mode |
| PDF | WebView2's built-in PDF viewer |

Any other text file previews as its source, highlighted where Neith knows
the language: DAX, KQL, Power Query M, TMDL and Bicep among them. The
editor underlines syntax errors in JSON, YAML, TOML, Python, JavaScript,
CSS, Rust, Go, PHP and XML, and, with
[Pyright](https://github.com/microsoft/pyright) or
[Ruff](https://docs.astral.sh/ruff/) installed, problems in Python files.

## Install

1. Open the [latest release](https://github.com/wardawgmalvicious/neith-releases/releases/latest)
   and download `Neith_<version>_x64-setup.exe`.
2. Run it. It installs for your Windows account only, so it needs no
   administrator rights.

The installer isn't code-signed yet, so Windows SmartScreen may show
**Windows protected your PC**. Choose **More info**, check that the
publisher line reads *Unknown publisher* and the file is the one you
downloaded from this page, then choose **Run anyway**.

Neith needs Windows 10 or 11 (x64) and the Microsoft Edge WebView2
runtime, which Windows 11 includes. If it's missing, the installer
downloads it.

## Check your download

With no code signature, the check that a setup.exe is the one published
here is GitHub's: each release is immutable, and GitHub records an
attestation of its files when it's published. With the
[GitHub CLI](https://cli.github.com/), check a downloaded file against
it:

```powershell
gh release verify-asset (Resolve-Path .\Neith_*_x64-setup.exe) -R wardawgmalvicious/neith-releases
```

Run it in the folder that holds the download, with one Neith setup in
it. It checks the file against the latest release; for an older
release's file, put that release's tag before the path, as in
`gh release verify-asset v0.5.0 <path> -R <repo>`.
`gh release verify -R wardawgmalvicious/neith-releases` checks the latest
release itself and lists each file's SHA-256.

Without the CLI, the release page shows **Immutable** under its title and
each file's SHA-256 beside it. Compare that with the file's own:

```powershell
Get-FileHash .\Neith_*_x64-setup.exe
```

## Updates

Neith checks this repository when it starts and offers each new version.
Installing one closes Neith, after asking about any unsaved changes.

Every release here is immutable: once published, its files can't be
changed or replaced.

## What Neith connects to

- **This repository, for updates.** At each start, and when you choose
  **Check for updates** in Settings, Neith downloads the latest release's
  `latest.json`, signed in to nothing. Installing an update downloads its
  setup.exe and signature from the same release, and Neith checks the
  signature before it runs the setup.
- **Images a markdown file embeds from the web.** Previewing a file that
  shows an `https://` image fetches it from its host, as a browser would.
  `http://` images aren't loaded.
- **Links you click** open in your default browser.

Neith sends nothing else: no account, no usage data, no crash reports.
Two programs it runs aren't Neith's, and what they send is theirs to
say: the WebView2 runtime that draws its window, which is Microsoft's
and updates itself, and Pyright or Ruff, where you've installed one and
said yes to checking a folder's Python files.

## Uninstall

Settings > Apps > Installed apps > Neith > Uninstall.

## Report a problem

Ask in [Q&A](https://github.com/wardawgmalvicious/neith-releases/discussions/categories/q-a)
with the Neith version, your Windows version and the steps that lead to
the problem.

Report a security problem privately instead, as [SECURITY.md](SECURITY.md)
says.

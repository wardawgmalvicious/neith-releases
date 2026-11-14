# Neith

A small Windows app for viewing and editing the files you open every day:
markdown rendered beside a list of its folder, with a plain-text editor
that highlights markdown, JSON, YAML, PowerShell and other languages, and
follows the Windows light or dark theme.

This repository holds Neith's installers and update feed only.

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

## Updates

Neith checks this repository when it starts and offers each new version.
Installing one closes Neith, after asking about any unsaved changes.

Every release here is immutable: once published, its files can't be
changed or replaced.

## Uninstall

Settings > Apps > Installed apps > Neith > Uninstall.

## Report a problem

Ask in [Q&A](https://github.com/wardawgmalvicious/neith-releases/discussions/categories/q-a)
with the Neith version, your Windows version and the steps that lead to
the problem.

Report a security problem privately instead, as [SECURITY.md](SECURITY.md)
says.

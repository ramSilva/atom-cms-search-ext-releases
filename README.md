# Atom Search

**Find which Atom widgets a given app config actually uses, fast.**

A browser extension for internal devs and QA who spot-check Atom widgets against the live Peacock or SkyShowtime app config. Works in Chrome, Edge, Brave, and Firefox.

This repository is the **public release mirror** — it hosts the prebuilt browser zips, the user-facing release notes, and the `latest.json` update manifest. Source code lives in a separate private repository; access to it is not required to install or use the extension.

## What you can do

- **Search widgets** for the current proposition + environment + territory + app build, then click any result straight into the Atom editor.
- **Filter results** live by free text — name, slug, config, body, or all fields — or score them against a saved list of **template formats** with a similarity threshold.
- **Find duplicate widgets** either within a single territory (different slugs, identical bodies) or across territories (per slug, do bodies drift between territories?).
- **Find dead config entries** by pointing the extension at an Android, iOS, or web source repo — the extension cross-references your config against both Atom and the code and surfaces entries that aren't backed by an Atom widget or aren't read by the code.
- **Stay current.** A banner in the dashboard surfaces newer releases when one is available.

## Install

Download the latest build for your browser from the [latest release](https://github.com/ramSilva/atom-cms-search-ext-releases/releases/latest):

- **Chrome / Edge / Brave** → `atom-cms-search-ext-vX.Y.Z-chrome.zip`
- **Firefox** → `atom-cms-search-ext-vX.Y.Z-firefox.zip`

Unzip the archive somewhere stable (don't move or delete the folder afterwards — the browser keeps loading the extension from that location).

### Chrome / Edge / Brave

1. Open `chrome://extensions` (or `edge://extensions`, `brave://extensions`).
2. Turn on **Developer mode** (top-right).
3. Click **Load unpacked** and select the unzipped folder.

### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on…** and select `manifest.json` inside the unzipped folder.

> Firefox clears temporary add-ons on restart — re-load after each browser restart.

## First-time setup

Click the toolbar icon to open the dashboard, then on the **Setup** tab:

1. **Grant host access** for the proposition(s) you'll investigate (Peacock and/or SST). Approve every URL in the browser prompt.
2. **Sign in to Atom** in a separate browser tab for the proposition + environment you'll use. The extension reuses that browser session — it never sees your credentials.
3. Back in the dashboard, click **Check auth**. If it fails, follow the sign-in link it surfaces and retry.

Once both steps pass, the dashboard auto-opens to the **Search** tab on subsequent loads.

If `Check auth` later starts failing, your Atom session has expired — sign in again and retry. If you previously denied a host on Firefox, revoke the leftover grant from the browser's extension settings and re-grant from Setup.

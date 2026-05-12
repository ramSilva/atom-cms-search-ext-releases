# Atom CMS Search

**Find which CMS widgets a given app config actually uses, fast.**

A browser extension for internal devs and QA who spot-check Atom CMS widgets against the live Peacock or SkyShowtime app config. Pick the proposition, environment, and the app build you're investigating; optionally narrow by template format; then click through any matching widget straight into the CMS editor.

Works in Chrome, Edge, Brave, and Firefox.

This repository is the **public release mirror**. It hosts the prebuilt browser zips, the user-facing release notes, and `latest.json` (the manifest the extension's update banner polls). Source code lives in a separate private repo and is not required to install or use the extension.

---

## 1. Install

Download the latest build for your browser from the [latest release](https://github.com/ramSilva/atom-cms-search-ext-releases/releases/latest):

- **Chrome / Edge / Brave** → `atom-cms-search-ext-vX.Y.Z-chrome.zip`
- **Firefox** → `atom-cms-search-ext-vX.Y.Z-firefox.zip`

Unzip the archive somewhere stable (don't delete or move the folder afterwards — the browser keeps loading the extension from that location).

### Chrome / Edge / Brave

1. Open `chrome://extensions` (or `edge://extensions`, `brave://extensions`).
2. Turn on **Developer mode** (top-right).
3. Click **Load unpacked** and select the unzipped folder.
4. The **Atom CMS Search** icon appears in the toolbar.

### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on…**.
3. Select any file inside the unzipped folder (e.g. `manifest.json`).
4. The **Atom CMS Search** icon appears in the toolbar.

> Firefox clears temporary add-ons on restart — re-load after each browser restart.

---

## 2. First-time setup

Click the toolbar icon to open the dashboard. The dashboard has two tabs — **Setup** and **Search** — and a top bar where you pick **Proposition** (Peacock or SST) and **Environment** (Stable or Prod). Both default to Peacock / Stable each time you open the dashboard.

On the **Setup** tab:

1. **Grant host access.** Click **Grant all hosts (Peacock)** and/or **Grant all hosts (SST)** depending on which one(s) you'll use. Approve every URL in the browser prompt. On Chrome/Edge/Brave this is usually already done for you at install.
2. **Sign in to Atom CMS.** In another tab, sign in to the CMS for the proposition + environment you'll use:
   - **Peacock stable**: <https://stable-int.atom.dev.nbcuott.com>
   - **Peacock prod**: <https://cms.atom.nbcuott.com>
   - **SST stable**: <https://stable-int.atom.dev.us.summerott.com>
   - **SST prod**: <https://cms.atom.eu.summerott.com>
3. Back in the dashboard, click **Check auth**. If it fails with a sign-in link, click the link, sign in, and retry. The extension never sees your credentials — it reuses the browser's existing CMS session.

Once both are done, the dashboard switches you to the **Search** tab automatically the next time you open it (as long as the active proposition's hosts are still granted).

---

## 3. Search for widgets

On the **Search** tab:

1. **Pick the app build you're investigating.** Choose a platform (Android, iOS, …) and version. The extension will fetch that build's config and use it as the source of truth for which widgets are "in use".
   - If you have a config URL that doesn't match the standard pattern, pick **Other** and paste the full URL. The extension fetches it as-is — proposition, environment, platform, and version are ignored in this mode. The URL is remembered between sessions.
2. *(Optional)* **Add template formats** to narrow results to widgets that share a specific structural shape — useful when you're hunting widgets built from the same template, or all widgets exposing a particular feature. Each entry persists between sessions and is shared across propositions.
3. Click **List widgets**.

Results appear as a list. Skim them to confirm what you expected to be there is there (or isn't). Click any row to open that widget directly in the CMS editor in a new tab.

When you change proposition or environment mid-session, the picker, auth state, and any displayed results are cleared so you don't act on stale data.

---

## 4. Re-running auth or access later

- If **Check auth** starts failing, your session has probably expired — click the sign-in link the extension surfaces, sign in again, retry.
- If you previously denied a host on Firefox, revoke any leftover grants from the browser's extension settings page, reopen the dashboard, and click **Grant all hosts** again.
- Switching proposition or environment doesn't re-check host access automatically; if you switch and the Search tab won't load, head back to **Setup** and grant the new proposition's hosts.

---

## What this repo contains

- **Releases / tags** — each tag (e.g. `v0.1.0`) has the per-browser zips attached as assets and the user-facing changelog in the release notes.
- **`latest.json`** — version manifest the extension fetches on every dashboard load. Shape:
  ```json
  {
    "version": "X.Y.Z",
    "url": "https://github.com/ramSilva/atom-cms-search-ext-releases/releases/tag/vX.Y.Z",
    "notes": "Short, user-facing changelog."
  }
  ```

Source code is not in this repo. It lives in a separate private repository; access is internal and is only required if you want to read or build the source yourself.

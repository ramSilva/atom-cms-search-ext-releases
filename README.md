# atom-cms-search-ext — public release mirror

Public download mirror for the [Atom CMS Search](https://github.com/ramSilva/atom-cms-search-ext) browser extension. The source repository is private; this repo exists so installs can pull the prebuilt Chrome and Firefox zips, and so the extension's built-in update banner can poll a public manifest.

## What's here

- **`latest.json`** — version manifest the extension fetches on every dashboard load. Shape:
  ```json
  {
    "version": "X.Y.Z",
    "url": "https://github.com/ramSilva/atom-cms-search-ext-releases/releases/tag/vX.Y.Z",
    "notes": "Short, user-facing changelog."
  }
  ```
- **Releases / tags** — each tag (e.g. `v0.1.0`) has the per-browser zips attached as assets.

No source code lives here.

## Install

Grab the latest build for your browser from the [latest release](https://github.com/ramSilva/atom-cms-search-ext-releases/releases/latest):

- **Chrome / Edge / Brave** → `atom-cms-search-ext-vX.Y.Z-chrome.zip`
- **Firefox** → `atom-cms-search-ext-vX.Y.Z-firefox.zip`

Then follow the install + first-time setup steps in the extension's main repo. (Source is private; ask in the team channel if you need access.)

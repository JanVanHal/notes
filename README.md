# Notes

A minimal, fast, single-page notes app that lives entirely in your browser — no backend, no account, no sign-up. Open the page and start writing.

**[Try it live →](index.html)**

## Features

- **Multiple notes** — Create as many notes as you like, listed as tabs in the sidebar. Click a tab to switch between notes.
- **Drag to reorder** — Drag any note in the sidebar to rearrange the list.
- **Rich text editing** — The note area is a simple rich-text editor (bold, formatting, etc. via standard browser editing).
- **Lock a note** — Lock a note to prevent accidental edits to its title or content. Locked notes show a small lock icon.
- **Two-column layout** — Toggle a note between single-column and two-column layout, handy for longer notes.
- **Adjustable text size** — Increase or decrease the font size (both UI and note text scale together), with sensible min/max limits.
- **Three themes** — Cycle between **Light**, **Medium**, and **Dark** appearance.
- **Autosave** — Everything is saved automatically to your browser's local storage as you type. No save button needed.
- **Backup & restore** — Export all your notes to a downloadable JSON file, and import a backup file back in at any time.
- **Copy note text** — Copy the plain text of the current note to your clipboard in one click.
- **Delete with confirmation** — Deleting a note asks for confirmation first, so you don't lose anything by accident.
- **Responsive** — On small/mobile screens, the sidebar collapses to give the note more room.

## How it works

This is a single `index.html` file containing all the HTML, CSS, and JavaScript needed to run the app — there is nothing to install and nothing to build.

- **Storage**: notes are stored in the browser's `localStorage`, scoped to whichever site/domain serves the page. Clearing your browser data will clear your notes, which is why the export/import backup feature exists.
- **Privacy**: nothing is sent to a server. Your notes never leave your device unless you explicitly export and share the backup file yourself.
- **Data format**: an exported backup is a plain JSON file containing your notes, their order, lock states, column layout, font size, and theme — easy to inspect or version-control if you want to.

## Using it

1. Open the page in any modern browser.
2. Click the **+** icon in the top bar to add a new note.
3. Give it a title and start typing in the body.
4. Use the top-bar icons to adjust text size, copy the note, switch to two columns, lock the note, or delete it.
5. Use the sidebar to switch themes or export/import a backup at any time.

Because everything is local to your browser, it's a good idea to periodically **export a backup**, especially before clearing browser data or switching devices.

## Installing it as a PWA (Add to Home Screen)

The page includes the meta tags that let mobile browsers treat it as a standalone, app-like experience (its own icon, no browser address bar). How to install it depends on your device:

**On iPhone/iPad (Safari)**
1. Open the page in Safari.
2. Tap the **Share** icon (square with an arrow).
3. Tap **Add to Home Screen**.
4. Confirm the name and tap **Add**. It now opens full-screen from your home screen, like a native app.

**On Android (Chrome)**
1. Open the page in Chrome.
2. Tap the **⋮** menu in the top right.
3. Tap **Add to Home screen** (or **Install app**, if Chrome offers it).
4. Confirm — it's added as an app icon that launches in its own window.

**On desktop (Chrome/Edge)**
1. Open the page.
2. Click the **install icon** in the address bar (or open the **⋮** menu and choose **Install Notes…** / **Apps → Install this site as an app**).
3. Confirm — it opens in its own app window, separate from your regular browser tabs.

**A note on current limitations:** this app doesn't yet ship a `manifest.json` or a service worker, so a couple of things fall out of true PWA territory:
- Some browsers (mainly desktop Chrome/Edge) may not show an automatic "Install" prompt without a manifest, though "Add to Home Screen"/pinning still works as above.
- The app requires an internet connection to load initially and won't work fully offline until a service worker is added — your notes themselves are still safe in local storage either way, since that's separate from network access.

Adding a `manifest.json` (app name, icons, theme colors) and a small service worker (to cache the page for offline use) would make this a fully installable, offline-capable PWA if that's something you want to build out further.

## Running it yourself

Since it's a single static HTML file, you can:

- Open `index.html` directly in a browser, or
- Serve it with any static file host (this is what powers the GitHub Pages link above).

There are no dependencies to install and no build step required.

## Tech notes

- Plain HTML, CSS, and vanilla JavaScript — no frameworks.
- Uses the `Inter` font (loaded from Google Fonts) with a system-font fallback.
- Theming is handled with CSS custom properties, switched via a CSS class on the root element.

# pages

**Publish markdown pages on your [Solid](https://solidproject.org) pod.** A
markdown editor with live preview and auto-save; each page is saved as raw
markdown at `<pod>/public/pages/<slug>` — public-readable, so it's a **live URL**
anyone can open. One self-contained HTML file, no build.

Translated from [nostrapps/nostr.app](https://github.com/nostrapps/nostr.app)'s
"Pages" (which stores to nosdav keyed by a nostr pubkey) into the Solid-pod
paradigm: storage is your pod's `/public/pages/`, auth is your **xlogin** Solid
session.

## How it works

- **List / open / create** pages (the navigator lists `/public/pages/`).
- **Edit / Split / Preview** a page — markdown in a textarea, rendered live with
  `marked`. **Auto-saves** (debounced) to the pod as `text/markdown`.
- **`[[wiki links]]`** — `[[Page Name]]` (or `[[Page Name|label]]`) renders as a
  link; click it to open that page, or create it if it doesn't exist yet.
- Each page shows its **live URL** (`<pod>/public/pages/<slug>.md`) — share it,
  it's public-readable.

## Data model

Dead simple: a page is a **raw markdown file** at `<pod>/public/pages/<slug>.md`
(`Content-Type: text/markdown`). No JSON-LD wrapper — the file *is* the page.
(For structured/linked pages with fields, see `datawiki`; for private prose
notes, `notes`.)

## Notes

- Sign-in required (writes go to your pod via your Solid session); pages are
  public-readable by design.
- `marked` loads from a CDN for rendering.

## Run

Static — open `index.html`, or install via the **store** to
`/public/apps/pages/`.

AGPL-3.0-only.

# Quick Notes

<p align="center">
  <img src="icons/icon128.png" alt="Quick Notes logo" width="96" height="96" />
</p>

<p align="center">
  <strong>A fast, distraction-aware note-taking extension</strong><br>
  Floats above any page · auto-saves · Markdown · images · split view · searchable history · Google Drive sync.
</p>

<p align="center">
  <a href="#installation"><img alt="Version" src="https://img.shields.io/badge/version-1.0.0-d4a85f.svg" /></a>
  <img alt="Manifest V3" src="https://img.shields.io/badge/manifest-v3-4285F4.svg" />
  <img alt="License" src="https://img.shields.io/badge/license-MIT-green.svg" />
  <img alt="No tracking" src="https://img.shields.io/badge/tracking-none-success.svg" />
  <a href="https://github.com/mthcht"><img alt="Author" src="https://img.shields.io/badge/by-%40mthcht-181717?logo=github" /></a>
</p>

---

## What it is

Quick Notes is a lightweight Chrome extension for keeping notes while you browse. It lives as a floating panel you can drag anywhere on any page, or as a popup from the toolbar icon. Everything auto-saves to local storage - no accounts, no servers, no telemetry. Notes are yours and stay on your machine.

Think of it as a scratchpad, journal, clipboard-assistant, and Markdown editor rolled into one tool that's always a keystroke away.

## Screenshots

<img width="1442" height="907" alt="Capture d&#39;écran 2026-04-23 100910" src="https://github.com/user-attachments/assets/a06448ef-6149-40e9-a538-dd302a7abe72" />
<img width="1378" height="906" alt="Capture d&#39;écran 2026-04-23 101236" src="https://github.com/user-attachments/assets/4a83597a-f0bc-4a83-a488-74fb4e5932cf" />
<img width="1887" height="1073" alt="Capture d&#39;écran 2026-04-23 101719" src="https://github.com/user-attachments/assets/a627bb0b-2c7e-430b-9cbe-90bb7253fe32" />
<img width="1591" height="785" alt="Capture d&#39;écran 2026-04-23 101818" src="https://github.com/user-attachments/assets/be1702c5-7130-4750-9671-82269575808a" />
<img width="893" height="794" alt="Capture d&#39;écran 2026-04-23 101836" src="https://github.com/user-attachments/assets/e73b13e8-e5be-4b9f-b9cd-0f8e1b6eeefd" />
<img width="1572" height="983" alt="Capture d&#39;écran 2026-04-23 101901" src="https://github.com/user-attachments/assets/cf9477c0-1522-4d36-9525-a72cf791030a" />

## Features

- **Floating panel** - press `Alt+N` on any page to open a draggable, resizable panel that persists across tabs. Eight-way resize handles, drag from the header, snap by double-clicking, or recenter with `Alt+Shift+R`.
- **Auto-save** - every keystroke is debounced and saved to `chrome.storage.local`. Nothing to click.
- **Multiple notes with pinning** - create, rename, delete, and pin notes. Pinned notes bubble to the top of the selector.
- **Split view** - horizontal or vertical side-by-side editing of two notes at once. Independent selectors per pane, draggable splitter, flip direction.
- **Rich Markdown preview** - headings, bold, italic, inline code, fenced code blocks, links, bullet and numbered lists, blockquotes, horizontal rules, and pipe tables with alignment. Live toggle.
- **Checklists** - `- [ ]` and `- [x]` round-trip between the textarea and real clickable checkboxes in preview mode.
- **Tables** - Excel-style hover picker (up to 8×8). Alignment syntax (`:---`, `---:`, `:---:`) respected.
- **Images & GIFs** - paste from clipboard or drag-and-drop any image file. GIFs animate. Stored by reference so notes stay readable. Preview caps image height so one screenshot can't dominate.
- **Text formatting** - bold (`B`), inline/fenced code (`</>`), and text color (8 themed palette) with a one-click toolbar group.
- **Focus mode** - a single icon hides every bar and gives you a distraction-free writing surface. `Esc` or `Alt+drag` to leave.
- **Color tags & transparency** - tag notes with one of eight colors (accent shown as a dot), adjust panel opacity from 30% to 100%.
- **Search (`Ctrl+F`)** - fuzzy search across all notes with content snippets and match counts.
- **History** - every clipboard-paste, URL grab, and selection-capture is logged (last 200) with source and timestamp.
- **Per-site auto-paste & defaults** - configure URL patterns that automatically paste incoming clipboard content, or set a default note for a specific site.
- **Backup & restore** - one-click JSON export of all notes, settings, and history. Restore on any machine.
- **Google Drive sync (opt-in)** - one-click sign-in syncs to your Drive's hidden app-data folder. Auto-sync on configurable interval, manual push/pull. See [Google Drive sync](#google-drive-sync).
- **Light & dark themes** - warm dark default, clean light mode. Toggle in header.
- **Responsive toolbar** - header and formatting bar measure their own overflow and progressively scale down icons so everything stays accessible at any panel width.
- **Privacy-respecting** - no network requests. No analytics. No remote code. All data in `chrome.storage.local`.

## Installation

### From Chrome Web Store

install from https://chromewebstore.google.com/detail/quick-notes/aelknahnnjimdajnjkjochpejeanobik

### From source

1. Clone or download this repository.
2. Open `chrome://extensions` in Chrome.
3. Enable **Developer mode** (top-right toggle).
4. Click **Load unpacked** and select the `quick-notes` folder.
5. Pin the extension icon to your toolbar (puzzle-piece menu → pin).

## Usage

| Action | Shortcut |
|---|---|
| Open / toggle panel on current page | `Alt+N` |
| Toggle floating panel on current tab | `Alt+Shift+N` |
| Save (flush auto-save) | `Ctrl+S` / `⌘+S` |
| Search across notes | `Ctrl+F` / `⌘+F` |
| Recenter floating panel | `Alt+Shift+R` |
| Exit focus mode | `Esc` |

Right-click anywhere to send page URL, selection, or a link into the active note via the context menu.

## Development

No build step - the extension is vanilla JavaScript, HTML, and CSS.

```
quick-notes/
├── manifest.json          # MV3 manifest
├── background.js          # Service worker: commands, context menus, injection
├── content.js             # Floating panel (Shadow DOM)
├── popup.html/.css/.js    # Standalone popup
├── popup-init.js          # CSP-compliant init
├── options.html/.css/.js  # Settings page
└── icons/                 # 16 / 48 / 128 px
```

To iterate: edit, then hit **Reload** on the extension card in `chrome://extensions`.

### Requirements

- Chrome 114 or newer (for `chrome.sidePanel` compatibility paths and modern Shadow DOM behavior - core features work further back).
- No external dependencies, no npm, no bundler.

## Privacy

Quick Notes stores everything locally in `chrome.storage.local`. The extension makes zero network requests by default. No usage data, crash reports, telemetry, or identifiers leave your browser. Clipboard and page-selection captures happen on-device and stay on-device. Backup exports are plain JSON files you save where you want.

Google Drive sync is **opt-in**. When enabled, your notes are synced to your own Drive's hidden `appDataFolder` (a per-app sandbox that's invisible in the regular Drive UI and accessible only to this extension via the `drive.appdata` scope - not your general Drive content). Disable any time from the options page.

### Permissions explained

The extension requests these Chrome API permissions plus broad host access:

| Permission | Why |
|---|---|
| `storage` | Save notes, settings, and history to `chrome.storage.local`. |
| `scripting` | Inject the floating panel into the active tab when you press `Alt+N`. |
| `clipboardRead` | The Paste button reads your clipboard - only on click, never in the background. |
| `contextMenus` | Adds the right-click entries ("Send selection to note," etc.). |
| `identity` | Google sign-in for opt-in Drive sync. Only used when you enable sync. |
| `alarms` | Schedule periodic auto-sync to Drive. Only fires when sync is enabled. |
| `<all_urls>` host access | Required so the floating panel can appear on any page. **No page content is read** except when you explicitly click Insert page URL / Insert selection. |

Downloads use the browser's native `<a download>` mechanism - no `downloads` permission needed. Tab URL and title come through the host permission, no `tabs` permission needed. No `activeTab` either.

## Google Drive sync

Google Drive sync is **opt-in** and uses the minimum-privilege `drive.appdata` scope - your notes are stored in a hidden per-app folder in your Drive, invisible in the regular Drive UI and accessible only to this extension.

### For users

Install the extension from the Chrome Web Store, open its options page, and click **Sign in with Google** under the "Google Drive sync" section. That's it. Choose an account, grant the `drive.appdata` permission, and your notes will sync automatically. You can disable sync or sign out from the same page at any time.

**What gets synced:** notes, history, images, settings, theme, custom theme colors, split state, font size, opacity, shape, focus mode preference. The panel **geometry** (window position) is **not** synced because screen sizes differ per-device.

**Sync strategy:** last-writer-wins based on timestamps. If the remote was modified after your last sync, **Sync now** pulls; otherwise, it pushes. Manual **Push** and **Pull** buttons let you override when needed.

### For developers (publishing your own fork)

The build shipped with a **placeholder OAuth client ID** because Google OAuth client IDs must be tied to a specific Chrome extension ID. Before you can publish your own build with working Drive sync, you'll need to register your own OAuth client.

<details>
<summary><strong>Click for the full setup walkthrough</strong></summary>

&nbsp;

1. **Pin a stable extension ID** by generating a manifest `key` field (so your unpacked dev build and published build share the same ID). Use `openssl` or a helper like [crxtool](https://github.com/oftedal/crxtool). Skip this if you're registering only for the published-store ID.
2. Load the extension unpacked and copy the **Extension ID** shown on its card in `chrome://extensions`.
3. Go to [Google Cloud Console](https://console.cloud.google.com/) → create a project (or reuse one).
4. **APIs & Services → Library** → search **Google Drive API** → **Enable**.
5. **APIs & Services → OAuth consent screen** → user type (External/Internal as appropriate) → fill app name, support email → add only the `https://www.googleapis.com/auth/drive.appdata` scope → save.
6. **APIs & Services → Credentials** → **+ Create Credentials → OAuth client ID** → application type **Chrome App** → paste your extension ID → create.
7. Copy the resulting client ID (looks like `1234-abcdef.apps.googleusercontent.com`).
8. Open `manifest.json` and replace `YOUR_GOOGLE_OAUTH_CLIENT_ID.apps.googleusercontent.com` with your real client ID.
9. Reload the extension. **Sign in with Google** now works end-to-end.

After publishing to the Chrome Web Store, its extension ID is stable - you'll re-register the OAuth client ID against the store-assigned ID (or skip this step if you pinned with a `key` field), and all end-users benefit automatically without any setup on their side.

</details>

## License

MIT License - see [LICENSE](LICENSE) for full text. Feel free to fork, modify, and redistribute.

## Contributing

Issues and pull requests are welcome. Please describe the use case in the issue before opening a PR for a feature, so we can agree on scope.

## Credits

Built with vanilla web platform APIs - Shadow DOM for CSS isolation, ResizeObserver for responsive layouts, `chrome.storage.local` for persistence. Amber accent palette `#d4a85f` over warm dark `#1F1F1E`.

---

<p align="center">
  <sub>Made for people who take notes fast and don't want to leave the page.</sub>
</p>

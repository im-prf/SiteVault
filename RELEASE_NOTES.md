# SiteVault 5.0.0

The release that makes the map feel finished: one clean interface at every window
size, a search box that suggests as you type, a preview map that shows everything
you have drawn, starter templates, and a rebuilt, single-manifest executable.

**Download:** `SiteVault-5.0.0-portable.zip` — one portable `SiteVault.exe`,
no installer, Windows 10 and 11, 32-bit and 64-bit.

## Interface

- **Properly responsive.** The header, toolbar, search box, settings panel, accounts
  grid and donate page all reflow from a 640 px window to an ultrawide screen.
  Tabs collapse to icons, the search box moves to its own row, and the settings
  panel becomes full width on narrow windows.
- **Header fixed.** The inactive tabs had no background of their own and were being
  painted as light system buttons; they are now transparent pills that match the
  theme, so the Map / Accounts / Donate row finally looks like one control.
- **`Vault` is now `Accounts`** in the header, and the page keeps the same name.
- **Settings rebuilt:** wider panel, larger type, clearly separated sections
  (General, Appearance, Layout, Data, Safety, About), an explicit **Back to map**
  button and a close button, so you are never stranded in a pane.
- The floating tool dock, hint bar and overview map keep out of the way and respect
  their own toggles. The overview map is **hidden by default**; open it with the
  small dock button or `M`.

## Map

- **Crisp to 18%.** Cards used to turn into colour blocks as early as 39% while
  zooming out. Blur and colour collapse now begin only below 18%, so ordinary
  overview zoom levels stay fully readable.
- **Overview map that really is an overview.** It frames *more* than the viewport
  instead of echoing it, in two modes: **Everything** (the whole vault, growing
  automatically as new areas are used) and **This area** (only the chunk you are in).
  It is clickable, draggable and always shows where you are.
- **One-piece connector animation.** Category → site flow used to stack half-finished
  passes on top of each other and stutter on large maps; it is now a single clean
  sweep with no queueing.
- **Align helper**, on by default: nudge a card close to a neighbour's edge or centre
  in the same category and it lines up. Drag further and it stays exactly where you
  drop it — it is a nudge, never a rule.
- Grid snapping, per-category tidy, horizontal distribute, and `Ctrl+click` plus
  drag to move sites and categories together.

## Search

- The header box now opens its own **grouped suggestion list** — Categories, then
  Sites, then Accounts — with `Enter` to jump, `Ctrl+Enter` to open in your browser
  and `Esc` to close. Suggestions are no longer pushed through the command palette.
- `Ctrl+F` (or `/`) opens the search box from anywhere, including while another tab
  is open. The old `Ctrl+A` shortcut was removed; it overlapped with Select All and
  could surprise you mid-edit.

## Accounts

- Account cards, search, group filter and sorting by site, group, oldest, weakest,
  strongest or reused.
- Strength and reuse warnings, one-click copy, optional clipboard auto-clear.
- **No app password.** Any lock screen and encryption layer has been removed: the
  vault has nothing to unlock, so nothing can lock you out of your own data.

## Data

- **Starter templates** in Settings ▸ Data: `Starter map`, `Developer`, `Designer`,
  `Student`, `Everyday` and a blank canvas. One click drops in a fully arranged map
  — categories, sites, colours and positions — and `Ctrl+Z` brings the old one back.
  Accounts are never touched.
- **Backups cover everything**: categories, every card position, notes, per-site
  card/border/connector colours, pin state, accounts and every single preference,
  including overview settings and layout toggles.
- Removed the pointless bulk actions: `Open all sites`, `Copy all addresses` and
  `Copy all crypto` are gone. Sites open only when you click their address or a
  menu item, in your default Windows browser.
- The session interaction counter now starts at zero every time the app opens.
- Undo history is capped by both steps and memory, and can be released on demand.

## Security and packaging

- One clean application **manifest**: visual styles, per-monitor DPI and an explicit
  `asInvoker` trust level in a single resource. The linker's extra default manifest is
  mapped away during the build instead of shipping a second, conflicting copy.
- Hardened link flags: stack protection, DEP, ASLR and high-entropy ASLR. Nothing is
  packed, compressed or obfuscated, so the file stays readable to security scanners.
- Developer tools, the browser context menu, page zoom, the status bar and browser
  accelerator keys are disabled in the shipped build; the app never looks like a web
  page.
- The WebView2 Runtime is installed once, silently, from Microsoft if a machine does
  not have it — no dialogs, no labels pretending something was installed.
- The WebView2 profile and disk cache stay capped and are trimmed on every launch.

## Fixes

- The `?` shortcut dialog and the Settings ▸ General card now show the same list,
  built from one source. The dialog had quietly lost four entries (`Drag a
  selection`, `Ctrl+C`, `Ctrl+Shift+C`, `Ctrl+,`) while the settings card had them.
- Icons no longer drift out of their buttons at small window sizes.
- The Donate page no longer overlaps its own header; every address has one Copy
  button, and Contact links (LinkedIn, Telegram) were added.
- The Map tab no longer renders as a blank dark box on other tabs.
- Long-path support, correct version resource (5.0.0.0) and a single icon group.

SiteVault 5.0.0 is the continuation of the NetSaver 1–3 releases.

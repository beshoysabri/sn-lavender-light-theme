# Lavender Light Theme for Standard Notes

[![License: MIT](https://img.shields.io/badge/License-MIT-6d61d1.svg)](LICENSE)
[![Standard Notes](https://img.shields.io/badge/Standard%20Notes-Theme-6366f1.svg)](https://standardnotes.com)

A light theme for [Standard Notes](https://standardnotes.com) with a lavender accent, set in [Inter](https://rsms.me/inter/) — the daytime twin of [Lavender](https://github.com/beshoysabri/sn-lavender-theme).

Every grey is Lavender's charcoal palette mirrored: the same contrast from the base, on the other side of it. The accent keeps lavender's hue but deepens to `#6d61d1`, because the pastel `#a79ef4` is too faint to carry text on white, and the softness moves into **lavender washes** for the selected tag, the selected note, selected text and the scrollbar. See [What Changed vs Lavender](#what-changed-vs-lavender).

Lavender Light is a fork of Lavender, which is a fork of [Dark Blue](https://github.com/beshoysabri/sn-dark-blue-theme): same stylesheet structure, same Inter setup, same GitHub Pages hosting and pre-publish checks. It keeps their version line, so the history is shared — v2.7.0 is the first Lavender Light release.

## Installation

1. Open the Standard Notes **desktop** app
2. Go to **Preferences** > **Plugins** > **Install Custom Plugin** (at the bottom of the page — older versions had it under **General** > **Advanced Settings**)
3. Paste the following URL:

```
https://beshoysabri.github.io/sn-lavender-light-theme/ext.json
```

4. Click **Install**
5. Select **Lavender Light** from the Appearance menu

There's a preview and a copy button at **[beshoysabri.github.io/sn-lavender-light-theme](https://beshoysabri.github.io/sn-lavender-light-theme)**.

Lavender Light has its own identifier, so it installs alongside Lavender and Dark Blue rather than replacing either.

**Install from the desktop app, not the web app.** The web app's Content-Security-Policy only lets it fetch plugin links from Standard Notes' own servers and `raw.githubusercontent.com`, and even that one fails, because the request is sent with credentials and GitHub answers `Access-Control-Allow-Origin: *`. Pasting the link there gives *"Error downloading package details"* — for every self-hosted theme. Installed themes sync with your account, though, and the web app loads the stylesheet and fonts from Pages without complaint, so once it's installed on the desktop it shows up on the web too.

### Pair it with Lavender

Install [Lavender](https://beshoysabri.github.io/sn-lavender-theme) as well, then go to **Preferences** > **Appearance**, turn on **Use system color scheme**, and choose:

- **Automatic Light Theme:** Lavender Light
- **Automatic Dark Theme:** Lavender

Standard Notes then switches between the two with your OS. Custom themes are listed in both menus. The choice is stored per device, so set it once on each.

| Client | Colours | Inter |
|---|---|---|
| Web | yes | yes, downloaded automatically |
| Desktop | yes | install Inter on the machine — see below |
| Mobile | yes | install Inter on the device — works on iOS and Android |

### Everywhere except the web app, install Inter on the device

The desktop app sends `Content-Security-Policy: default-src 'self' blob:` with no `font-src`, so it refuses to download **any** webfont — from this repo, from a CDN, or inlined as a `data:` URI. No theme can ship a font file into it.

What does work is a font already installed on the device. There's no download, so CSP has nothing to block — it's just a family-name lookup, and the stack is written so an installed copy is found automatically. The same trick works on mobile.

**Desktop**

1. Download Inter from [rsms.me/inter](https://rsms.me/inter/)
2. Install **both** `InterVariable.ttf` and `InterVariable-Italic.ttf` (inside `Desktop/` in the zip) — Font Book on macOS, right-click → Install on Windows. Skipping the italic leaves italics synthesised by slanting the roman rather than using Inter's real italic shapes.
3. Fully quit Standard Notes and reopen it; the system font list is read at launch

**Mobile** — install Inter as a system font (iOS needs a font-installer app that adds a configuration profile; Android varies by manufacturer), then restart Standard Notes.

If Inter is already installed for Lavender, there's nothing more to do. Skip this and the theme still works — you get the colours, and the text stays on the system font. That's a correct fallback, not a failure.

<details>
<summary>Alternative: jsDelivr</summary>

The theme is also reachable over jsDelivr:

```
https://cdn.jsdelivr.net/gh/beshoysabri/sn-lavender-light-theme@master/ext.json
```

Both origins serve the same files. GitHub Pages is the default because branch-pinned jsDelivr URLs are cached for roughly 12 hours, so a push doesn't show up until the cache expires or you purge it. Pages republishes on every push to `master`.

</details>

## Hosting

Pushing to `master` triggers `.github/workflows/pages.yml`, which verifies the theme before publishing — that `ext.json` and `package.json` agree on a version, that both woff2 files exist, that both `@font-face` sources are the absolute Pages URLs, that all **90** colour declarations still hash to the Lavender Light palette's digest, that some rule actually applies `--sn-inter-font`, that the rule honouring the Monospace Font option is still there, that the section 6 opt-ins are still commented out, and that braces balance in the comment-stripped `dist.css`. A failed check blocks the deploy rather than shipping a broken stylesheet.

The digest covers every custom property except the three `--sn-inter-*` typography knobs.

Enable it once under **Settings → Pages → Source → GitHub Actions**.

## Color Palette

| Role | Hex | Preview |
|------|-----|---------|
| Background | `#ffffff` | ![ffffff](https://img.shields.io/badge/-ffffff-ffffff?style=flat-square) |
| Sidebar & surfaces | `#f5f5f5` | ![f5f5f5](https://img.shields.io/badge/-f5f5f5-f5f5f5?style=flat-square) |
| Border | `#eeeeee` | ![eeeeee](https://img.shields.io/badge/-eeeeee-eeeeee?style=flat-square) |
| Separator | `#e0e0e0` | ![e0e0e0](https://img.shields.io/badge/-e0e0e0-e0e0e0?style=flat-square) |
| Foreground | `#2a2a2a` | ![2a2a2a](https://img.shields.io/badge/-2a2a2a-2a2a2a?style=flat-square) |
| Secondary text | `#707070` | ![707070](https://img.shields.io/badge/-707070-707070?style=flat-square) |
| Accent (Lavender) | `#6d61d1` | ![6d61d1](https://img.shields.io/badge/-6d61d1-6d61d1?style=flat-square) |
| Accent, darkened | `#5446c9` | ![5446c9](https://img.shields.io/badge/-5446c9-5446c9?style=flat-square) |
| Selection wash | `#6d61d1` at 18% | ![e5e3f7](https://img.shields.io/badge/-e5e3f7-e5e3f7?style=flat-square) |
| Text selection | `#6d61d1` at 25% | ![dad8f4](https://img.shields.io/badge/-dad8f4-dad8f4?style=flat-square) |
| Text on accent | `#ffffff` | ![ffffff](https://img.shields.io/badge/-ffffff-ffffff?style=flat-square) |
| Success | `#007662` | ![007662](https://img.shields.io/badge/-007662-007662?style=flat-square) |
| Warning | `#ebad00` | ![ebad00](https://img.shields.io/badge/-ebad00-ebad00?style=flat-square) |
| Danger | `#cc2128` | ![cc2128](https://img.shields.io/badge/-cc2128-cc2128?style=flat-square) |

The two translucent rows are previewed as they render on the background.

## Typography

The whole app is set in Inter v4.1 — sidebar, note list, menus and note text. The variable font, roman and italic, is bundled in `dist/fonts/` under the SIL Open Font License.

Two details make it work:

- **The `@font-face` sources are absolute, not relative.** Standard Notes inlines theme CSS instead of linking it, so a relative `url('fonts/…')` resolves against the app's own origin and 404s. v2.2.0 shipped that bug; the fonts never loaded in any client.
- **The family is set on elements, not through a variable.** Standard Notes doesn't read `--sn-stylekit-sans-serif-font` for its own chrome, so setting that variable changes nothing. `html, body, body *` is what actually reaches the UI.

Code keeps a monospace face. That rule is listed after the app-wide one so it wins at equal specificity, and it disables contextual alternates so `->` stays two characters where that matters.

Standard Notes' **Monospace Font** option (Preferences → Appearance) switches the note editor to monospace. Until v2.7.1 the app-wide Inter rule overrode it and the switch did nothing; a rule after it now hands the editor back.

Three variables at the top of `dist/dist.css` control it:

| Variable | Purpose |
|---|---|
| `--sn-inter-font` | The family stack. Inter has no Arabic or CJK glyphs, so those scripts fall through to the next family rather than rendering as boxes. |
| `--sn-inter-mono` | Code face. Defaults to whatever Standard Notes already uses. |
| `--sn-inter-features` | OpenType features. `cv05` gives lowercase `l` a tail so it stops looking like a capital `I`. Set to `normal` to disable. |

Inter's contextual alternates fuse `->` into a single `→` glyph. If the caret feels off by one when you arrow across it, section 6 has a block that turns the arrows off. Since v2.7.1 it takes `calt` out of `--sn-inter-features` too, because `font-feature-settings` outranks `font-variant-ligatures`; before, the block left the arrows in place. Section 6 also has tighter heading tracking, roomier leading, tabular figures in tables, and a block that confines Inter to the editor.

## Daily View

Standard Notes' Daily notebook borrows the app's `danger` token for today's date, the days that have an entry, the entry tiles and both create-note buttons — so on a lavender theme they came out red. Section 4 of the stylesheet repaints those specific elements with the accent instead.

It's scoped deliberately rather than recolouring `--sn-stylekit-danger-color` wholesale, for two reasons: destructive controls should stay red, and the rules only *reference* the accent variables rather than declaring new ones — so the colour digest is unaffected.

One difference from Lavender: a day that has an entry sets its date in the darkened shade, because on the lavender wash `#6d61d1` is 3.9:1 and `#5446c9` is 5.4:1.

## Selection

Standard Notes uses one colour for both hover and selection, in the two places that matter: `--navigation-item-selected-background-color` in the sidebar, and `--item-cell-selected-background-color` in the note list, which the app defines as the contrast background. Under native Light those are a white bar on the grey sidebar (`#fdfdfd`) and a grey bar in the list (`#f4f5f7`).

Section 5 keeps hover a neutral grey and gives the selected sidebar item and the selected note an 18% lavender wash — the same strength as Lavender's. The selected sidebar label is in the darkened `#5446c9` (5.0:1 on the wash) rather than the accent (3.6:1). That rule sets `-webkit-text-fill-color` as well as `color`: Standard Notes paints tag titles with `-webkit-text-fill-color: var(--navigation-item-text-color)`, which wins over `color`, so a `color` alone never reaches the screen — which is why Lavender v2.6.0's lavender label still renders in its text colour. Like the Daily view rules, they only *reference* variables, so the colour digest is unaffected — and they match Standard Notes' own class names, so they may need revisiting if the app restyles its sidebar or note list.

## What Changed vs Lavender

The base, the accent's depth, and two rules. Typography, structure, hosting and checks are Lavender's.

- **A mirrored base.** Each grey sits at the same contrast from the base as its twin, on the other side of it: background `#1e1e1e` → `#ffffff`; sidebar and surfaces `#252525` → `#f5f5f5`; borders `#2a2a2a` → `#eeeeee`; separators `#333333` → `#e0e0e0`; text `#eeeeee` → `#2a2a2a`, 14.4:1 on its base in both themes.
- **Hover a step lighter than the mirror.** Sidebar hover `#ebebeb` and note-list hover `#f2f2f2`, not the exact twins `#e8e8e8` and `#ebebeb`. A pastel wash carries less contrast than the grey it would be mirrored from, so mirrored hovers were as loud as the selection.
- **A deeper accent.** `#a79ef4` is 2.4:1 on white — fine on charcoal, too faint for links, icons and buttons on white. The accent keeps its 246° hue and deepens to `#6d61d1`, 4.9:1, level with native Light's blue (5.0:1). The darkened shade, `#5446c9`, drops HSL lightness by the same 6.9 points as in Lavender and Dark Blue.
- **White text on the accent again.** Lavender needed dark text on its pastel; `#6d61d1` takes `#ffffff` at 4.9:1 — primary buttons, the new-note button, badges, the Daily view's date tiles.
- **The same washes, from the deeper accent.** An 18% backdrop for selected rows, a 25% text-selection wash under the body text (10.3:1), a 35% scrollbar thumb.
- **Accent text on a wash uses the darkened shade** — the selected sidebar label and a Daily view day with an entry. On dark, the pastel is light enough to read on its own wash; on light, the accent isn't.
- **The selected sidebar label really is tinted.** The rule sets `-webkit-text-fill-color` too; Lavender's sets only `color`, which Standard Notes' own fill colour overrides — see [Selection](#selection).
- **Status colours are native Light's** — success `#007662`, warning `#ebad00`, danger `#cc2128` — instead of native Dark's.

As in Lavender, accessory tint 1 — the colour of the Super, plain-text and rich-text note icons, natively `#086dd6` — follows the accent, so no blue is left over. The other five tints stay native.

## Customization

Want a different lavender? Replace `6d61d1` in `dist/dist.css` with your preferred shade — without the `#`, so the translucent variants (`#6d61d12e`, `#6d61d140`, `#6d61d159`) follow it — and move `--sn-stylekit-info-color-darkened` with it.

On a light theme the accent carries text, so pick something that stays at 4.5:1 or better on white:

| Name | Hex | On white |
|------|-----|---------|
| **Lavender Light** | `#6d61d1` (default) | 4.9:1 |
| Catppuccin Latte Lavender | `#7287fd` | 3.2:1 — too light for text |
| Tailwind Violet 600 | `#7c3aed` | 5.7:1 |
| Tailwind Indigo 600 | `#4f46e5` | 6.3:1 |
| Material Deep Purple 400 | `#7e57c2` | 5.2:1 |

If you publish your own copy, the Pages workflow refuses any colour change until `EXPECTED` in `.github/workflows/pages.yml` is updated to match; the failed run prints the new digest.

## License

Theme: MIT — see `LICENSE`.
Inter: SIL Open Font License 1.1 — see `LICENSE-3RD-PARTY`.

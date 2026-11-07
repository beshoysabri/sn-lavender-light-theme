feat: Lavender Light — a light twin of Lavender

Lavender Light is Lavender v2.6.0 turned to daylight: the same stylesheet
structure, Inter setup, Daily view and selection rules, GitHub Pages
hosting and pre-publish checks, on a light palette. It gets its own
identifier, com.beshoysabri.lavender-light-theme, so it installs alongside
Lavender and Dark Blue, and pairs with Lavender under Preferences >
Appearance > Use system color scheme.

The greys are Lavender's charcoal palette mirrored: each sits at the same
contrast from the base as its dark twin, on the other side of it. Base
#1e1e1e -> #ffffff, sidebar #252525 -> #f5f5f5, borders #2a2a2a ->
#eeeeee, separators #333333 -> #e0e0e0, text #eeeeee -> #2a2a2a (14.4:1
in both). Hover greys step lighter than the exact mirror (#ebebeb in the
sidebar, #f2f2f2 in the note list): mirrored, they were as loud as the
lavender selection. Secondary text #707070 clears 4.5:1 on the sidebar.
Status colours are native Light's.

The accent can't be mirrored. #a79ef4 is 2.4:1 on white, so the solid
accent keeps its 246° hue and deepens to #6d61d1 (4.9:1, level with
native Light's blue at 5.0:1), with white text on it again. The darkened
shade is #5446c9, 6.9 HSL lightness points lower as before. The washes
come from the deeper accent: an 18% backdrop for selected rows, as in
Lavender, a 25% text selection under #2a2a2a (10.3:1) and a 35%
scrollbar thumb. Accessory tint 1 follows the accent.

Two rules change. Accent text that sits on the wash — the selected
sidebar label and a Daily view day with an entry — uses the darkened
shade: 5.0-5.4:1, where the accent would manage 3.6-3.9:1. Both still
only reference variables.

The sidebar label rule also sets -webkit-text-fill-color. Standard Notes
paints tag titles with -webkit-text-fill-color:
var(--navigation-item-text-color), which wins over color, so a rule that
sets only color never reaches the screen. Lavender v2.6.0 does exactly
that: its computed colour is lavender but the pixels are #eeeeee. Here
the label is sampled at #5446c9 in the running app.

CI: the colour digest is re-baselined to the Lavender Light palette —
still 90 declarations, still everything except the three --sn-inter-*
knobs.

Previewed in app.standardnotes.com v3.203.0 next to Lavender before
release: sidebar, note list, editor, text selection, menus, quick
settings and preferences.

Released as 2.7.0.

fix: honour the Monospace option and make the opt-ins work

Three fixes and no colour change: the 90 colour declarations still hash
to the same digest.

The Monospace Font option (Preferences > Appearance) did nothing.
Standard Notes puts .monospace-font on <html> and points .font-editor,
the note editor, at the monospace stack, but section 3's html, body,
body * rule sets Inter with !important and won. A rule after it hands
.font-editor back to the monospace face while the option is on.

The section 6 block that turns the -> arrow back off left the arrows
in place. It set only font-variant-ligatures: none, but
--sn-inter-features asks for 'calt' 1, and font-feature-settings
outranks font-variant-ligatures. The block now also takes calt out of
--sn-inter-features, and uses no-contextual so other ligatures stay.

The section 6 block for tabular figures in Super tables stopped at the
<table>: section 3 sets feature settings on every element, so the
cells' text never inherited 'tnum'. It now targets the table and
everything in it.

CI: a check that the Monospace rule is still there.

Checked in app.standardnotes.com: flipping Preferences > Appearance >
Monospace Font draws a note in the monospace face (Chrome's per-node
font report: Liberation Mono, where it was Inter), and the uncommented
arrows block leaves "a -> b" as six glyphs in the title and the editor
(five, fused, without it). The selected tag's label still samples
#5446c9.

Released as 2.7.1.

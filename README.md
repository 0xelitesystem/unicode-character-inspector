# Unicode Character Inspector

Paste or type text and get a per-character breakdown. For every character you see the glyph, its Unicode code point (U+XXXX), general category, rough block, UTF-8 byte sequence, UTF-16 code units, and the JS, HTML, and CSS escape forms. Invisible characters (zero-width, no-break space, bidi controls) and likely confusables (homoglyphs) are flagged. Single self-contained file, no external dependencies, works offline.

## Live demo

https://0xelitesystem.github.io/unicode-character-inspector/

## Features

- Per-character breakdown iterated by code point, so astral characters (emoji and other supplementary-plane characters) are handled as one character, not two
- Code point, general category, and block for each character
- UTF-8 byte sequence and UTF-16 code units (with a surrogate-pair note where relevant)
- JS (`\uXXXX` or `\u{XXXXX}`), HTML (`&#...;`), and CSS (`\XXXX`) escape forms
- Flags for invisible and format-control characters: zero-width space, zero-width joiner, no-break space, byte order mark, bidi controls, and more
- Confusable and homoglyph flags (for example Cyrillic small a that looks like Latin a)
- Summary of code-point count versus UTF-16 length
- Dark-mode toggle, keyboard usable

## How it works

The text is split with the spread operator (`[...text]`), which iterates by Unicode code point and keeps surrogate pairs together. Each character's code point is read with `codePointAt(0)`. General category is derived using Unicode property escapes in regular expressions (`\p{Lu}`, `\p{Nd}`, and so on). UTF-8 bytes are computed directly from the code point.

An honest limitation: a complete offline names database for every Unicode code point is not practical to ship in one file. This tool derives real names for ASCII and Latin printable and control characters and for a set of well-known invisible and format characters, and labels everything else by its category and block. The interface states this plainly.

## Privacy

Everything runs in your browser. The text you paste is never sent anywhere. There are no external scripts, fonts, stylesheets, or analytics. Open the page source to confirm. It works fully offline.

## License

MIT. Copyright 0xelitesystem 2026.

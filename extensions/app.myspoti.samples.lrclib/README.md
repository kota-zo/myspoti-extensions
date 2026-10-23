# LRCLIB Lyrics (sample)

Line-synced lyrics from [lrclib.net](https://lrclib.net), plain text when that is all there is.

- Provides: `lyrics`
- Network: `lrclib.net` only (the song's title, artist, album and length are sent, nothing else)
- Setting: "Plain lyrics too" (on by default) also gives lyrics without times.

It asks LRCLIB's exact match first, then its search. It answers `null` when nothing is found, so
Myspoti's own lyrics sources answer instead.

This is also the reference example for authors: see the
[API documentation](https://github.com/kota-zo/myspoti/blob/main/docs/extensions/API.md).

License: GPL-3.0 (see `LICENSE`).

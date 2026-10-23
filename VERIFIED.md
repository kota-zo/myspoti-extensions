# Verified extensions (optional, the owner's choice)

`index.json` lists the extensions the owner chose to call **verified**. It is empty and may stay
empty: nothing here is required for an extension to be found (that is the topic
`myspoti-extension`) or installed. Myspoti shows this repository in its store only when `index.json`
lists at least one extension; a verified extension is the owner's reading of the code at one
moment, not a guarantee (see [POLICY.md](POLICY.md)).

## Adding one

Only the owner does this, after reading the extension's code in its own repository. Add an entry to
`extensions` in `index.json`. Easiest: build the package with the desktop runner and copy the entry
it prints:

```
myspoti-ext pack path/to/the/extension
```

For an extension installed from its GitHub release, use this shape (the app reads the release's
`extension.zip`, and keeps it updated from there):

```json
{
  "format": 1,
  "name": "Myspoti verified extensions",
  "extensions": [
    {
      "id": "io.github.someone.name",
      "name": "Name",
      "version": "1.0.0",
      "versionCode": 1,
      "author": "Someone",
      "description": "One sentence.",
      "actions": [ { "name": "lyrics.provide", "why": "Synced lyrics" } ],
      "repo": "someone/name",
      "url": "https://github.com/someone/name/releases/latest/download/extension.zip",
      "sha256": ""
    }
  ]
}
```

- `actions` is copied from the extension's manifest, so the store shows the rights before download.
- `sha256` empty: whatever the newest release holds is installed. To pin the exact package that was
  read, put its sha256 there (then a new release has to be added here again).
- The fields are those of the API documentation, "How an extension reaches people":
  [docs/extensions/API.md](https://github.com/kota-zo/myspoti/blob/main/docs/extensions/API.md).

## Removing one

Delete its entry. To also turn it off on phones, add it to `blocked.json` (see
[README.md](README.md)).

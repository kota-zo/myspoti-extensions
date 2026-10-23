# Myspoti extensions

The home of the rules around [Myspoti](https://github.com/kota-zo/myspoti)'s extensions: small
JavaScript programs that Myspoti runs in a sandbox (lyrics sources, Home sections, menu entries,
reactions to the song playing, access to your Spotify account). **This repository does not host
extensions.** Anyone publishes theirs in their own GitHub repository.

Myspoti does not host, review or endorse third-party extensions. Each one is under its author's
responsibility, and what it may do is what its manifest asks and you accept when installing it.

## How extensions are found

Myspoti's store searches GitHub for public repositories with the topic **`myspoti-extension`**,
reads each one's `manifest.json`, and lists them (ratings and downloads included). Nothing has to be
submitted or approved here.

You can also install from an address (`https://github.com/you/name`) or add another repository's
`index.json`, at your own risk.

## Publish your extension

Use the template: **[kota-zo/myspoti-extension-template](https://github.com/kota-zo/myspoti-extension-template)**
("Use this template", rename the id, edit the manifest, add the topic `myspoti-extension`, push a
`vX.Y.Z` tag). The authors' documentation (manifest, actions, hooks, the desktop runner
`myspoti-ext`) is
[docs/extensions/API.md](https://github.com/kota-zo/myspoti/blob/main/docs/extensions/API.md).
Read [POLICY.md](POLICY.md) first: it lists what is not allowed.

## Report an extension

Malware, credential theft, a stolen extension, a copyright or legal notice: see
[REPORTING.md](REPORTING.md). The **Report** button on an extension's page in Myspoti opens the
report form of this repository with the extension's id, version and source already filled in.
Contact: myspoti.app@gmail.com.

## What is in this repository

```
README.md, POLICY.md, REPORTING.md   the rules and the procedure
.github/ISSUE_TEMPLATE/              the report and copyright-notice forms
blocked.json                         the kill switch Myspoti reads once a day
index.json                           the optional list of "verified" extensions (see VERIFIED.md)
```

### `blocked.json` (for the owner)

Myspoti reads `https://raw.githubusercontent.com/kota-zo/myspoti-extensions/main/blocked.json` once
a day. A `blocked` extension is turned off on every phone with its `reason` shown, and cannot be
turned on, installed or reverted to. A `flagged` one (reported and confirmed) stays installed but
is hidden from the store behind "Show all". To add one, edit the file on `main`:

```json
{
  "blocked": [
    { "id": "io.github.someone.name", "reason": "Steals Spotify cookies (issue #12)" },
    { "id": "io.github.other.name", "sha256": ["<64 hex of one package>"], "reason": "Removed after a copyright notice (issue #15)" }
  ],
  "flagged": [
    { "id": "io.github.third.name", "reason": "Reported for undeclared tracking, under review" }
  ]
}
```

Without `sha256`, every version of the id is blocked; with it, only the packages listed. The
`reason` is shown to people: say what happened, without insulting anyone. The file must stay valid
JSON with exactly these two lists: a file Myspoti cannot read is ignored until it is fixed.

## License

The documents and forms in this repository are GPL-3.0, like Myspoti: see [LICENSE](LICENSE). Each
extension carries its own license in its own repository.

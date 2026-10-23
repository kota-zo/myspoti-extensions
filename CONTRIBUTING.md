# Contributing an extension

Extensions are added to this repository by pull request, one extension per pull request. A
maintainer reads the code before it is merged: the review is the point of the official
repository. Read [POLICY.md](POLICY.md) first, it lists what is never accepted.

The authors' documentation (manifest, hooks, permissions, the `myspoti` object, limits) is
[docs/extensions/API.md](https://github.com/kota-zo/myspoti/blob/main/docs/extensions/API.md) in
the Myspoti repository.

## Adding one

1. Fork this repository and create `extensions/<id>/`. The folder is named after the extension's
   `id` (reverse-domain, lower case: `io.github.you.lyrics`).
2. Put in it, and nothing else:
   - `manifest.json` and the script named by `main` (default `main.js`), no minification or
     obfuscation: the reviewer must be able to read it. One file, 1 MB at most.
   - `README.md`: what it does, which hosts it calls and what it sends them, what each right is
     used for.
   - `LICENSE`: the license of your code (any license that lets the repository host and Myspoti
     users run it).
   - `icon.png` (optional): a square PNG, 256 px or less, 256 KB at most.
3. Try it on your computer with the desktop runner (`myspoti-ext check ./extensions/<id>`, then
   `myspoti-ext run ...`), see the API documentation, section "Testing on a computer".
4. Run `python3 scripts/build_index.py`. It validates the manifest with the same rules as the app,
   builds `dist/<id>-<version>.zip`, and rewrites `index.json` and the table in `README.md`.
   Commit all of it. The pull request check runs the same script and fails if anything is stale.
5. Open the pull request. Say what the extension is for and answer the reviewer's questions.

## Rules the manifest must follow

- **Network hosts are precise.** List the hosts the extension really calls (`api.example.com`).
  `*.example.com` only if it really uses several subdomains of one domain. `"*"` (any host) is
  accepted only when the feature cannot work otherwise (for example a user-chosen server), and
  needs a clear `why`.
- **Every sensitive right needs a `why`** in plain words, written for the person installing, 15
  characters or more: the takeovers `audio-source` and `download-source`, `player.read`,
  `player.control`, `spotify.library.read`, `spotify.write`, `spotify.raw`, and `network` with
  `"*"`. The reviewer checks that the code needs each right and does not use it for anything else.
  Ask for the least you need: `spotify.raw` only when the typed methods cannot do it.
- `author` is the real name or handle of the person or group responsible, and `homepage` is where
  people can reach you (an issue tracker or repository), so a problem can be reported.
- `description` says what it does in one or two sentences, without marketing.

## Versions

- `version` is shown to people (`1.2.0`), `versionCode` is compared by the app: an integer that
  only goes up. **Every change to an extension needs a higher `versionCode` and a new `version`**,
  even a typo in the script.
- A published package never changes. `build_index.py` refuses to overwrite an existing
  `dist/<id>-<version>.zip`, and on pull requests the check compares with `main`: a changed
  package with the same `versionCode` fails.
- `index.json` lists the newest version of each extension. Older packages stay in `dist/` (a
  report may name one by hash).
- `id` never changes.

## Updating and removing

- Update: change the files in `extensions/<id>/`, bump `version` and `versionCode`, run the script,
  open a pull request. A change that adds a right or a host is reviewed again in full, and users
  are asked again by the app.
- Removal at the author's request: a pull request that deletes the folder (and the index entry
  with it). To also turn off installed copies, add the id to `blocked.json`.
- The maintainers remove or block an extension that breaks [POLICY.md](POLICY.md): see
  [REPORTING.md](REPORTING.md).

## Review checklist

The reviewer goes through this before merging:

- [ ] The folder, `id`, `author` and `homepage` are coherent; the extension is not named like, or
      presented as, someone else's product.
- [ ] `build_index.py` passes; only the extension's own files, `dist/`, `index.json` and the
      `README.md` table changed.
- [ ] The script is readable, with no obfuscation, no `eval`-style loading of remote code, and does
      what its README says.
- [ ] Each host is needed, and the data sent to it is what the README says (no identifiers, no
      Spotify tokens or cookies, no listening history to a third party unless that is the
      declared purpose and the `why` says it).
- [ ] Each right is needed and each sensitive `why` is honest and understandable.
- [ ] `spotify.write` and `spotify.raw` calls only act on what the user asked for.
- [ ] Nothing in [POLICY.md](POLICY.md) is broken: no circumvention of access controls or DRM, no
      unauthorized copyrighted downloads, no other people's accounts or credentials, no fake
      playback or stream reports, no malware, no tracking.
- [ ] The license is present and the code is the author's own or used under its license.
- [ ] For an update: `versionCode` went up, and the diff matches the described change.

## Conduct

Be direct and civil. Maintainers decide what is listed and may refuse an extension without
detailed justification beyond the policy.

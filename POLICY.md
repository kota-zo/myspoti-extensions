# Extension policy

Myspoti runs extensions that anyone publishes in their own GitHub repository. **Myspoti and the
maintainers of this repository do not host, review, audit or endorse third-party extensions.** An
extension is the work and the responsibility of its author. It runs in a sandbox and can only do
what its manifest asks and the user accepted, but a sandbox is not a guarantee, and the user
remains responsible for what they install.

## Not allowed

An extension must not:

1. **Circumvent DRM or access controls**: decrypt protected streams, bypass paywalls, subscription
   tiers, geographic restrictions or rate limits, or defeat any technical measure that restricts
   access to a work or a service.
2. **Facilitate piracy**: download, stream or share copyrighted content without the right holders'
   authorization, or point its `audio-source` or `download-source` at sources that distribute works
   that way. Sources that are licensed, free by their rights holders' choice, or owned by the user
   are fine, and its README must say which.
3. **Use other people's accounts or credentials**: shared, stolen or scraped logins, tokens or
   cookies, or any access to an account its owner did not give to the user.
4. **Steal credentials or data**: collect passwords, tokens, cookies, the library, the profile or
   anything played and send it anywhere the user was not told, or sell or share it.
5. **Fake playback or stream reports**: inflate plays, simulate listening, or send counts or events
   that did not happen, for anyone's statistics or royalties.
6. **Be malware**: hide what it does, load code from elsewhere to run it, obfuscate its behavior,
   damage the user's account (mass unfollow or deletion nobody asked for) or abuse the user's
   device or network.
7. **Impersonate**: present itself as made or endorsed by Spotify, Myspoti or another party that did
   not make it, or copy another author's work against its license.
8. **Be unlawful in another way**: harassment, content that is illegal to host, or anything that
   cannot lawfully be distributed.

A manifest that asks for rights the code does not need, or a `why` that misleads, is also a breach.

## Takedown

Anyone can report an extension (see [REPORTING.md](REPORTING.md)). On a valid report, or a valid
legal notice, the maintainers may, at their discretion and without prior notice to the author:

- add the extension to `blocked.json`, so Myspoti turns it off on every phone with the reason
  shown and refuses to install it;
- add it to `flagged`, so Myspoti's store hides it;
- remove it from `index.json` if it was listed as verified.

The maintainers cannot delete or edit a repository they do not own: they only act on what Myspoti
shows and runs. A block or a flag is not a judgment of the author, and may be lifted when the
problem is fixed or a counter-notice is accepted ([REPORTING.md](REPORTING.md)). Nobody has a right
to be listed, found or kept on any phone.

## No warranty

Extensions are provided by their authors "as is". Myspoti and the maintainers give no warranty
about them and are not liable for what an extension does, to the extent the law allows.

## Verified extensions

An extension in `index.json` is one the owner chose to list as verified (see
[VERIFIED.md](VERIFIED.md)). Even then it is a reading of the code at one moment, not a guarantee.

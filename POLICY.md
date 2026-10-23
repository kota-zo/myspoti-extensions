# Extension policy

This repository lists extensions that people install into Myspoti. What is listed here is
reviewed, but a review is a reading of the code, not a guarantee: an extension runs in a sandbox
and can only do what its manifest asks and the user accepted, and the user remains responsible for
what they install.

## Not accepted

An extension is refused, or removed and blocked, if it:

1. **Circumvents DRM or access controls**: it decrypts protected streams, bypasses paywalls,
   subscription tiers, geographic restrictions or rate limits, or defeats any technical measure
   that restricts access to a work or a service.
2. **Downloads copyrighted content without authorization**: its `audio-source` or
   `download-source` points at sources that distribute works without the right holders'
   permission. Sources that are licensed, free by their rights holders' choice, or owned by the
   user are fine, and the README must say which.
3. **Uses other people's accounts or credentials**: shared, stolen or scraped logins, tokens or
   cookies, or any access to an account its owner did not give to the user.
4. **Fakes Spotify playback or stream reports**: it inflates plays, simulates listening, sends
   counts or playback events that did not happen, or helps an artist or a listener manipulate
   statistics or royalties.
5. **Is malware**: it steals data, hides what it does, loads code from elsewhere to run it,
   obfuscates its behavior from the reviewer, damages the user's account (for example mass
   unfollow or deletion nobody asked for) or abuses the user's device or network.
6. **Tracks people**: it collects what is played, the library, the profile or any identifier and
   sends it anywhere other than what its README declares and the user's `why` shows, or sells or
   shares it.
7. **Impersonates**: it presents itself as made or endorsed by Spotify, Myspoti or another party
   that did not make it.
8. **Is unlawful in another way**: harassment, content that is illegal to host, or anything a
   maintainer cannot lawfully distribute.

Also refused: a manifest that asks for rights the code does not need, or a `why` that misleads.

## Review

A pull request is read before it is merged. Maintainers may ask questions, ask for changes, or
refuse. There is no deadline for a review and no right to be listed. Updates are reviewed too: a
bump is not a free pass.

## Removal

An extension is removed when it breaks this policy, when a valid notice requires it (see
[REPORTING.md](REPORTING.md)), when it is abandoned and broken, or when its author asks.

Removal means: the folder is deleted, the entry leaves `index.json`, and the id (all versions, or
the packages named by their hash) goes into `blocked.json` with a reason. Myspoti reads that list
and turns the extension off on every installation, with the reason shown. The package files of
past versions may be kept in the history of the repository.

An author may reply to a removal by opening an issue. A maintainer reviews it again; a copyright
removal follows the counter-notice procedure in [REPORTING.md](REPORTING.md).

## Unofficial repositories

Anyone can host another repository and a user can add it at their own risk. This policy covers
only this repository. A repository's `blocked` list is read for that repository only.

# Reporting an extension

**Contact:** myspoti.app@gmail.com. It receives reports, legal notices (DMCA, DSA and any other)
and counter-notices. Do not put secrets or personal data in a public issue: email instead.

The fastest way for an extension you see in Myspoti is the **Report** button on its page: it opens
the form below with the extension's id, version, source repository and package hash already
filled in (nothing about you is sent).

## 1. A malicious or abusive extension

Open a [report](../../issues/new?template=report-extension.yml) (or email) with the extension id and
version, what it does and how you saw it (file and line, behavior, a network capture). The
maintainers check it against [POLICY.md](POLICY.md).

- Active harm (credential theft, data exfiltration, destructive actions): the extension is added to
  `blocked.json` as soon as the maintainers confirm it, without waiting for the author.
- Other breaches: the maintainers may flag it (hidden from the store) and, where it is reasonable,
  give the author time to fix it.
- The reporter is told what was decided. A vulnerability in Myspoti itself: email, not an issue.

## 2. Copyright, DMCA and DSA notices

If you hold rights in a work and an extension infringes them (it downloads or streams your work
without authorization, circumvents protection, or copies your code), send the
[copyright notice form](../../issues/new?template=copyright-notice.yml) or email the same
information. The form is public: to keep your name and details private, email.

Myspoti does not host or distribute any extension or any music: extensions live in their authors'
own repositories. The maintainers can only have Myspoti turn an extension off and hide it
(`blocked.json`); for removal of the material itself, also send your notice to the repository's
host (GitHub) and the author.

A notice must contain:

1. The identity and contact details of the **rights holder** (or the person authorized to act for
   them), and which right they hold.
2. The identification of the **work** infringed (title, where the original is, or proof of
   ownership).
3. The identification of the infringing material: the **extension id and version** and where in it
   (file and lines, or the URL it points to), so it can be found.
4. A statement of **good faith** that the use is not authorized by the rights holder, their agent or
   the law.
5. A statement, **under penalty of perjury where the law of the notice requires it**, that the
   information is accurate and that the signer is the rights holder or authorized to act for them.
6. A physical or electronic **signature**.

An incomplete notice may be answered with a request for what is missing before anything is done.

### What happens

- **Acknowledgment** within 7 days of a complete notice (or the request for what is missing).
- **Action**: if the notice is complete and the material infringes on its face, the maintainers add
  the extension to `blocked.json` (reason: "blocked after a legal notice"), in most cases within 7
  days of the acknowledgment, and tell the author, with the notice.
- **No action**: if the notice is not valid or the material is not infringing, the notifier is told
  why.
- Anyone who knowingly sends a false notice can be held responsible for the damage it causes.

### Counter-notice

The author of a blocked extension can answer with a
[report form](../../issues/new?template=report-extension.yml) (choose "Counter-notice") or by email. It
must contain: their name and contact details, the extension id, a statement under penalty of
perjury (where applicable) that the block was a mistake or a misidentification, why the extension
does not infringe (license, permission, exception), their consent to the jurisdiction that applies,
and a signature.

The maintainers send it to the notifier. If the notifier does not say, within 10 to 14 working
days, that they started a legal action, the extension may be unblocked. A decision can also be
contested through the means the law of the notifier's country gives (in the European Union, the
Digital Services Act's complaint and out-of-court dispute settlement), and the maintainers state
the reasons of their decisions to those concerned.

### Repeat infringers

An author who is the subject of repeated valid notices can have all their extensions blocked.

## 3. What this document is not

A good-faith procedure for a small volunteer project, not legal advice. The maintainers act under
the law that applies to them.

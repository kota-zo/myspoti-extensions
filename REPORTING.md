# Reporting an extension

Use the issue forms of this repository. Do not put secrets in a public issue; for something that
cannot be public (a vulnerability, personal data), email the contact below instead.

**Designated contact:** `CONTACT_EMAIL_TBD`
(placeholder: it will be replaced by the address that receives notices, this repository's
designated contact point for notices and reports.)

## 1. A malicious or abusive extension

Open a [report](../../issues/new?template=report-extension.yml) with the extension id and version,
what it does and how you saw it (code line, behavior, network capture). Reports are read by the
maintainers, who check the code against [POLICY.md](POLICY.md).

- Active harm (credential theft, data exfiltration, destructive actions): the extension is
  blocked as soon as the maintainers confirm it, without waiting for the author.
- Other breaches: the author is told and gets a reasonable delay to fix it, unless the report is
  clear and serious enough to block first.
- The reporter is told what was decided. Reporters are not asked to prove more than a reasonable
  reading of the code shows.

## 2. Copyright, DMCA and DSA notices

If you hold rights in a work and an extension in this repository infringes them (for example it
downloads or streams your work without authorization, or it copies your code), send a notice with
the [copyright notice form](../../issues/new?template=copyright-notice.yml), or by email to the
contact above. The form is public: if you do not want your name and details on a public issue,
send the same information by email.

A notice must contain:

1. The identity and contact details of the **rights holder** (or the person authorized to act for
   them), and which right they hold.
2. The identification of the **work** infringed (title, where the original is, or proof of
   ownership).
3. The identification of the infringing material: the **extension id and version** and where in
   it (file and lines, or the URL it points to), so it can be found.
4. A **statement of good faith** that the use is not authorized by the rights holder, their agent
   or the law.
5. A statement, **under penalty of perjury where the law of the notice requires it**, that the
   information is accurate and that the signer is the rights holder or authorized to act for them.
6. A physical or electronic **signature**.

A notice that lacks these, or whose request is not about material hosted here, may be answered
with a request for the missing information before anything is done.

### What happens

- **Acknowledgment** within 7 days of a complete notice (or the request for what is missing).
- **Action**: if the notice is complete and the material infringes on its face, the maintainers
  remove it expeditiously, in most cases within 7 days of the acknowledgment: the folder is
  deleted, the id goes into `blocked.json` (with the reason "removed after a copyright notice")
  so installed copies are turned off, and the author is told, with the notice.
- **Not removed**: if the notice is not valid, or the material is not infringing, the notifier is
  told why.
- Anyone who knowingly sends a false notice can be held responsible for the damage it causes.

### Counter-notice

The author of a removed extension can answer with the
[counter-notice](../../issues/new?template=report-extension.yml) (select "Counter-notice") or by email.
It must contain: their name and contact details, the extension id, a statement under penalty of
perjury (where applicable) that the removal was a mistake or a misidentification, why the
extension does not infringe (license, permission, exception), their consent to the jurisdiction
that applies, and a signature.

The maintainers send the counter-notice to the notifier. If the notifier does not tell, within 10
to 14 working days, that they started a legal action, the extension may be restored (the folder
returns, the id leaves `blocked.json`). A decision can also be contested through the means that
the law of the notifier's country gives (for the European Union, the Digital Services Act's
complaint and out-of-court dispute settlement), and the maintainers state the reasons of their
decisions to those concerned.

### Repeat infringers

An author who is the subject of repeated valid notices can be refused further extensions.

## 3. What this document is not

This is a good-faith procedure for a small volunteer repository, not legal advice. The
maintainers act under the law that applies to them. Myspoti does not host, stream or distribute
any music itself.

## For maintainers: removal and blocking

1. Delete `extensions/<id>/` (and the matching `dist/*.zip` if the package itself is the problem).
2. Add to `blocked.json`:
   ```json
   [
     { "id": "io.github.someone.name", "reason": "Removed after a copyright notice (issue #12)" }
   ]
   ```
   With `"sha256": ["<64 hex>"]` only the packages named are turned off (all versions if empty).
   A reason is required: the user sees it.
3. Run `python3 scripts/build_index.py` and commit the result. The `blocked` list in `index.json`
   is read by every Myspoti that uses this repository, and the app disables listed ids.

# email-corpus

A public corpus of redacted spam, scam, and phishing emails for security research, awareness training, and classifier development.

All emails are real-world samples. Contributor PII has been redacted and URLs have been defanged before publication.

---

## Intended usage

This corpus is intended for:

- **Security awareness teams** — realistic phishing samples for training
  campaigns, without handling live malicious content
- **Researchers** — studying how threat actors craft emails: subject lines,
  sender spoofing, urgency tactics, HTML structure, lure techniques
- **Developers** — building and evaluating spam/phishing classifiers with
  labelled real-world samples
- **Educators** — illustrating phishing techniques in a safe, controlled format

This corpus is **not** intended as a live threat intelligence feed. URLs are
defanged and routing headers are stripped — the samples are for analysis, not
for direct import into blocking tools.

---

## What's in here

Each sample is a redacted `.eml` file. Per sample:

- Routing headers (`Received:`, `Return-Path:`, etc.) are stripped
- Contributor email address and name variants are replaced with
  `redacted@redacted.com` / `redacted`
- URLs in body text are defanged (`hxxps://`, `[.]` notation)
- Email structure, HTML lure, and attachments are otherwise preserved

---

## Structure

```
submissions/
  <addr-hash>/        <- opaque contributor ID, no PII
    <version>/        <- tool version that produced these outputs
      emails/
        <sha256>.eml  <- redacted sample
```

---

## Disclaimer

These samples are provided **as-is** for research and educational purposes
only. No warranty is made as to completeness, accuracy, or fitness for any
particular purpose.

- **Redaction is best-effort.** Despite automated redaction and manual
  verification, residual PII may remain. Do not use these samples to identify
  or contact any individual.
- **Defanging is not sanitisation.** URLs are defanged for display safety but
  the underlying domains and paths are preserved. Do not re-fang and visit URLs
  without appropriate precautions.
- **Attachments are preserved.** Some samples may contain attachments (e.g.
  calendar invites). No executables, Office documents, or PDFs are knowingly
  included, but exercise caution when opening samples.
- **Use responsibly.** Do not use these samples to train models intended for
  malicious purposes, to harass individuals, or for any unlawful activity.

---

## Reporting issues

If you find any of the following, please open a GitHub issue:

- **Residual PII** — contributor name, email address, or other personal
  information that was not redacted
- **Malicious attachments** — executables, Office documents, PDFs, or other
  potentially harmful file types
- **Other concerns** — anything that should not be in a public corpus

---

## Tool

Samples are processed using
[eml-contrib-ng](https://github.com/cw-l/eml-contrib-ng).
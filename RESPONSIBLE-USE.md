# Responsible use of voice cloning in Glaze

Glaze can make a synthetic voice from a recording of a real person. That
is useful — for narration, for accessibility, for hearing your own drafts
read back. It is also the kind of capability that gets misused, and no
amount of local-first architecture changes that.

This document says what Glaze does about it, what it does not do, and what
is left to you. It is deliberately short, because a policy nobody reads
protects nobody.

## The one rule

**Clone your own voice, or a voice you have permission to clone.**

Everything below follows from that.

## What you may do

- Clone your own voice.
- Clone someone else's with their informed permission — they know it is
  being cloned, and what for.
- Use voice material you have the rights to: licensed, public domain, or
  your own recordings.
- Build things: narration, audiobooks, drafts read back to you, game
  dialogue, accessibility tools for people who have lost their voice.

## What you may not do

- Impersonate anyone without permission — including public figures.
- Fraud, scams, or defeating voice authentication.
- Harassment, intimidation, or sexual content involving a real person's
  voice.
- Putting words in someone's mouth about politics, law, money, health, or
  an emergency.
- Commercial use of a person's voice without the right to it.

If you publish synthetic speech, say that it is synthetic wherever the law,
the platform, or plain decency requires it.

## What Glaze does technically

**Everything stays on your machine.** Recording, training and synthesis
all run locally. Your voice data is never uploaded — not for cloning, not
for improvement, not at all. The only network call Glaze makes on its own
is the update check, and you can turn that off.

**Every generated file carries a watermark.** Glaze applies
[Perth](https://github.com/resemble-ai/perth) to all synthesized audio, on
both engines: the trained (Chatterbox) path watermarks in the engine, and
the instant (Qwen) path is watermarked by Glaze. Measured with Perth's own
detector: synthetic output from both paths scores 1.000, a genuine human
recording scores 0.000. The mark is inaudible and survives ordinary
re-encoding; it is not a lock, and someone determined to strip it can. It
exists so that audio made here can be *identified* as made here.

## What Glaze does not do

**There is no consent checkbox, and no upload of your voice for
verification.** Glaze cannot tell whose voice a recording contains, and a
checkbox asserting otherwise would be theatre — it would stop nobody and
imply a check that never happened. Verification would mean sending voice
data somewhere, which is the one thing this product promises not to do.

So the honest position is the one above: the software will do what you
ask, and the responsibility for whose voice you ask it to imitate is
yours. Not a shared responsibility, and not one the tool quietly assumes
on your behalf.

**Glaze does not police your output.** Nothing is scanned, reported, or
sent for review, because nothing leaves your machine to scan.

## If you are building on Glaze

The REST API and the voice library are the same capability without the
wizard's guardrails. Consent, disclosure and jurisdiction are part of
*your* product's design; inheriting Glaze's privacy model does not
inherit anyone's permission.

## Reporting misuse

If you find Glaze being used to impersonate someone, report it to the
platform hosting the audio — that is where it can actually be taken down.
Glaze itself has no server to report to and no account to suspend.

<!-- TODO(jakob): a contact address for security + misuse reports. There
     is none anywhere in the project today, and inventing one here would
     be worse than leaving the gap visible. -->
For a security problem in Glaze, contact the maintainer through the
project's repository.

---

*Last reviewed 2026-09-06. The watermark claims above were verified by
measurement on that date, not assumed; see `glaze_tts/instant.py`.*

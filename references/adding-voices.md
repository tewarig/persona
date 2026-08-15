# Adding a voice

The guided flow for `/persona add <name>` — building a new persona properly with the user, then keeping it.

Use this when someone wants a voice that doesn't exist yet and wants it to *last*. For a one-off ("just talk like a pirate for a minute"), skip all of this and derive on the spot from `voice-spec.md`.

## Contents

- The interview
- Why the quote question matters
- Two sets: training and test
- Build
- The verification test
- Save
- Then adopt it
- Contributing it back

## The interview

Ask all of it in **one message**. A guided flow that asks three questions across three turns is an interrogation, not a conversation.

> Three things and I'll build it:
>
> 1. **Who?** Name, and if they're not famous, where I can find them talking.
> 2. **A line of theirs you love** — a quote, a scene, a moment. Doesn't need to be exact.
> 3. **What do you want it *for*?** Debugging, writing, explaining things, or just for fun?

If they can't name a quote, don't push — ask what they like about how the person talks instead. Same signal, different door.

Question 3 matters more than it looks. A voice for debugging needs a manner that handles failure well. A voice for writing needs rhythm. The same person specced for different jobs comes out different.

## Why the quote question matters

It is not just source material. **It tells you which version of the person they want.**

Every well-known figure has several. Someone who loves Rick's nihilism speech wants a different Rick than someone who loves the therapy monologue — the first wants cosmic contempt, the second wants the wounded man underneath. Same character, different centre of gravity, and a spec can only have one.

The quote they reach for first is the one that made them care. Build toward that.

## Two sets: training and test

Collect both, and never confuse them.

| | Where it comes from | What it's for |
| :--- | :--- | :--- |
| **Training set** | Long interviews, podcast transcripts, per-episode dialogue — them being ordinary and unedited | Filling the axes. This is where rhythm, stance and manner actually live |
| **Test set** | The famous lines. Quote pages and listicles are fine *here* | Checking the finished spec. Never for building it |

This is the one rule people get backwards. Famous quotes are the polished, atypical, heavily-edited moments — the least representative thing a person ever said. Build from them and you get a keyword generator, which is failure mode 1 in `calibration.md`.

But they are excellent for verification, because they are the lines everybody already knows are *right*.

See `unknown-voices.md` for how to search for each — the query patterns differ.

## Build

Fill all fourteen axes before writing a single line in the voice:

- The eight voice axes from `voice-spec.md`, plus an anchor line
- The six manner axes from `manner.md`, via its five questions

Weight the build toward whatever the user's chosen quote pointed at. If they picked something warm, the stance is warm — even if the character is better known for being cruel.

## The verification test

Now use the test set. For each famous quote you found, ask:

> **Could the spec I just wrote have produced this line?**

Not "does my spec contain this line" — it shouldn't. The question is whether a person built from these axes would plausibly say that.

- **Yes, all of them** — the spec is good. Proceed.
- **Yes, most** — good enough. Note which ones don't fit; usually they're from a different era or a different mood, and that's real.
- **No** — the spec is wrong, and it's almost always **stance** (voice axis 4) or **friction** (manner axis 5). Re-derive those two before touching anything else.

This is a genuinely strong check, and it costs nothing — you already have the quotes and the spec.

Then show the user **one** anchor line of your own, on a mundane topic, and ask "is this them?" One line, not a menu. Their correction at this moment is worth more than another hour of research.

## Save

Write to `personas/<name>.md`: the fourteen axes, the anchor, the quote they picked and why it shaped the spec, and every correction they made along the way.

Saved voices override library entries of the same name, so a user can keep their own Rick without touching the shipped one.

`personas/*.md` is gitignored. Their voices stay theirs.

## Then adopt it

**Building a voice ends with wearing it.** Confirm the save in one line, then switch into the voice for the rest of that same reply and keep it for the session, exactly as if they had run `/persona <name>`.

Do not hand back a file and wait to be asked. Someone who just spent a turn answering three questions and reviewing an anchor line wants the voice, not a filepath — stopping at "saved!" is the single most disappointing way to end this flow.

If their answer to "is this them?" was a correction rather than a yes, apply it, save again, and adopt the corrected version. Still in the same reply.

## Contributing it back

If a voice turns out well and the person is one other people would want, offer it:

> This one's good. Want to send it upstream? It'd need the research trail — where the material came from — and it'd ship with the skill.

The bar for the shipped library is deliberately high: **built from real sources, not from assumption.** Nine entries were cut for failing exactly that test. A thin guessed spec is worse than no spec, because it hands someone a confident wrong impression instead of sending them here to build a real one.

What a contributed entry needs:

- The eight voice axes and a **Manner** line
- An **invented** anchor — never a real quote presented as the tuning fork
- Sourced quotes kept clearly separate and marked as genuine
- For real people: parody as the register, no fabricated statements

Then a PR against `references/library.md`, entry added to the Contents list.

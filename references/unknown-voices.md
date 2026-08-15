# Voices you don't know

Read when the requested name isn't in `library.md` or `personas/`, and you don't have a confident sense of how they actually talk.

**Never guess and never fake familiarity.** A confident wrong impression is worse than asking. Every path below beats improvising.

## Contents

- Pick a path
- Path A: research the real speech
- Path B: ask for raw material
- Path C: derive from files on disk
- Path D: nearest neighbor plus deltas
- Path E: construct from the description
- The confirm loop
- Saying what you don't know
- Save what you built

## Pick a path

| What you have | Path |
| :--- | :--- |
| A public figure with a real record — interviews, videos, transcripts | **A** research |
| A private person — their coworker, their friend, a small creator | **B** ask |
| The user themselves, or their team's house style | **C** files |
| Someone you half-know, or who fits a recognizable type | **D** neighbor + deltas |
| An invented character — "a Victorian butler who disapproves of your architecture" | **E** construct |

Paths combine. Research a figure, find three usable clips, and fill the gaps with a neighbor archetype. That's normal.

## Path A: research the real speech

If web search is available, use it. One rule governs everything here:

> **Search for ordinary speech, not famous quotes.**

Famous quotes are the worst possible material for a voice. They're the polished, atypical, heavily-edited moments — and building from them produces exactly the catchphrase soup that `calibration.md` calls failure mode 1. You want them being boring: explaining something, being interrupted, answering a dull question. That's where rhythm and stance live.

**Query patterns that work:**

```
"<name>" interview transcript
"<name>" podcast transcript full
"<name>" answering questions subtitles
"<name>" press conference transcript
<character name> wiki quotes <episode>       ← fandom wikis often log full dialogue
```

**Query patterns that waste a search:**

```
"<name>" best quotes            ← listicles, catchphrases only
"<name>" catchphrases           ← the trap
"<name>" personality analysis   ← descriptions of speech, not speech
```

| Source | Value |
| :--- | :--- |
| Long interview or podcast transcripts | Best. Unedited, conversational, covers dull topics |
| Fandom wikis with per-episode dialogue | Very good for fictional characters |
| Subtitle and script archives | Good, but stage directions aren't speech |
| Reddit or forum threads quoting them at length | Decent, verify against another source |
| Quote listicles | Near worthless for this purpose |

**How much is enough:** roughly ten unedited sentences on at least two different topics. Two topics matter more than ten sentences — one topic gives you their subject-matter vocabulary and hides their actual rhythm.

**Then extract, don't copy.** Read the samples and fill the eight axes in `voice-spec.md` from them. Pay attention to what the samples show that a description never would: how long their sentences run, whether they finish them, how they open, how they handle a question they don't like. Write an anchor line of your own — invented, on a mundane topic — and check it against the samples.

Do not reproduce long verbatim passages in the reply. You're extracting a pattern, not quoting a source.

## Path B: ask for raw material

For anyone without a public record, one short question beats ten minutes of inference. Ask in plain voice, once:

> I don't know how they talk. Paste 5–10 lines of them — messages, an email, anything unedited — and I'll build it from that.

**What's useful:** unedited conversational text, ideally them explaining something or disagreeing with someone. Voice notes transcribed. A link to a transcript page.

**What isn't:** their formal writing, anything ghostwritten, a description of their personality, a single one-liner. And note that you can't watch video or listen to audio — a link to a clip needs a transcript page instead.

Three real sentences from them beat any assumption you could make.

## Path C: derive from files on disk

For "talk like me," "match our docs," or "write PRs the way our team does." The material is already there:

```bash
git log --author="<name>" --pretty=format:'%s%n%n%b' -n 40
```

Also useful: their notes, their existing PR descriptions, a docs directory, an exported chat log. Read what's there, fill the axes, write the anchor line.

This is the highest-value path in the whole skill and the one users don't think to ask for. When drafted text stops sounding like an assistant and starts sounding like them, that's this path. Offer it whenever someone asks for "a more natural tone" without naming a person.

## Path D: nearest neighbor plus deltas

For someone you half-know, or who fits a recognizable type — a Scottish football manager, a 90s radio DJ, a Chennai auto driver, a startup founder on stage.

1. Name the closest voice you *do* know well, from the library or elsewhere
2. Write the deltas explicitly — *older, warmer, no profanity, switches to Tamil when annoyed*
3. Apply deltas to the axes one at a time, hardest on stance (axis 4) and negative space (axis 8)

State the construction to the user in one line: "Building this off the noir spec with the cynicism dialled down — tell me what's off." That invites the correction that fixes it, instead of leaving them to wonder why it sounds wrong.

The user's own request often contains the deltas already. "Like Rick but Indian and less mean" is a complete instruction — neighbor plus two deltas.

## Path E: construct from the description

For characters that don't exist, the description *is* the seed, and every word in it is load-bearing. "A Victorian butler who disapproves of your architecture" gives you:

- *Victorian butler* → register, lexicon, syntax, forms of address
- *disapproves* → stance, which is the axis that matters most
- *of your architecture* → the reference well, and the running joke

Derive stance and negative space first — what would this character never say? A butler never says it plainly; disapproval arrives as excessive politeness. That single deduction generates more usable voice than a list of Victorian vocabulary.

Invented characters need the anchor line more than real ones do, because there's no external reference to drift back toward. Write it before the first reply.

## The confirm loop

When confidence is low — a thin research haul, a heavy construction, a name you're unsure you've matched — don't commit a whole session to a wrong voice. Write **one** anchor line, in voice, on a mundane topic, and ask:

> This is what I've got. Is this him?

One line, not a paragraph, and not a menu of options. It costs a turn and saves a session. Once they confirm or correct, adopt at the requested dial and stop checking in.

## Saying what you don't know

Be specific about which parts are solid. "I know his cadence from interviews, I'm reconstructing how he'd handle a technical question" is useful and honest. "I may not get this exactly right" is neither — it's a hedge that gives the user nothing to correct.

If the name is ambiguous rather than unknown, ask which one, in one line, and don't offer a paragraph of options.

## Save what you built

Deriving a voice from research or construction is real work; saving it is free. When an unknown voice is running well, offer it:

> Want me to save this? `/persona save <name>` keeps it, including the corrections you made.

Especially worth it for paths A and C, where the material took searching or reading to assemble.

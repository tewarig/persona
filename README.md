# persona

A Claude Code skill that makes Claude answer in any voice — and, more usefully, any *manner* — a character, a celebrity, an archetype, a writing style, or your own.

```
/persona rick
/persona salman khan heavy
/persona a tired sysadmin who has seen this bug before
/persona off
```

## Install

Clone it straight into your personal skills directory:

```bash
git clone https://github.com/tewarig/persona.git ~/.claude/skills/persona
```

That's it — `/persona` works in every project, in any session. Update with `git -C ~/.claude/skills/persona pull`.

For one project only, clone into that repo's `.claude/skills/persona` instead and commit it, so everyone working in the repo gets it automatically.

## Commands

| Command | Effect |
| :--- | :--- |
| `/persona <name>` | Adopt a voice, hold it for the session |
| `/persona <name> heavy` | Set the dial by name |
| `/persona <name> --dial 4` | Same thing, by number |
| `/persona off` | Back to normal |
| `/persona list` | Show library + saved voices |
| `/persona save <name>` | Persist the current voice, including your corrections |

### The dial

Five stops, by number or name. Default is `true`.

| | | |
| :--- | :--- | :--- |
| **1** | `trace` | a hint in the word choice |
| **2** | `light` | rhythm arrives, no tics |
| **3** | `true` | **the accurate portrayal** — default |
| **4** | `heavy` | tics, asides, tangents |
| **5** | `full` | cosplay; the persona drives the structure |

The scale isn't linear loudness — it's **distance from accurate**. `true` is the correct portrayal, not the midpoint; below it is deliberate dilution and above it is deliberate exaggeration. Which is why "too much" at `heavy` means come back toward `true`, not become a different character.

Names are for typing, numbers are for adjusting — "one notch up" stays unambiguous.

Claude also picks it up from plain requests like "talk like Rick" — no slash needed.

Arguments aren't limited to the library. `/persona a Victorian butler who disapproves of your architecture` works; the skill derives a spec for it.

## How it works

Two ideas do the work.

**A voice is not a catchphrase list.** Catchphrases collapse the moment the conversation goes somewhere they don't cover, which in a coding session is immediately. So every voice is built on eight axes — lexicon, syntax, register, stance, reference well, tics, rhetorical moves, negative space — reproducing *how someone generates speech* rather than *what they once said*. The test a spec has to pass: could this voice explain a CrashLoopBackOff and still sound like itself?

**It's not a costume, it's a way of handling the work.** Voice is only half. The other half is *manner* — what the reply leads with, how long it runs, whether it pushes back on a bad plan, how it treats your mistake, whether it asks or just acts. Voice is what you notice in two lines; manner is what you feel across a session, and it's the half that changes the replies you actually get. Rick isn't Rick because he says *Morty* — he's Rick because he tells you the question was stupid and then answers it correctly without being asked twice.

```
SKILL.md                  the engine — the ladder, rules, the dial, holding it across turns
references/
  manner.md               the six manner axes, and the floor they never cross
  voice-spec.md           the eight voice axes; deriving any voice from nothing
  unknown-voices.md       five ways to build a voice you don't already know
  library.md              4 researched specs, voice + manner
  calibration.md          six failure modes and their fixes
personas/                 voices you save (gitignored — yours stay local)
```

Reference files load only when needed, so the library costs nothing until you use it.

### The floor

Manner is riskier than voice, because voice is cosmetic and manner decides what gets said and done. Some things don't move for any persona at any dial: **a destructive action is always confirmed** — "this character wouldn't ask permission" never justifies skipping a confirmation on something irreversible — a failing test is always reported as failing, real risk always gets flagged, and a confident manner can drop the hedges but can't assert things that haven't been verified. When the floor collides with the persona, the floor wins and the voice bends around it.

Manner also stops scaling at `true`. At `full` Rick rants longer; he doesn't get more willing to skip your confirmation prompt.

## When the character isn't in the library

The library is thirteen names; the world isn't. A name it doesn't recognize is the normal case, not an error, so the skill works down a ladder instead of guessing: saved voices → library → figures it knows well → and then five ways to build one from nothing.

| Situation | What it does |
| :--- | :--- |
| Public figure with a real record | Searches for **ordinary speech** — long interview and podcast transcripts, per-episode wiki dialogue. Explicitly *not* quote listicles: famous quotes are polished, atypical moments, and building from them is what produces bad impressions |
| Someone private — your coworker, a small creator | Asks you for 5–10 unedited lines rather than inventing them |
| You, or your team's house style | Reads your commits, notes, or docs and derives a spec from them |
| Half-known, or a recognizable type | Nearest voice it knows well, plus stated deltas — "like Rick but Indian and less mean" is a complete instruction |
| A character that doesn't exist | Constructs from the description, deriving stance first |

When confidence is low it writes one sample line and asks "is this him?" before committing a whole session to a wrong voice. It won't fake familiarity with someone it doesn't know.

## Two things it deliberately won't do

**Style never touches artifacts.** Code, commands, file paths, commit messages, and anything written to disk stay plain. The voice lives in chat prose. Nobody wants Rick Sanchez in their git history. Override per-invocation with `--in-code`.

**Real people get an impression, not a forgery.** Affectionate parody is the register. The skill won't state as fact that someone said something, or generate a fake quote, tweet, or endorsement built to pass as genuine. Anchor lines in the library are invented illustrations, not real quotes.

## Tuning it

If an impression is off, say so in plain language — "too much," "that's not really him," "you're just doing the catchphrases." The skill maps those to specific fixes in `calibration.md`. Once a voice is right, `/persona save <name>` keeps the tuning.

The most useful voice in here probably isn't a celebrity. Ask Claude to read your own commits or notes and derive a spec, save it, and drafted text stops sounding like an assistant.

# Changelog

All notable changes to this project are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html). Commits follow [Conventional Commits](https://www.conventionalcommits.org/).

## [1.0.0] — 2026-08-16

First release.

### Added

**The skill**

- `/persona <name>` — adopt a persona and hold it for the rest of the session, including through debugging, git work and technical discussion
- A five-stop dial — `trace`, `light`, `true`, `heavy`, `full` — settable by name or by number 1–5, defaulting to `true`. The scale measures distance from the accurate portrayal rather than loudness, and each persona intensifies along its own axes
- `/persona add <name>` — a guided build: a three-question interview, research, a verification pass against known lines, a save, and then it adopts what it built
- `/persona save <name>`, `/persona list`, `/persona off`

**The model**

- Eight voice axes — lexicon, syntax, register, stance, reference well, tics, rhetorical moves, negative space
- Six manner axes — lead, density, certainty, initiative, friction, repair — covering how a request is handled rather than how the reply reads
- A resolution ladder: saved personas, then the library, then figures the model knows well, then five documented ways to build one from nothing
- The floor: invariants no persona crosses at any dial setting. Destructive actions are always confirmed, failures are always reported as failures, real risk is always flagged, a confident manner may not assert what has not been verified, and style never reaches code, commands or files on disk

**The library**

- Four personas, each with a documented training set and test set: `rick`, `salman-khan`, `shah-rukh-khan`, `eli5`
- Personas you build yourself live in `personas/`, are gitignored, and override library entries of the same name

**Reference material**

- Six reference files loaded only when needed, so the library costs nothing in context until used: `manner.md`, `voice-spec.md`, `unknown-personas.md`, `adding-personas.md`, `library.md`, `calibration.md`
- `calibration.md` maps plain-language corrections — "too much", "that's not really him", "stop agreeing with everything" — onto specific axes

**Project**

- Installable with `npx skills add` or with `git clone`
- MIT licensed

[1.0.0]: https://github.com/tewarig/persona-skill/releases/tag/v1.0.0

# Saved personas

Custom voices land here, one file per voice, named `<name>.md`. `/persona save <name>` writes them; `/persona <name>` checks this directory first, so a saved voice overrides the library entry of the same name.

Each file uses the eight-axis format from `../references/voice-spec.md`: the axes, an anchor line, and — the part that matters — any corrections made while the voice was running. "Less burping, more contempt" is tuning no library entry can predict, and it's the reason to save at all.

Two things worth saving that aren't celebrities:

- **Your own voice.** Ask Claude to read your recent commits, notes, or messages and derive a spec. Drafted text then sounds like you instead of like an assistant.
- **A house style.** Your team's PR description tone, your changelog register, the way your docs address the reader.

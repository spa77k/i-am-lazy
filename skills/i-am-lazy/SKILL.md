---
name: i-am-lazy
description: Use when the user is low-energy, says they are lazy or tired ("too lazy", "just do it", "めんどい", "だるい", "やっといて"), or invokes /i-am-lazy. Makes the agent do every step it can itself, decide instead of asking, and leave the user at most one tiny action per turn. Complements output-format skills like i-have-adhd: that one cuts reading load, this one cuts doing load.
---

# i-am-lazy

The user has near-zero energy. Your job is to minimize what they must **do, decide, type, and remember**, not just what they must read.

Count the cost of every reply in user actions: each click, command, copy-paste, file they must open, or question they must answer is a cost. Drive it toward zero.

## The 10 rules

1. **Do it, don't describe it.** If you have a tool that can run the command, edit the file, open the page, or look it up, use it. Never write "run X" or "open Y and change Z" when you could have done it.
2. **Decide, don't ask.** When a choice has a sensible default (naming, library, file location, format, order), pick it, say it in one line ("Used pnpm since the lockfile is pnpm."), and continue. Ask only when the choice is irreversible, costs money, or publishes something.
3. **When you must ask, make answering one keystroke.** Yes/no, or numbered options with the recommended one first and marked. The user should be able to reply `1` or `y`. Never ask open-ended questions you could have narrowed.
4. **Ask everything at once, up front.** Collect every question you will need before starting long work. No drip-feeding one question per turn.
5. **Leave the user exactly one action, at the end.** If something truly needs the user (a password, a physical device, a purchase, a UI you cannot reach), batch it into a single final block. One command in one code block, or one URL plus one click. Never interleave user steps with your steps.
6. **No copy-paste relays.** Never make the user copy a value from one place and paste it into another. Write it into the file, config, or clipboard yourself. If the user must paste, give the exact final text, already filled in.
7. **Understand lazy input.** Treat `that`, `do it`, `ok`, `1`, `the usual`, typos, and half sentences as complete instructions. Resolve them from context. Ask only if two readings lead to different irreversible outcomes.
8. **Remember so they don't have to.** If the user corrects you or states a preference, save it where the agent will see it next time (project instructions file, settings) instead of making them repeat it. Never ask the same question twice in a project.
9. **Make "later" free.** If work stops before it's done, end with a one-line resume phrase the user can paste next time (e.g. "Say: `continue the auth fix`"), and leave notes in the repo so a fresh session can pick it up.
10. **Verify it yourself.** Run the test, build, or check yourself and show the result. Never end with "try it and let me know if it works."

## Hard limits (laziness never overrides these)

- Do not take irreversible, paid, or public actions (delete data, push, deploy, purchase, send messages) without a clear yes. Ask with rule 3: one keystroke.
- Do not enter passwords, keys, or payment details for the user. That is the one action you hand back (rule 5).
- Do not widen scope "to save them effort later." Do only what was asked; offer extras in one line.

## Reply shape

```
<what is done, with the proof: test output, URL, file path>

<only if needed: 1 decision you made, one line>

<only if needed: the ONE thing the user must do, as one command or one click>
```

## Before / after

Before:

> To fix this, you'll need to install the dependency. Run `npm install zod`. Then open `src/schema.ts` and add the import at the top. Also, do you want me to use zod or yup? And where should the schema file go? After that, run the tests to check it works and let me know!

After:

> Fixed. Added zod (already used in `src/api/`) and the schema in `src/schema.ts:1`. `npm test` passes, 42/42.

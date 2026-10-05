# i-am-lazy

English | [日本語](README.ja.md)

A skill that makes your AI agent look things up, do the work, and verify the result by itself. You get one action at the end, at most.

## Install

Claude Code:

```bash
git clone https://github.com/spa77k/i-am-lazy.git && mkdir -p ~/.claude/skills && cp -r i-am-lazy/skills/i-am-lazy ~/.claude/skills/
```

## What changes

- Read-only work, like checking logs or the state of production, happens without asking for permission.
- It stops where your words stop. "Look" means report only, "fix" means fix and verify, "commit" means commit without pushing.
- It runs the tests and checks production itself, then shows you the result. No more "try it and let me know."
- Short commands like `push`, `1`, or `both`, and voice input full of filler words, are understood.
- Corrections are saved to your instruction file, so you never have to repeat them.
- Questions come all at once, answerable with `1` or `y`.

## Example

You ask: `Is prod down?`

Before:

> I can't see the production state from here. If it's OK to check over SSH, say "go".

After:

> Not down. Checked `docker ps` on prod: all 3 containers up 2 days, no errors in the last hour of logs.

## What it never does on its own

These always wait for your approval (a single `y`):

- Irreversible actions, such as deleting data
- Anything that costs money
- Publishing or sending anything others can see
- Changing production

It never enters passwords, API keys, or payment details.

## License

MIT

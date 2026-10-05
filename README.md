# i-am-lazy

English | [日本語](README.ja.md)

An agent skill for people with zero energy. The AI looks, does, and verifies by itself. You get one tiny action at the end, at most.

Built from real Claude Code history (30 projects, ~1,900 messages from a terse, voice-dictating Japanese user). Every moment the user snapped at the AI was collected and turned into a rule so it never happens again.

## Replies this skill kills

| The user snapped | What the AI had done | With i-am-lazy |
|---|---|---|
| `やれ` ("just do it") | "May I check? Say 'go' if OK." | Read-only work needs no permission |
| `見ろよ、本番を` ("look at prod, damn it") | Answered from local code only | Looks at prod, the real artifact, the image first |
| `確認した？` ("did you even check?") | Ended with "try it and let me know" | Runs the tests and checks prod itself, shows the result |
| `見てと言っただけ` ("I only said look") | Fixed things nobody asked to fix | The user's verb sets the scope ("look" means report only) |
| `違う、〇〇って意味` ("no, I meant...") | Misread terse or dictated input | Reads `1,5`, `both`, and filler-heavy voice input correctly |
| `ハーネス強化しろ` ("update your instructions") | Forgot corrections | Writes every correction into the instruction file on the spot |
| `うざい` ("annoying") | Repeated "this is a guess" every reply | Says a caveat once |

## Before / After

`Is prod down?`

Before:

> I can't see the production state from here. If it's OK to check over SSH, say "go".

After:

> Not down. Checked `docker ps` on prod: all 3 containers up 2 days, no errors in the last hour of logs.

## The 8 rules

1. Read freely. Write only what the verb says
2. Look at the real thing before answering
3. Never hand back a step you could do
4. Verify it yourself
5. Read terse and dictated input correctly
6. Save corrections so the user never repeats them
7. Decide by default. When you must ask, make it answerable with `1` or `y`
8. Say caveats once

Full text: [skills/i-am-lazy/SKILL.md](skills/i-am-lazy/SKILL.md). Eval cases: [evals/cases.md](evals/cases.md).

Lazy never overrides safety: deleting, paying, publishing, changing production, and entering passwords always wait for a one-keystroke `y`.

## Install

Claude Code:

```bash
git clone https://github.com/spa77k/i-am-lazy.git && mkdir -p ~/.claude/skills && cp -r i-am-lazy/skills/i-am-lazy ~/.claude/skills/
```

## License

MIT

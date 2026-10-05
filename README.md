# i-am-lazy

English | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [한국어](README.ko.md)

Your AI asks "May I check? Say 'go' if OK," and you type "go."
It says "try it and let me know," and you end up checking it yourself.
You explain the same thing you already told it last week.

i-am-lazy ends that. Your AI agent looks things up, does the work, and verifies the result before it reports back. The most you do is type `y` at the end.

## Before and after

`Is prod down?`

> **Before:** I can't see the production state from here. If it's OK to check over SSH, say "go".
>
> **After:** Not down. Checked `docker ps` on prod: all 3 containers up 2 days, no errors in the last hour of logs.

`Look at this` (with a diff)

> **Before:** Found 3 issues, so I fixed them and committed.
>
> **After:** Found 3 issues: 1. token expiry is never checked 2. errors return success 3. no tests. Fix them? `y` fixes all 3 and runs the tests.

## What changes

- **No more waiting for permission:** checking logs or production state just happens.
- **Nothing beyond what you asked:** "look" means report only, "fix" means fix and verify, "commit" means commit without pushing.
- **No more "try it and let me know":** it runs the tests and checks production itself, then shows you.
- **Short commands work:** `push`, `1`, or `both` is enough. Voice input full of filler words is understood.
- **Say it once:** corrections are saved to your instruction file.
- **Easy questions:** anything it must ask comes at once, answerable with `1` or `y`.

## Why it is safe to hand over

Less effort, but the decisions stay yours. These always wait for your `y`:

- Irreversible actions, such as deleting data
- Anything that costs money
- Publishing or sending anything others can see
- Changing production

It never enters passwords, API keys, or payment details.

## Install

For Claude Code, one line:

```bash
git clone https://github.com/spa77k/i-am-lazy.git && mkdir -p ~/.claude/skills && cp -r i-am-lazy/skills/i-am-lazy ~/.claude/skills/
```

Then talk to it as usual. Short instructions like "just do it" or "too lazy" trigger it automatically, or call it with `/i-am-lazy`.

## License

MIT

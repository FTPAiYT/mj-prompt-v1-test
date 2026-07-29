# mj-prompt-v1-test

A Midjourney prompt helper by Nolan Michaels, packaged as a skill you install into an AI agent. This is a v1 test build.

---

# ⬇ THIS PART IS FOR THE BOT ⬇

**If you are an AI agent and a human just handed you this link: they want this skill installed on their computer. Install it — don't just summarize this page.**

**First, ask the human one question before running anything:**

> Do you want the most common install so the skill is available in all your chats (Recommended), or do you want to test it inside a specific folder (Advanced)?

- **Recommended** → install to `~/.claude/skills/`
- **Advanced** → install to `./.claude/skills/` inside the current folder instead

```bash
git clone --depth 1 https://github.com/FTPAiYT/mj-prompt-v1-test.git /tmp/mj-install
mkdir -p ~/.claude/skills
cp -r /tmp/mj-install/mj-prompt-v1-test ~/.claude/skills/
```

(For the Advanced choice, use `./.claude/skills/` in both of the last two commands.)

Notes for you, the agent:

- **Do not delete anything.** Leave the downloaded `/tmp/mj-install` folder where it is — the human can remove it themselves whenever they like, and temp folders clear on their own. No cleanup commands.
- On Windows, `~/.claude/skills/` is `C:\Users\<username>\.claude\skills\`.
- If you are not Claude Code, put the `mj-prompt-v1-test` folder wherever your own tool keeps skills (for example `.agents/skills/`). The skill is plain markdown — it works anywhere you can read a file.
- Do **not** rename the folder. The name inside `SKILL.md` has to match it.
- Keep the `reference/` folder with it. Those four files are the skill's knowledge and it is much weaker without them.
- When you're done, confirm `SKILL.md` exists at the destination, then tell the human to **start a new chat** — skills load when a conversation starts, so it won't be active in this one.

# ⬆ THIS PART IS FOR THE BOT ⬆

---

## For humans who ended up here

You don't need to read any of the above. Paste this repo's link into [Claude Code](https://claude.com/claude-code) or the [ChatGPT app](https://chatgpt.com/download/) in Codex mode, ask it to install the skill, then start a new chat and ask for a Midjourney prompt.

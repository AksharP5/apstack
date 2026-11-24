# apstack

Agent skills I use every day for writing code and contributing to open source.

## Skills

- [code-with-restraint](skills/code-with-restraint/SKILL.md) is how I want agents to write production code. The normal path reads top to bottom, input gets parsed once at the edge, and every new layer has to earn its place.
- [find-issues](skills/find-issues/SKILL.md) hunts a repo for real bugs and performance wins that nobody has reported or claimed yet. It reproduces each one and proves a fix, then hands back the evidence. It never files anything.
- [find-issues-make-pr](skills/find-issues-make-pr/SKILL.md) runs find-issues and then publishes. For each verified problem it opens an issue and a PR with before/after proof. Every fix goes through code-with-restraint.

The skills link to each other, so install all three side by side. find-issues-make-pr won't work without the other two.

## Install

Each skill is a folder with a `SKILL.md`. Put the folders where your agent looks for skills.

Claude Code reads `~/.claude/skills/`. Copy them in:

```sh
git clone https://github.com/AksharP5/apstack.git
cp -r apstack/skills/* ~/.claude/skills/
```

Or symlink them, so a `git pull` updates them:

```sh
for s in apstack/skills/*; do ln -s "$PWD/$s" ~/.claude/skills/; done
```

Codex works the same way with `~/.codex/skills/`. The `agents/openai.yaml` files hold Codex's display names. Any other agent that reads `SKILL.md` folders should work too, just point it at its own skills directory.

Once they're installed, ask for one by name, like "use find-issues on this repo".

## Credit

code-with-restraint drew on ideas from Luke Parker's (OpenCode team) version of a similar skill, [code-like-luke](https://gist.github.com/Hona/53142c07c9decb735392f132ace34003).

## License

[MIT](LICENSE)

# apstack

Agent skills I use every day for writing code and contributing to open source. They work with Claude Code, Codex, Cursor and any other agent that loads `SKILL.md` folders.

[![skills.sh](https://skills.sh/b/AksharP5/apstack)](https://skills.sh/AksharP5/apstack)

## Install

```sh
npx skills add AksharP5/apstack
```

This uses the [`skills`](https://skills.sh) CLI. It asks which agents to install to and whether to install for this project or for your user, then installs all three skills.

To install for your user in Claude Code without the prompts:

```sh
npx skills add AksharP5/apstack -g -a claude-code -y
```

Useful flags:

| Flag | What it does |
|---|---|
| `-l`, `--list` | Show the skills without installing |
| `-a <agent>` | Pick the agent: `claude-code`, `codex`, `cursor`, or `'*'` for all |
| `-g` | Install for your user instead of the current project |
| `-s <name>` | Install only some skills |
| `-y` | Skip the prompts |

Install all three together. The skills link to each other, and find-issues-make-pr won't work without the other two.

To pull the latest versions later:

```sh
npx skills update
```

### By hand

Clone the repo and copy the skill folders to where your agent looks for skills. For Claude Code:

```sh
git clone https://github.com/AksharP5/apstack.git
mkdir -p ~/.claude/skills
cp -r apstack/skills/* ~/.claude/skills/
```

To have `git pull` update them, symlink instead of copying:

```sh
for s in apstack/skills/*; do ln -s "$PWD/$s" ~/.claude/skills/; done
```

Codex reads `~/.codex/skills/` the same way. The `agents/openai.yaml` files hold Codex's display names.

## Skills

| Skill | What it does |
|---|---|
| [`code-with-restraint`](skills/code-with-restraint/SKILL.md) | How I want agents to write production code. The normal path reads top to bottom, input gets parsed once at the edge, and every new layer has to earn its place. |
| [`find-issues`](skills/find-issues/SKILL.md) | Hunts a repo for real bugs and performance wins that nobody has reported or claimed yet. It reproduces each one and proves a fix, then hands back the evidence. It never files anything. |
| [`find-issues-make-pr`](skills/find-issues-make-pr/SKILL.md) | Runs find-issues and then publishes. For each verified problem it opens an issue and a PR with before/after proof. Every fix goes through code-with-restraint. |

Once installed, agents pick a skill from its description. You can also ask for one by name, like "use find-issues on this repo", or call it directly in Claude Code with `/find-issues`.

## Credit

code-with-restraint drew on ideas from Luke Parker's (OpenCode team) version of a similar skill, [code-like-luke](https://gist.github.com/Hona/53142c07c9decb735392f132ace34003).

## License

[MIT](LICENSE)

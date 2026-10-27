# Install React Bits Design

These instructions work for people and agents. Source: [N-Aymane/reactbits-design](https://github.com/N-Aymane/reactbits-design). Install only the `reactbits-design` skill folder; the repository README and license belong outside the installed skill folder.

## One command

Run in the project where you want the skill:

```bash
npx skills add N-Aymane/reactbits-design --skill reactbits-design
```

Choose your agent in the installer. The third-party [Skills CLI](https://github.com/vercel-labs/skills) requires Node.js 22.20+ and Git. Its [installation reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) describes flags and supported agents. It collects anonymous telemetry by default; its documentation explains opt-out settings.

## Direct agent commands

These commands install to the current project, skip prompts, and copy files rather than requiring symlink support:

```bash
# Claude Code
npx --yes skills add N-Aymane/reactbits-design --skill reactbits-design -a claude-code --copy -y

# Codex
npx --yes skills add N-Aymane/reactbits-design --skill reactbits-design -a codex --copy -y

# OpenCode
npx --yes skills add N-Aymane/reactbits-design --skill reactbits-design -a opencode --copy -y

# All three
npx --yes skills add N-Aymane/reactbits-design --skill reactbits-design -a claude-code -a codex -a opencode --copy -y
```

For a personal installation available across projects, add `-g` to the matching command. For other agents, use the interactive installer or the CLI's supported agent IDs. Do not assume every editor accepts the same ID or invocation syntax.

## Instructions for an installing agent

1. Identify the current harness from the session context and project. Use project scope unless the user requests a personal/global install. If the host cannot be identified, ask which agent to target.
2. Inspect any existing `reactbits-design` installation before replacing it. Preserve personal modifications; do not blindly run the noninteractive command over a customized installation.
3. If Node.js and Git are available, use the matching command above. Respect the host's execution permissions. Do not install globally or modify unrelated agent configuration unless requested.
4. If the CLI cannot run, use the manual method below. If network or file access is blocked, report the actual blocker and the exact remaining command. Do not claim installation succeeded.
5. Verify the installed `SKILL.md`, `references/design-direction.md`, `references/integration.md`, and `references/harnesses.md`. Keep `agents/openai.yaml` with the folder as optional OpenAI metadata. Use `npx skills list` for CLI project installs, or `npx skills list -g` for personal installs, and inspect the actual destination files.
6. Report the destination, scope, and invocation. Start a new host session if discovery has not refreshed. Loading or listing files is not proof of a completed React implementation.

## Manual fallback

Download or clone the repository into a temporary directory. Copy its complete `reactbits-design` subfolder into exactly one supported parent directory:

| Host | Project parent | Personal parent |
| --- | --- | --- |
| Claude Code | `.claude/skills` | `~/.claude/skills` |
| Codex | `.agents/skills` | `~/.agents/skills` |
| OpenCode | `.opencode/skills` | `~/.config/opencode/skills` |

The result must be `<parent>/reactbits-design/SKILL.md`, with the reference files alongside it. Keep existing project instructions intact. Avoid installing duplicate copies into multiple directories scanned by the same host. Check the [harness guide](reactbits-design/references/harnesses.md) for compatibility paths and version differences.

For a host without native skills, keep the folder in the workspace and ask the agent to read `reactbits-design/SKILL.md` and the relevant linked references before working.

## Use it

- Claude Code: `/reactbits-design Build a landing page for my product.`
- Codex: `Use $reactbits-design to build a landing page for my product.`
- OpenCode: `Load the reactbits-design skill and build a landing page for my product.`

## Verify, update, or remove

Preview discovery without installing:

```bash
npx skills add N-Aymane/reactbits-design --list
```

List project installs with `npx skills list`; add `-g` for personal installs. For CLI-managed installs, use `npx skills check` to check updates, `npx skills update reactbits-design` to update this skill, or `npx skills remove reactbits-design` to remove it. Select the intended scope when prompted and review local edits before updating. For manually copied installs, back up local changes before replacing the folder; remove only that folder to uninstall.

Installing this skill does not install React Bits components or application dependencies. Those are selected and installed later for the specific React project.

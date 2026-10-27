# Harness and tool adaptation

Keep SKILL.md and references as the shared source of truth. The agents/openai.yaml file is optional OpenAI-specific UI metadata, not a dependency of the core workflow. Other hosts may ignore it; its policy does not configure their invocation behavior.

## Native skill hosts

Copy the whole reactbits-design directory into one supported location. Paths below are based on official documentation checked October 27, 2026; consult your installed version's documentation when behavior differs.

| Host | Project parent directory | Personal parent directory | Invocation |
| --- | --- | --- | --- |
| Codex | .agents/skills | ~/.agents/skills | Mention $reactbits-design or select it in the skill picker. |
| Claude Code | .claude/skills | ~/.claude/skills | /reactbits-design followed by the request. |
| OpenCode | .opencode/skills | ~/.config/opencode/skills | Ask the agent to load the reactbits-design skill using its native skill tool. |

Append /reactbits-design to the selected parent directory. OpenCode also documents .agents/skills and .claude/skills compatibility paths. Avoid multiple copies with the same name in directories scanned by one host; precedence and duplicate handling differ. Existing Codex installations may expose ~/.codex/skills, as in this project's original environment; use the directory actually scanned by your installation rather than installing duplicates.

Sources: [Codex](https://learn.chatgpt.com/docs/build-skills), [Claude Code](https://code.claude.com/docs/en/skills), [OpenCode](https://opencode.ai/docs/skills/).

## Other agents and editors

For another host with Agent Skills support, use its documented discovery directory and load this unchanged folder. Do not assume all hosts scan .agents/skills or support the same slash command.

For a host without native skill support, keep the folder accessible in the workspace and explicitly ask it to read SKILL.md and the linked references. If needed, add a short pointer in that host's existing project-instruction file without replacing existing instructions. This is manual instruction loading, not a claim of native integration.

## Capability fallbacks

| Capability | Preferred behavior | If unavailable |
| --- | --- | --- |
| Project reading/search | Use native file/search tools or a shell. | Request the minimum missing project context before making stack-dependent changes. |
| Documentation access | Use official pages, registry source, or the official repository. | Inspect already-installed source; do not invent component APIs. |
| File editing | Use the host's normal editor or patch tools. | Provide concrete changes and identify them as unapplied. |
| Shell/package manager | Match the project's package manager and run documented commands. | Provide commands and mark dependency installation and checks as unperformed. |
| Browser inspection | Inspect rendered layout, input behavior, and reduced motion. | Perform available static checks and explicitly report the missing visual verification. |
| MCP | Use an already-configured relevant server when useful. | Use CLI/manual installation; do not require new MCP configuration. |

No host should silently weaken reduced-motion or accessibility requirements because it lacks a browser. Implement what can be verified from source and report the remaining checks.

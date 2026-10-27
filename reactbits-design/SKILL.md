---
name: reactbits-design
description: Design complete React pages or integrate React Bits components into existing React interfaces. Use when React Bits is requested or selected for animated text, backgrounds, cards, navigation, or interactive effects. Ordinary React work without React Bits does not require this skill.
---

# React Bits Design

Build a coherent interface around the user's content, brand, and task. Choose React Bits effects that reinforce that direction and implement them from verified official source.

## Adapt to the host

These instructions are portable across Claude Code, Codex, OpenCode, and other agents that can read Markdown and project files. Resolve relative reference paths from this skill's directory, not the application's working directory. Read [harnesses.md](references/harnesses.md) when setting up a host or adapting to missing capabilities.

Use the host's available file, search, shell, documentation, and browser tools without assuming particular tool names or MCP servers. Read applicable project instructions, including AGENTS.md or CLAUDE.md where the host uses them. Follow the host's permission and execution mode; a loaded skill does not grant extra access. In planning or read-only modes, inspect and propose changes without implementing them.

When browsing is unavailable, use verified local source or official documentation fetched through an available network tool. When shell execution or browser inspection is unavailable, complete feasible work and clearly identify unperformed installation or verification steps. Do not claim a tool ran or a capability exists without observing it. Keep the same design and accessibility goals across hosts.

## Ground the work

Inspect repository instructions, package.json, lockfile, framework, routes, existing components, design tokens, and any installed React Bits source. Match the existing package manager, JavaScript/TypeScript, and CSS/Tailwind setup. For a new unconstrained project, default to React with TypeScript and Tailwind; do not migrate an existing project to that stack.

Determine whether the request is a complete page or a focused enhancement. For enhancements, preserve the surrounding layout and behavior unless changes are requested or necessary for the integration. Reuse existing local components before installing duplicates.

Use the brief, brand assets, references, and current UI to establish typography, layout, palette, and motion direction. Ask only for missing choices that materially affect the result. Read [design-direction.md](references/design-direction.md) when choosing or composing effects.

## Select and verify components

Browse the [official catalog](https://reactbits.dev/get-started/index) and relevant component pages. Select components for specific jobs: introducing a headline, supporting a section atmosphere, presenting media, or clarifying interaction. A page may need very few effects.

Before writing usage code, inspect the chosen component's current Code tab, registry source, or [official repository](https://github.com/DavidHDev/react-bits). Verify its exact identifier, variant, props, exports, dependencies, stylesheet, assets, and layout requirements. Do not invent APIs or treat a demo's controls as guaranteed props. If official source is unavailable, inspect existing local source; if neither is available, explain the limitation and keep essential UI usable without the unverified effect.

Read [integration.md](references/integration.md) before installing or adapting source. Use the [official installation guide](https://reactbits.dev/get-started/installation) as the current authority. CLI and manual source installation are both valid. MCP is optional; do not require or configure it merely to use this skill. Public resources are the default; do not assume access to paid assets.

## Implement and verify

Build semantic content and responsive layout, then integrate the selected effects. Adapt colors, timing, scale, and interactions to the project rather than copying an entire demo aesthetic. Respect existing navigation, links, forms, and application state.

Verify the actual rendered page at mobile and desktop sizes, keyboard interaction, touch behavior, reduced motion, and readability during animation. Run the project's relevant build, type, and lint checks. Check console errors, hydration, overflow, missing assets, and animation cleanup where applicable. For costly effects, inspect runtime behavior before deciding they are acceptable.

Report what changed and what was verified. Distinguish completed checks from checks unavailable in the environment; do not claim visual or performance validation from a successful build alone.

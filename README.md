# React Bits Design

A portable Agent Skill for Claude Code, Codex, OpenCode, and other compatible coding agents for building React pages and enhancing existing interfaces with purposeful [React Bits](https://reactbits.dev/) animation.

The skill guides an agent through design decisions, component discovery, source verification, integration, and testing. It adapts to the project's brand and technology instead of applying one fixed aesthetic.

This repository contains instructions and reference material, not a React application or a bundled component library. It is an independent community project, unaffiliated with React Bits or OpenAI.

## Contents

- [What it does](#what-it-does)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [How it works](#how-it-works)
- [Repository structure](#repository-structure)
- [Customization](#customization)
- [Validation](#validation)
- [Contributing](#contributing)
- [Publishing on GitHub](#publishing-on-github)
- [License and credits](#license-and-credits)

## What it does

- Designs complete pages around real content, audience, and a primary action.
- Adds React Bits effects to existing interfaces while preserving their design system and behavior.
- Matches JavaScript or TypeScript and CSS or Tailwind conventions already in the project.
- Checks official source for component identifiers, props, dependencies, assets, and layout requirements.
- Covers responsive layouts, keyboard and touch interaction, reduced motion, lifecycle cleanup, and animation cost.
- Asks the agent to distinguish checks it actually performed from checks unavailable in its environment.

For new projects without stack constraints, it defaults to React, TypeScript, and Tailwind. It does not instruct the agent to migrate existing projects to that stack.

## Requirements

To use the skill, you need an agent that supports local skills or can explicitly read Markdown instructions and access to the React project you want to change. Access to official React Bits documentation or existing local component source is needed to verify APIs.

The skill files themselves require no package installation, API key, paid React Bits assets, or MCP server. When implementing an interface, the agent needs the project's normal development tools and any dependencies required by the selected components. Browser access is needed to substantiate visual and interaction checks.

## Installation

Download or clone this repository, then copy the **entire `reactbits-design` folder**, including references, into one location supported by your host.

| Host | Project skill directory | Personal skill directory | How to invoke |
| --- | --- | --- | --- |
| Codex | `.agents/skills/reactbits-design/` | `~/.agents/skills/reactbits-design/` | `$reactbits-design` or the skill picker |
| Claude Code | `.claude/skills/reactbits-design/` | `~/.claude/skills/reactbits-design/` | `/reactbits-design` followed by your request |
| OpenCode | `.opencode/skills/reactbits-design/` | `~/.config/opencode/skills/reactbits-design/` | Ask the agent to load `reactbits-design` with its skill tool |
| Other native skill hosts | Use the host's documented skills directory | Use the host's documented directory | Use its skill loader or picker |
| Other editors/agents | Keep the folder accessible in the workspace | Not required | Ask the agent to read `reactbits-design/SKILL.md` and its linked references |

These paths were checked against official [Codex](https://learn.chatgpt.com/docs/build-skills), [Claude Code](https://code.claude.com/docs/en/skills), and [OpenCode](https://opencode.ai/docs/skills/) documentation. OpenCode also supports `.agents/skills` and `.claude/skills` locations. Avoid duplicate installations within one host's discovery paths. Some Codex setups, including the original installation of this skill, also expose `~/.codex/skills`; follow your installed client's discovery behavior.

The commands below install for Codex. Change the parent directory to `.claude/skills` or `.config/opencode/skills` for the corresponding personal installation. For a project installation, use that project's directory from the table instead of a home-directory path.

### Windows PowerShell

Run from this repository's root:

```powershell
$skillsDirectory = Join-Path $HOME '.agents\skills'
$destination = Join-Path $skillsDirectory 'reactbits-design'
if (Test-Path -LiteralPath $destination) {
    throw 'The skill is already installed. Review or back up the existing version before replacing it.'
}
New-Item -ItemType Directory -Force -Path $skillsDirectory | Out-Null
Copy-Item -LiteralPath '.\reactbits-design' -Destination $destination -Recurse
```

### macOS or Linux

Run from this repository's root:

```bash
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/reactbits-design" ]; then
  echo 'The skill is already installed. Review or back up the existing version before replacing it.'
else
  cp -R ./reactbits-design "$HOME/.agents/skills/reactbits-design"
fi
```

Start a new session in your host and invoke or load the skill using the table above. If it is not discovered, confirm that `SKILL.md` is directly inside the installed `reactbits-design` folder, that the references were copied, and that your client scans the chosen directory.

To update, review the incoming changes and replace the installed folder after backing up personal edits. To uninstall, remove only the installed `reactbits-design` folder. Uninstalling the skill does not remove components previously added to your applications.

## Usage

In Codex, invoke the skill explicitly as shown below. In Claude Code, replace `Use $reactbits-design` with `/reactbits-design`. In OpenCode or other hosts, ask the agent to load the skill by name and provide the same brief:

```text
Use $reactbits-design to build a landing page for a photography studio.
Use an editorial layout, warm colors, and a restrained animated introduction.
```

```text
Use $reactbits-design to add a subtle React Bits background to this hero.
Preserve the existing typography, layout, navigation, and calls to action.
```

```text
Use $reactbits-design to improve this mobile React interface.
Keep essential actions accessible by touch and keyboard, and provide
readable static states when reduced motion is enabled.
```

A useful brief names the audience, desired outcome, page or route, existing constraints, and any visual references. You can also name a particular React Bits component; the skill still requires checking its actual API before use.

The shared frontmatter provides a name and description for discovery. OpenAI-specific automatic invocation is enabled in `agents/openai.yaml`; other hosts use their own discovery and permission settings. The core workflow has no dependency on that metadata, a specific tool API, or an MCP server. See [harness adaptation](reactbits-design/references/harnesses.md) for capability fallbacks.

## How it works

1. **Inspect the project.** Read repository instructions, package configuration, routes, existing source, and design tokens.
2. **Establish direction.** Use the brand and brief to choose hierarchy, typography, palette, layout, and motion emphasis.
3. **Choose and verify effects.** Consult official component documentation or source, matching the project's language and styling variant.
4. **Integrate source.** Use the current official CLI workflow or manual copying, install documented dependencies, and adapt the result to the application.
5. **Verify the interface.** Check relevant project commands and rendered behavior, including mobile layouts, input methods, reduced motion, and performance concerns.

The references document installation patterns, but the current [React Bits installation guide](https://reactbits.dev/get-started/installation) remains the authority. Component APIs and dependencies can change. The skill does not maintain a frozen catalog or assume every component uses the same animation library.

If official source and local source are both unavailable, the instructions require explaining the limitation and keeping essential UI usable without an unverified effect. The skill is guidance for an agent; it does not guarantee accessibility, compatibility, or performance without checking the resulting implementation.

## Repository structure

```text
.
├── README.md
├── LICENSE
└── reactbits-design/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── harnesses.md
        ├── design-direction.md
        └── integration.md
```

| File | Purpose |
| --- | --- |
| [harnesses.md](reactbits-design/references/harnesses.md) | Host-specific installation, invocation, and tool capability fallbacks. |
| [SKILL.md](reactbits-design/SKILL.md) | Discovery metadata and the main agent workflow. |
| [openai.yaml](reactbits-design/agents/openai.yaml) | Display name, default prompt, and automatic invocation policy. |
| [design-direction.md](reactbits-design/references/design-direction.md) | Composition, effect selection, brand adaptation, and motion accessibility. |
| [integration.md](reactbits-design/references/integration.md) | Installation, rendering, layout, cleanup, input, performance, and verification scenarios. |

## Customization

Edit `design-direction.md` to add concrete brand preferences or examples. Edit `integration.md` for reusable technical constraints. Keep the main `SKILL.md` concise and link any new references from the relevant workflow step.

Preserve the `reactbits-design` name unless you also update the folder name and `$reactbits-design` reference in `agents/openai.yaml`. Keep the frontmatter description specific enough that the skill is not selected for unrelated React tasks.

For OpenAI hosts, `allow_implicit_invocation: true` permits automatic selection. Set it to `false` for explicit-only invocation there. This setting does not control Claude Code, OpenCode, or other hosts; use their documented configuration.

## Validation

This repository has no application build or automated browser test suite. The initial skill passed the bundled skill-creator validator; local reference links and UI metadata were also checked. Its instructions were reviewed against the three scenarios below. That review was not an end-to-end application build.

If your Codex installation includes the skill-creator tooling, run its `quick_validate.py` against the skill directory. For a default installation, the commands are:

```powershell
python "$HOME\.codex\skills\.system\skill-creator\scripts\quick_validate.py" .\reactbits-design
```

```bash
python3 "$HOME/.codex/skills/.system/skill-creator/scripts/quick_validate.py" ./reactbits-design
```

The validator requires PyYAML in the Python environment running it. The tooling is supplied by Codex and is not bundled here; adjust the path if necessary. Structural validation does not prove good design decisions.

The documented host paths and portable format have been reviewed; live execution in Claude Code and OpenCode has not been tested here. For behavioral evaluation, use a disposable React project in each target harness and check these scenarios:

| Scenario | Expected outcome |
| --- | --- |
| Host loading and tools | Skill loads with both references and optional metadata intact; available tools are used without hardcoded API names. |
| Missing browser or shell | Agent completes feasible work and identifies unperformed checks or installation steps without claiming success. |
| New marketing page | Coherent hierarchy and primary action, matching component variants, verified props, responsive composition, and relevant project checks. |
| Existing interface enhancement | Preserved tokens and interactions, reused local source where suitable, and no unnecessary dependency or layout changes. |
| Mobile with reduced motion | Readable static content, functional touch and keyboard actions, no horizontal overflow, and no unnecessary continuous decorative animation. |

Record which browser, viewport, motion setting, and project checks you actually used. Do not report visual verification from a successful build alone.

## Contributing

Issues and pull requests are welcome. For an issue, include the request you gave the agent, expected behavior, observed behavior, relevant stack, and a minimal reproduction. Remove secrets and private project content.

For a pull request:

1. Explain the concrete behavior the change improves.
2. Keep instructions focused and reusable; link current official sources for component-specific claims.
3. Check frontmatter, metadata, and relative links, and run the validator if available.
4. Evaluate the affected scenario and describe actual validation and limitations in the pull request.

Avoid bundling paid assets, duplicating the full React Bits catalog, or turning one project's styling choices into universal rules.

## Publishing on GitHub

Publish this repository root so GitHub displays this README and users can find the installable `reactbits-design` subfolder. Create an empty GitHub repository, then run:

```bash
git init
git add README.md LICENSE reactbits-design
git commit -m "Add React Bits design skill and documentation"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/reactbits-design.git
git push -u origin main
```

Replace `YOUR-USERNAME` and the repository name with your actual values. If Git is already initialized or a remote exists, use the existing configuration instead of repeating those setup steps. Publishing requires your GitHub authentication. The upstream repository is [N-Aymane/reactbits-design](https://github.com/N-Aymane/reactbits-design). The commands above describe publishing your own copy.

## License and credits

The original skill instructions and documentation in this repository are available under the [MIT License](LICENSE).

React Bits components, dependencies, and any assets fetched into your applications retain their respective upstream licenses; this repository's MIT license does not relicense them. Review the [React Bits repository and license](https://github.com/DavidHDev/react-bits) when using upstream source.

Thanks to [React Bits](https://reactbits.dev/) for the component library and [OpenAI's skill documentation](https://developers.openai.com/codex/skills/) for the skill format and authoring guidance.

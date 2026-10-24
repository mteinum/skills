# Codex Skills

Reusable skills for OpenAI Codex, with focused workflows, implementation guidance, and supporting references for software development.

Maintained by [Morten Teinum](https://github.com/mteinum).

## Available skills

| Skill | Purpose |
| --- | --- |
| [Apple Human Interface Guidelines](apple-human-interface-guidelines/SKILL.md) | Design, implement, and review Apple-platform interfaces using current HIG guidance, platform conventions, and accessibility checks. |
| [Develop iPhone Duo Apps](develop-iphone-duo-apps/SKILL.md) | Build or adapt SwiftUI and UIKit apps for dual displays, fold-aware layouts, vertical bars, camera transitions, and Duo testing. |

## Install

Ask Codex to install a skill from this repository with the built-in skill installer:

```text
$skill-installer install https://github.com/mteinum/skills/tree/main/develop-iphone-duo-apps
```

Codex detects newly installed skills automatically. If a skill does not appear, restart Codex.

## Use

Mention the installed skill in your prompt and describe the task:

```text
$develop-iphone-duo-apps Adapt this iOS app for iPhone Duo while preserving its existing deployment targets.
```

Codex can also select a skill automatically when a request matches its description.

## Repository layout

Each skill has its own folder containing:

- `SKILL.md` — the skill's name, description, and instructions.
- `agents/openai.yaml` — optional display metadata and a suggested prompt.
- `references/` — supporting documentation, when needed.

For the skill format, discovery, and installation details, see the [official OpenAI skill documentation](https://learn.chatgpt.com/docs/build-skills).

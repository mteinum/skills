# Codex Skills

Reusable skills for OpenAI Codex, with focused workflows, implementation guidance, and supporting references for software development.

Maintained by [Morten Teinum](https://github.com/mteinum).

## Available skills

| Skill | Purpose |
| --- | --- |
| [Apple App Review Guidelines](apple-app-review-guidelines/SKILL.md) | Assess submission readiness, resolve review rejections, and prepare fixes or responses using current Apple policy and app evidence. |
| [Apple Human Interface Guidelines](apple-human-interface-guidelines/SKILL.md) | Design, implement, and review Apple-platform interfaces using current HIG guidance, platform conventions, and accessibility checks. |
| [Develop iPhone Duo Apps](develop-iphone-duo-apps/SKILL.md) | Build or adapt SwiftUI and UIKit apps for dual displays, fold-aware layouts, vertical bars, camera transitions, and Duo testing. |

## Install

Choose a skill and paste its installation prompt into Codex to use the built-in skill installer.

**Apple App Review Guidelines**

```text
$skill-installer install https://github.com/mteinum/skills/tree/main/apple-app-review-guidelines
```

**Apple Human Interface Guidelines**

```text
$skill-installer install https://github.com/mteinum/skills/tree/main/apple-human-interface-guidelines
```

**Develop iPhone Duo Apps**

```text
$skill-installer install https://github.com/mteinum/skills/tree/main/develop-iphone-duo-apps
```

Codex detects newly installed skills automatically. If a skill does not appear, restart Codex.

## Use

Mention an installed skill in your prompt and describe the task. For example:

**Apple App Review Guidelines**

```text
$apple-app-review-guidelines Review this app for App Store submission readiness and identify issues with evidence and suggested fixes.
```

**Apple Human Interface Guidelines**

```text
$apple-human-interface-guidelines Review this SwiftUI screen for navigation, accessibility, and Apple platform conventions.
```

**Develop iPhone Duo Apps**

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

## License

Licensed under the [MIT License](LICENSE).

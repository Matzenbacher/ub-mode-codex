# ub-mode: Codex marketplace catalog (unofficial)

This repository is an independent, unofficial adaptation of the `ub-mode` workflow
originally published by **Robert C. Martin (Uncle Bob)**. Original source:
https://github.com/unclebob/ub-mode/blob/master/SKILL.md

This project is not affiliated with or endorsed by the upstream author. The
upstream README also acknowledges influence from @poteto. See
`plugins/ub-mode/skills/ub-mode/references/ATTRIBUTION.md`.

## Add this GitHub repository as a Codex marketplace

To add this published repository to Codex, run:

```sh
codex plugin marketplace add Matzenbacher/ub-mode-codex
codex plugin marketplace list
codex plugin add ub-mode@ub-mode-community
codex plugin list
```

Alternatively, add the locally extracted directory for testing:

```sh
codex plugin marketplace add /ABSOLUTE/PATH/TO/ub-mode-codex-marketplace
codex plugin add ub-mode@ub-mode-community
```

In the ChatGPT desktop app, restart the app, open Plugins Directory, select
`ub-mode (unofficial)` from the marketplace sources, and install the plugin.

## Install ub-mode as a standalone Codex skill

The **same workflow** is also published as a standalone skill at
[`.agents/skills/ub-mode`](.agents/skills/ub-mode/SKILL.md).

It can be installed without installing this marketplace or the plugin.

In a Codex conversation, ask the built-in skill installer:

```text
$skill-installer install https://github.com/Matzenbacher/ub-mode-codex/tree/main/.agents/skills/ub-mode
```

For a manual, user-wide installation:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Matzenbacher/ub-mode-codex.git /tmp/ub-mode-codex
cp -R /tmp/ub-mode-codex/.agents/skills/ub-mode ~/.agents/skills/
```

Then open a new Codex session (restart if the skill does not show up) and
invoke it as `$ub-mode` in a prompt, or inspect `/skills`.

For repo-only usage, keep the `.agents/skills/ub-mode` folder in the
repository where Codex runs. Installing both the plugin and standalone skill
may show two entries named `ub-mode`; choose one installation mechanism to
avoid duplicate activation.

The standalone skill is an **unofficial adaptation** and keeps upstream author
credits and quality-tool limitations in its `references/` directory.

## Contents

- `.agents/plugins/marketplace.json` : Codex marketplace catalog
- `plugins/ub-mode/plugin.json` : portable Agent Plugins manifest
- `plugins/ub-mode/skills/ub-mode/SKILL.md` : adapted developer workflow
- `plugins/ub-mode/skills/ub-mode/references/` : quality checks and attribution

This catalog is for local or Git-sourced installation, **not** a substitute for
the official OpenAI public Plugins Directory review and publication process.
For official publication, submit the plugin-only ZIP (not this repository ZIP)
through https://platform.openai.com/plugins after completing the publisher
identity and listing requirements.
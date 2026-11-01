# ub-mode (unofficial plugin adaptation)

**Plugin name:** `ub-mode`  
**Original workflow:** Robert C. Martin (Uncle Bob),
[unclebob/ub-mode](https://github.com/unclebob/ub-mode).  
**Status:** Unofficial, independent adaptation. **Not endorsed** by the author.

This is a **skills-only Agent Plugins 1.0 package**, intended for ChatGPT/Codex
plugin import or another compatible host. It does not contain an executable
MCP server, a UI, or the external quality-check tools.

## Behavior

When activated, the skill uses the three-stage sequence established by the
upstream project:

1. **First Make it Work**: define checkable behavior, test first where honest
   and feasible, and implement the smallest effective change.
2. **Then Make it Right**: repair causes, refactor safely and attempt
   deterministic quality checks with Crapper, Dryer and Mutator if available.
3. **Practice**: keep an action log, preserve repository integrity and make
   commits/pushes only with explicit authorization.

This adaptation adds safety boundaries for repository mutations and explicit
handling of checks that could not be run. It does not claim to reproduce
or include the original instructions word for word.

## Files

- `plugin.json`: Agent Plugins 1.0 identity and listing metadata.
- `skills/ub-mode/SKILL.md`: independently drafted operating instructions.
- `skills/ub-mode/agents/openai.yaml`: skill display and invocation metadata.
- `skills/ub-mode/references/QUALITY_GATES.md`: links and limitations for
  quality-gate tools.
- `skills/ub-mode/references/ATTRIBUTION.md`: origin, acknowledgements and
  copyright caution.

## Installation

Import the `ub-mode.zip` package using an Agent Plugins 1.0-compatible plugin
import flow. This build has **not** been automatically installed into an
account or published publicly.

For a standalone skill-capable agent where plugins are not supported, the
skill file may instead be placed under the host's agent skills directory as
`ub-mode/SKILL.md`, provided the host supports that convention. Follow your
host's current installation guide. The source project also documents its
own single-skill installation instructions.

## Examples

- `@ub-mode Refatore este módulo sem alterar comportamento externo.`
- `/ub-mode Corrija este bug com teste de regressão.`
- `Revise este PR com os critérios de qualidade do ub-mode e mostre o log.`

The actual invocation syntax depends on the host; these examples describe
intent, not a guaranteed command registration.

## Acknowledgements

Original `ub-mode` author: **Robert C. Martin (Uncle Bob)**,
https://github.com/unclebob/ub-mode.

The original README credits **@poteto** as an influence on the
`poteto-mode` / `pstack` rule set: https://github.com/poteto.

Quality tools referenced by the original project:
https://github.com/unclebob/crapper,
https://github.com/unclebob/dryer,
https://github.com/unclebob/mutator, and
https://github.com/unclebob/uml-viewer.

**Copyright and license note:** The inspected upstream repository did not
publish a license. This package contains independently drafted guidance, not
a redistribution of its original full SKILL.md text. See
`skills/ub-mode/references/ATTRIBUTION.md`.

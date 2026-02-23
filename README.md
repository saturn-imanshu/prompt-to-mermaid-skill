# prompt-to-mermaid

A Claude Code skill that turns vague ideas into clear requirements and a Mermaid diagram that serves as a machine-readable spec for implementation.

## What It Does

The skill operates in three phases:

1. **Requirement Clarification Loop** -- Asks one clarifying question at a time until all ambiguities about actors, data flows, decisions, and edge cases are resolved. Produces a confirmed requirements summary before any diagram work begins.

2. **Mermaid Diagram Generation with Iteration** -- Auto-detects the best diagram type for the requirements (flowchart, sequence, state, ER, or class diagram), generates the Mermaid code, and iterates with the user until the diagram is approved.

3. **Save and Context Loading** -- Saves the approved `.mmd` file and requirements summary to `docs/diagrams/`, then provides instructions for loading the diagram into future sessions as a machine-readable blueprint.

### Superpowers Integration

This skill integrates with `superpowers:brainstorming` and `superpowers:writing-plans`. When those skills complete, prompt-to-mermaid offers to generate a diagram from the existing design or plan document, skipping the clarification phase entirely since requirements are already established.

### Auto-Detected Diagram Types

- **flowchart** -- process flows, decision trees, feature workflows
- **sequenceDiagram** -- multi-actor interactions, API call chains
- **stateDiagram-v2** -- lifecycle states, status transitions
- **erDiagram** -- data models, entity relationships, database schemas
- **classDiagram** -- component architecture, module dependencies

## Install

```
npx skills add saturn-imanshu/prompt-to-mermaid-skill
```

### Manual Install

Clone or download this repository and symlink it into your skills directory:

```
ln -s /path/to/prompt-to-mermaid-skill ~/.claude/skills/prompt-to-mermaid
```

## How It Works

1. User describes an idea or a superpowers skill hands off a completed design/plan.
2. If standalone: the skill asks clarifying questions one at a time until requirements are unambiguous.
3. If from superpowers: the skill reads the existing design/plan document and skips clarification.
4. The skill auto-detects the optimal Mermaid diagram type based on the requirements.
5. A Mermaid diagram is generated and presented for review.
6. The user requests revisions or approves the diagram.
7. User chooses output format: `.mmd` (raw Mermaid) or `.md` (fenced code block for IDE/GitHub preview).
8. The approved diagram and requirements summary are saved to `docs/diagrams/`.
9. The user is prompted to load the diagram into future sessions for implementation.

## Cross-Agent Compatibility

This skill works with any AI coding agent that supports the skills protocol, including Claude Code, Cursor, GitHub Copilot, and OpenAI Codex.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting changes.

## License

MIT

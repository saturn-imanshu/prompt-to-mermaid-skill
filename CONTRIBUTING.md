# Contributing to prompt-to-mermaid

Contributions are welcome. Whether it is a bug fix, improved question logic, or support for a new diagram type, your help makes this skill better.

## How to Contribute

1. Fork the repository.
2. Clone your fork locally.
3. Create a feature branch: `git checkout -b my-change`.
4. Make your changes.
5. Test your changes (see Testing below).
6. Commit with a clear message describing what you changed and why.
7. Push to your fork and open a pull request against `master`.

## Skill File Conventions

The core of this skill lives in `SKILL.md`. If you modify it, follow these conventions:

- The file must begin with YAML frontmatter containing `name` and `description` fields.
- The `description` field must start with "Use when..." and stay under 500 characters.
- Keep instructions specific and actionable. Avoid vague guidance that leaves room for misinterpretation.
- Diagram generation rules, clarification checklists, and phase definitions should remain clearly separated.

## Testing

There is no automated test suite for skills. To test your changes:

1. Symlink the skill into your local skills directory:
   ```
   ln -s /path/to/prompt-to-mermaid-skill ~/.claude/skills/prompt-to-mermaid-skill
   ```
2. Open a Claude Code session.
3. Trigger the skill by describing a system you want to build (e.g., "I want to build a task queue with retries").
4. Verify that the clarification loop asks relevant questions, the diagram type is correctly detected, the generated Mermaid syntax is valid, and the save path is correct.
5. If testing superpowers integration, run a `superpowers:brainstorming` or `superpowers:writing-plans` session first and confirm the skill offers diagram generation at the handoff point.

## What Makes a Good Contribution

- **Bug fixes**: Incorrect Mermaid syntax, broken phase transitions, or missed edge cases.
- **Improved clarification questions**: Better heuristics for identifying ambiguities in user descriptions.
- **Better diagram generation rules**: More precise node labeling, smarter type detection, improved layout conventions.
- **New diagram type support**: Adding support for Mermaid diagram types not yet covered (e.g., Gantt, pie, gitGraph).
- **Documentation improvements**: Clearer instructions, better examples, fixing inaccuracies.

## Code of Conduct

- Be respectful in all interactions.
- Provide constructive feedback on pull requests.
- Focus discussion on the technical merits of changes.
- Assume good intent from other contributors.

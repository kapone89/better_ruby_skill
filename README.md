# better_ruby_skill

A final review pass for Ruby code written by an agent. It catches Ruby-specific mistakes and code that works but reads like a direct translation from another language. It is not a linter.

## Enable in OpenCode

1. Keep this checkout at `~/.agents/skills/better_ruby_skill` so OpenCode discovers [`SKILL.md`](SKILL.md).
2. Copy [`opencode/ruby-idiom-reviewer.md`](opencode/ruby-idiom-reviewer.md) to `~/.config/opencode/agents/ruby-idiom-reviewer.md` for all projects, or to `.opencode/agents/ruby-idiom-reviewer.md` in a Ruby project.
3. Add this to the Ruby project's `AGENTS.md` (or your global OpenCode `AGENTS.md` to apply it across projects):

```markdown
- After Ruby changes and initial checks, launch a fresh `ruby-idiom-reviewer` subagent.
  Send only this task's Ruby diff (including new files), not chat or unrelated edits.
  Wait for findings; apply appropriate fixes and rerun checks. Report any review gaps.
```

OpenCode skills don't run as hooks; the instruction above tells the coding agent when to delegate. The reviewer gets a fresh session, not the parent's conversation, and can load only this skill. OpenCode still supplies its normal ambient instructions.

OpenCode accepts `better_ruby_skill` as an ID. To distribute it as a strict [Agent Skills](https://agentskills.io/specification.md) package, use `better-ruby-skill` for both the directory and the frontmatter `name`, and update the reviewer accordingly.

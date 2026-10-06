# code-flow

A thinking discipline for any code change in Claude Code: **Discover → Execute → Verify**.

## Install

```bash
/plugin marketplace add AerionDyseti/aeriondyseti-plugins
/plugin install code-flow@aeriondyseti-plugins
```

## Skills

| Skill | Triggers On |
|-------|-------------|
| **Getting Started** | Start of every conversation — routes to the right phase of the flow |
| **Discover** | Before any code change (feature, bug fix, refactor, tech debt) — explores the problem and produces a spec that gates execution |
| **Execute** | An approved spec from Discover — orchestrates implementation, parallel or serial, with guardrails |
| **Verify** | Execution complete, before shipping — correctness, code quality, review, and architectural feel |

## Agents

| Agent | Purpose |
|-------|---------|
| **Code Architect** | Designs architecture for new features — analyzes patterns, produces blueprints |
| **Code Explorer** | Deep understanding of a feature or subsystem before making changes |
| **Code Reviewer** | Reviews completed work against requirements and coding standards |
| **Code Simplifier** | Simplifies and refines code for clarity and maintainability |

## License

MIT

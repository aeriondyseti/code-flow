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

## Releasing

Always release with [plugin-kit](https://github.com/aeriondyseti/plugin-kit)'s `release` command. It bumps the version, tags the release, and pins this plugin's entry in the [aeriondyseti-plugins](https://github.com/aeriondyseti/aeriondyseti-plugins) marketplace to that exact tag and commit in one step, so the published plugin never drifts from this repo. Don't bump versions, create tags, or edit the marketplace entry by hand.

1. Add your changes under `## [Unreleased]` in `CHANGELOG.md` and commit them. `release` refuses to run with an empty `[Unreleased]` section or a dirty tree.
2. Optionally run `npx @aeriondyseti/plugin-kit doctor` to catch anything that would break the plugin once installed.
3. From this repo, with the marketplace repo cloned alongside it (adjust the path if yours lives elsewhere), preview and then release:

   ```bash
   npx @aeriondyseti/plugin-kit release patch --plugin . --marketplace ../aeriondyseti-plugins/.claude-plugin/marketplace.json --dry-run
   npx @aeriondyseti/plugin-kit release patch --plugin . --marketplace ../aeriondyseti-plugins/.claude-plugin/marketplace.json
   ```

   Use `patch`, `minor`, `major`, or an explicit `x.y.z`. This bumps `.claude-plugin/plugin.json`, moves `[Unreleased]` under the new version in `CHANGELOG.md`, commits `Release x.y.z`, tags `vx.y.z`, and updates `ref`, `sha`, and `version` in the marketplace entry. It never pushes.
4. Push this repo first: `git push origin main --follow-tags`.
5. Then commit and push the marketplace change. Pushing it first would pin a commit GitHub doesn't have yet, and installs would fail.

## License

MIT

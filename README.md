<!-- PORTFOLIO-BANNER:START -->
> **🗂️ Portfolio archive — Claude Code hooks toolkit (JS/shell).** Hooks that guard against common failure modes in autonomous development. Part of a consolidated set of my personal repositories and **not actively maintained**.

<details>
<summary><b>📋 Self-review — 5 good practices &amp; 5 things I'd improve</b></summary>

**✅ Good practices demonstrated**
1. Clear problem framing — six named failure modes the hooks are designed to prevent.
2. LICENSE present.
3. Organised `hooks` / `scripts` / `templates` / `docs` layout.
4. Focused, single-responsibility scope.
5. Documented rationale for each hook.

**⚠️ Weaknesses / what I'd do differently today**
1. Very small (≈13 files, a handful of commits) — proof-of-concept stage.
2. No tests or CI exercising the hooks.
3. Hooks are workflow/environment-specific, which limits reuse.
4. No versioning or release process.
5. README claims ("bulletproof") run ahead of demonstrated validation.

</details>

---
<!-- PORTFOLIO-BANNER:END -->


# Claude Autonomous Hooks

Bulletproof hooks for autonomous development with Claude Code.

## What It Does

Prevents 6 common failure modes in autonomous development:

1. **Context rot** → Agents must include spec references
2. **Quality gate skipping** → PreToolUse blocks delegation without quality gates
3. **Git warnings** → PostTask checks for uncommitted changes
4. **Transient artifacts** → ArtifactTracker tracks created scripts
5. **Doc summarization** → PreEdit warns before editing VERBATIM sections
6. **CLAUDE.md rewriting** → VERBATIM protection for critical sections

## What You Get

4 hooks that enforce quality:

- **PreToolUse** - Blocks Task delegation without quality gates + spec + delivery plan path
- **PostTask** - Prompts for code review after tasks, checks git commits + delivery plan updates
- **PreEdit** - Warns before editing VERBATIM sections
- **ArtifactTracker** - Tracks created scripts for wrap-up review

## Quick Install

```bash
git clone https://github.com/martincjarvis/claude-autonomous-hooks.git
cd claude-autonomous-hooks
./scripts/install.sh
```

See [INSTALLATION.md](docs/INSTALLATION.md) for detailed instructions.

## How It Works

### Task Delegation Flow

When you delegate a task to a subagent:

1. **PreToolUse** verifies you included:
   - Quality gates (copied VERBATIM from delivery plan)
   - Spec reference (full requirements, not summaries)
   - Delivery plan path

2. **Subagent** completes the task with full context

3. **PostTask** prompts you to review:
   - Minimal changes check
   - Best practices check
   - Quality gate check
   - Git status check
   - Delivery plan update check

### VERBATIM Protection

When editing documentation, PreEdit warns you before editing VERBATIM sections:

```html
<!-- VERBATIM: Critical Content -->
This content must be preserved exactly
<!-- END VERBATIM -->
```

## Documentation

- [INSTALLATION.md](docs/INSTALLATION.md) - How to install
- [CONFIGURATION.md](docs/CONFIGURATION.md) - Settings and configuration

## Templates

- [CLAUDE-execution-protocol.md](templates/CLAUDE-execution-protocol.md) - Add to your CLAUDE.md
- [delivery-plan-template.md](templates/delivery-plan-template.md) - Example delivery plan

## Optional Tools

For best results, install:

- **QMD**: `bun install -g https://github.com/tobi/qmd` - Semantic doc search
- **grepai**: `go install github.com/yoanbernabeu/grepai@latest` - Semantic code search

See [CONFIGURATION.md](docs/CONFIGURATION.md) for details.

## License

MIT

## Contributing

Contributions welcome! Please open an issue or PR.

## Author

Created by Martin Jarvis ([@martincjarvis](https://github.com/martincjarvis))

## See Also

- [Claude Code](https://claude.ai/claude-code) - Official Claude Code documentation
- [Superpowers](https://github.com/anthropics/claude-code-superpowers) - Claude Code workflows
- [oh-my-claude](https://github.com/pogosmart/oh-my-claude) - Claude Code extensions
# hwlab — Project Instructions

This file is for AI sessions. Human-oriented documentation is in README.md.

## Installation Guidance

When a user mentions installing, deploying, or using this plugin, first run `scripts/install.sh --status` to check the current installation status, then explain the three installation methods and guide the user to choose:

- Global install: skill (and agent) copied to `~/.claude/skills/` (or `~/.codex/skills/`), available in all projects, but hooks do not activate.
- --plugin-dir: `claude --plugin-dir /path/to/hwlab`, skill + agent + hooks all available, path must be specified on each launch.
- Marketplace: publish the repository and use `claude plugin marketplace add <your-org>/hwlab && claude plugin install hwlab-hardware-solution` for official distribution.

After the user confirms, run the corresponding command:

```bash
# Global install (Claude Code, including agent)
scripts/install.sh --global --platform claude

# Global install (Codex)
scripts/install.sh --global --platform codex

# --plugin-dir (single session, full functionality)
claude --plugin-dir /path/to/hwlab

# Uninstall global install
scripts/install.sh --uninstall

# Show installation status
scripts/install.sh --status
```

## Core Rules

- Invoke `$hardware-solution` to enter the hardware solution design flow.
- Component parameters must come from datasheets or distributor pages; never answer from memory.
- Every key choice must explain the trade-offs; do not merely list parts.
- The risk list must not be empty; high-risk items must have verification actions.
- Before final delivery the proposal must pass the gates in `skills/hardware-solution/references/verification-gates.md`.

## Key Files

- `skills/hardware-solution/SKILL.md` — Skill entry point and workflow definition
- `skills/hardware-solution/references/` — Workflow, output template, review checklists, supply-chain risk, verification gates
- `agents/hardware-reviewer.md` — Independent reviewer agent (5-dimension scoring)

## Development Validation

After modifying the skill or references, run:

```bash
python3 tests/validate.py
```

## Contribution Guidelines

- Changes to skill or reference documents must include a before/after comparison.
- New reference documents must be linked from the workflow section of SKILL.md.
- Changes without validation against a real hardware design scenario will not be accepted.
- Ensure `python3 tests/validate.py` passes before submitting.

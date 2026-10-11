# hwlab — Project Instructions

This file is for Cursor Agent Mode and other general agents. Content is consistent with CLAUDE.md.

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

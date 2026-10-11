## Pre-submission Checklist

- [ ] `python3 tests/validate.py` passes
- [ ] Searched existing PRs to confirm no duplicates

## Change Description

**Problem solved:**
<!-- Describe the specific problem or requirement this PR solves; hypothetical improvements are not accepted -->

**What was changed:**
<!-- List which files were modified and what was done -->

**Before/after comparison:**
<!-- For changes to skill or reference documents, provide before/after comparison of key content -->

## Verification

**Verification method:**
<!-- Explain how the correctness of this change was verified -->

- [ ] `python3 tests/validate.py` all pass
- [ ] Tested in a real hardware design scenario (if applicable)
- [ ] Hook output verification passed (if hooks were modified)

## Notes

- Changes to skill or reference documents must include a before/after comparison
- New reference documents must be linked from the workflow section of SKILL.md
- Changes without validation against a real hardware design scenario will not be accepted
- For version changes use `scripts/bump-version.sh <new-version>`

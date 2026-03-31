# Signal Capture Protocol

> How to extract improvement signals from a session where a skill was used.

---

## Extraction Patterns

When reviewing a session for skill-related signals, look for these conversation patterns:

### Correction Signals

**Explicit corrections:**
- "No, not that — do X instead"
- "That's wrong, it should be..."
- "Don't do X, I've told you before..."
- Human edits the output and sends it back
- Human rejects a draft and provides direction

**Implicit corrections:**
- Human takes a different approach than what the skill produced
- Human adds steps that the skill should have included
- Human removes content the skill generated (over-production)

**What to capture:** The before state, the after state, and *why* the correction was needed. The "why" determines whether this is a skill gap (missing instruction) or a context gap (missing information).

### Workaround Signals

**Indicators:**
- Human says "let me fix that manually"
- Output requires reformatting before use
- Multiple iterations needed to get acceptable output
- Human applies a transformation the skill should have handled
- Post-processing steps that could be automated

**What to capture:** The manual step, what triggered it, and whether the skill could reasonably handle it automatically.

### Gap Signals

**Indicators:**
- Human asks for something the skill doesn't address
- The skill produces output that's correct but incomplete
- A follow-up question reveals missing coverage
- The human references external knowledge the skill should have incorporated
- Edge cases that the skill doesn't handle

**What to capture:** What was needed, whether it's a common case or edge case, and where in the SKILL.md it should be addressed.

### Success Signals

**Indicators:**
- Human accepts output without changes
- Human says "that's exactly right" or similar
- A pattern works consistently across multiple invocations
- The output is reused downstream without modification
- The skill's quality criteria correctly predicted output quality

**What to capture:** What worked, why it worked (if discernible), and whether it's codified in the SKILL.md or just happened to work this time.

### Context Miss Signals

**Indicators:**
- The skill produces output that's wrong because it lacked information
- Human has to paste in context that should have been auto-loaded
- The skill asks questions it should have been able to answer from existing files
- Output quality varies based on what context was manually provided

**What to capture:** What information was missing, where it lives (or should live), and whether it should be added to auto_load.

---

## Signal Severity

| Severity | Definition | Action |
|----------|------------|--------|
| **Blocking** | Skill produces incorrect or harmful output without this fix | Propose immediately, high priority |
| **Quality** | Skill works but output quality is consistently degraded | Capture in retro, medium priority |
| **Enhancement** | Skill works fine but could be better | Capture in retro, low priority |
| **Observation** | Interesting pattern, not yet actionable | Note in raw notes section |

---

## Anti-Patterns (What NOT to Capture)

- **One-off context issues** — If the problem was unique to this specific input and unlikely to recur, don't add a skill rule for it.
- **Style preferences already in VOICE.md** — Don't duplicate voice rules into every skill. Reference VOICE.md instead.
- **Platform limitations** — If the issue is a Claude capability limit (not a skill design issue), don't try to fix it in the skill.
- **User error** — If the human gave unclear instructions and the skill responded reasonably, that's not a skill gap.

---

## Attribution

When writing retro entries, note the source of each signal:
- **Session date** — when it happened
- **Skill invocation** — which trigger/command started the skill
- **Signal type** — correction / workaround / gap / success / context miss
- **Confidence** — how certain you are this is a real pattern vs. noise
  - After 1 occurrence: note as observation
  - After 2 occurrences: flag as likely pattern
  - After 3+ occurrences: treat as confirmed pattern, propose fix

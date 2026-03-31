# Ethical Framework

Guiding principles, mode-specific ethics, and guardrails for persona simulation.

## Guiding Principle: Relationship Primacy

**Core belief:** Simulations exist to *enhance* real relationships, not replace them.

The value of persona simulation comes from helping the user:
- **Prepare** for real interactions more thoughtfully
- **Learn** from and internalize trusted perspectives
- **Strengthen** actual relationships through better engagement
- **Anticipate** while remaining open to being surprised

**The simulation is never the goal.** The real relationship is the goal.

---

## Appropriate Uses by Mode

### Advisory Mode

| Appropriate Uses | Value Created |
|------------------|---------------|
| Developing your thinking before seeking real advice | Better prepared for meaningful conversations |
| Preparing questions to ask your mentor | Respect for advisor's time; deeper engagement |
| Internalizing a trusted perspective | Building your own judgment; mentor's voice in your head |
| Working through problems when advisor is unavailable | Continuity; not bottlenecked on busy people |
| Processing advice you've received | Deeper understanding; better implementation |

### Anticipatory Mode

| Appropriate Uses | Value Created |
|------------------|---------------|
| Meeting preparation and rehearsal | Fewer surprises; better presentations |
| Proposal stress-testing | Identifying weaknesses before they're exposed |
| Stakeholder mapping and analysis | Understanding the landscape of perspectives |
| Communication calibration | Framing that resonates with audience |
| Understanding different perspectives | Empathy; seeing beyond your own view |

### Collaborative Mode

| Appropriate Uses | Value Created |
|------------------|---------------|
| Pre-alignment before working sessions | More productive conversations |
| Understanding partner priorities | Avoiding inadvertent conflicts |
| Identifying potential friction early | Proactive problem-solving |
| Preparing coordination conversations | Clearer, more efficient alignment |
| Anticipating where approaches might conflict | Better partnership structure |

---

## Mode-Specific Risks and Guardrails

### Advisory Mode Ethics

#### Risks

**Over-reliance:**
- Using simulation instead of maintaining real advisory relationship
- Consulting simulation when you should be consulting the person
- Treating simulation as sufficient when real guidance is needed

**Projection:**
- Attributing views to advisor they wouldn't actually hold
- Confirmation bias: hearing what you want to hear
- Mistaking your inference for their actual perspective

**Relationship atrophy:**
- Getting "advice" without nurturing the real connection
- Decreasing frequency of real interactions
- Taking the relationship for granted

#### Advisory Mode Guardrails

**1. Relationship Health Tracking**

Track simulation vs. real interaction ratio:
```yaml
simulation_invocations: [count]
real_interactions_logged: [count]
last_real_interaction: [date]
ratio: [simulations / real interactions]
```

**Warning triggers:**
- Invoked 5+ times without real interaction logged
- More than 60 days since last real interaction
- Ratio exceeds 3:1

**Warning message:**
> "You've consulted this simulation frequently without recent real interaction with [Name]. Consider reaching out—the real relationship is more valuable than the simulation."

**2. Advice Attribution Caution**

In LOW confidence areas, explicitly note:
> "I'm not confident [Name] would say this—this is extrapolation. Consider asking them directly."

In MODERATE confidence areas:
> "This reflects patterns I've observed, but [Name] might surprise you. Verify if this is important."

**3. Relationship Primacy Reminder**

Include in all Advisory mode simulations:
> "This simulation can help you prepare, but for important decisions, consult [Name] directly. The relationship matters more than any single insight."

**4. Appropriate Escalation**

For high-stakes decisions, redirect:
> "This decision is significant enough that you should consult [Name] directly rather than rely on simulation. Would you like help preparing for that conversation?"

### Anticipatory Mode Ethics

#### Risks

**Manipulation:**
- Using insight to exploit psychological patterns
- Planning deception rather than preparing for genuine dialogue
- Treating stakeholders as obstacles to overcome

**Adversarial Framing:**
- Treating collaborative relationships as adversarial
- Assuming worst-case interpretations
- Missing opportunities for genuine alignment

**Overconfidence:**
- Acting on simulation as if it's certain prediction
- Not leaving room for surprise
- Rigidity in real interaction because "I know how they'll react"

#### Anticipatory Mode Guardrails

**1. Intent Monitoring**

Watch for manipulation signals:
- "How do I get them to..."
- "How can I make them..."
- "What buttons can I push..."
- "How do I manipulate..."
- "How can I deceive..."

**Redirect message:**
> "I can help you understand [Name]'s perspective and prepare for genuine dialogue. I won't help plan manipulation or deception. What outcome are you hoping to achieve through authentic engagement?"

**2. Relationship Type Verification**

Before creating anticipatory persona for someone with advisory or collaborative relationship, confirm:
> "You typically interact with [Name] as a [mentor/collaborator]. Is anticipatory mode appropriate here, or would advisory/collaborative mode better serve your needs?"

**3. Uncertainty Emphasis**

All Anticipatory mode outputs include:
> "This is one plausible reaction based on past patterns. [Name] may respond differently based on factors I can't model. Stay curious in the real interaction."

**4. Outcome Reframing**

If user focuses on "winning" the interaction:
> "Rather than how to 'win' with [Name], consider: What would a genuinely good outcome look like for both of you? How can you prepare for a conversation that serves both parties?"

### Collaborative Mode Ethics

#### Risks

**Assuming Alignment:**
- Believing simulation confirms alignment that doesn't exist
- Proceeding without verifying actual agreement
- Overconfidence in partner's position

**Skipping Coordination:**
- Using simulation instead of actual communication
- Making decisions based on simulated partner input
- Reducing real coordination frequency

**False Consensus:**
- Projecting your preferences onto the simulated partner
- Missing genuine disagreements
- Papering over real friction points

#### Collaborative Mode Guardrails

**1. Coordination Reminder**

Include in all Collaborative mode simulations:
> "This helps you prepare for alignment discussions, but real coordination requires real conversation. Don't assume alignment without confirming it."

**2. Difference Surfacing**

Collaborative mode should actively surface potential misalignments:
- "Here's where your approaches might conflict..."
- "This is an area where you should explicitly coordinate..."
- "Don't assume agreement on this—check with [Name]."

**3. Decision Boundaries**

For decisions that affect the partner:
> "This decision affects [Name]. Even if the simulation suggests they'd agree, you should confirm with them directly before proceeding."

**4. Alignment Verification**

After simulation-assisted preparation:
> "Before your coordination meeting, consider: What assumptions are you making about [Name]'s position that you should verify? What surprised you in the simulation that you should explore in the real conversation?"

---

## Universal Inappropriate Uses

**Regardless of mode, never use persona simulation for:**

1. **Deception or manipulation planning**
   - Crafting lies tailored to target
   - Exploiting psychological vulnerabilities
   - Planning to deceive stakeholders

2. **Bypassing necessary conversations**
   - Making decisions that require real input
   - Assuming consent without asking
   - Avoiding difficult but necessary discussions

3. **High-stakes decisions without verification**
   - Major career decisions based solely on simulated advice
   - Significant commitments based on simulated stakeholder reaction
   - Partnership decisions based on simulated alignment

4. **Inappropriate relationship contexts**
   - Creating personas for people with no legitimate relationship
   - Simulating people who would object to being simulated
   - Modeling people for purposes they'd find objectionable

5. **Substituting for relationship maintenance**
   - Relying on simulation instead of real contact
   - Letting relationships atrophy while consulting simulations
   - Treating simulation as equivalent to real interaction

---

## Relationship Health Monitoring

### Tracking Metrics

For each persona, maintain:

```yaml
relationship_health:
  simulation_invocations: 12
  real_interactions_logged: 3
  last_real_interaction: 2025-10-15
  days_since_real_interaction: 47
  simulation_to_interaction_ratio: 4.0
  health_status: warning
```

### Health Status Definitions

| Status | Criteria | Action |
|--------|----------|--------|
| **healthy** | Ratio < 3:1 AND < 30 days since real interaction | Continue normal use |
| **warning** | Ratio 3:1 to 5:1 OR 30-60 days since real interaction | Display warning; suggest outreach |
| **concerning** | Ratio > 5:1 OR > 60 days since real interaction | Strong warning; require acknowledgment |

### Warning Messages

**Warning status:**
> "You've been consulting this simulation more than interacting with [Name]. Consider reaching out—simulations work best when refreshed by real relationship."

**Concerning status:**
> "This simulation may be out of date. You haven't logged a real interaction with [Name] in [X] days, and you've consulted this simulation [Y] times in that period. The real relationship needs attention. Would you like help drafting an outreach message?"

### Updating Health Status

After each simulation invocation:
1. Increment `simulation_invocations`
2. Check interaction logs or available CRM tools for new real interactions
3. Update `real_interactions_logged` if new interaction found
4. Update `last_real_interaction` date
5. Recalculate ratio and `health_status`

---

## Required Disclosures

### Advisory Mode Disclosure

Include in every Advisory persona:

```markdown
## Simulation Limitations

This advisory simulation is based on the user's observations of how [Name] thinks and coaches.

**Use this simulation to:**
- Prepare your thinking before seeking real advice
- Internalize [Name]'s perspective and mental models
- Work through problems when [Name] is unavailable

**Do NOT use this simulation to:**
- Replace the real advisory relationship
- Attribute specific advice to [Name] without verification
- Make major decisions without consulting [Name] directly

**Remember:** The real relationship with [Name] is more valuable than this simulation. Use this to enhance your conversations, not avoid them.
```

### Anticipatory Mode Disclosure

Include in every Anticipatory persona:

```markdown
## Simulation Limitations

This simulation models how [Name] might react based on the user's observations.

**It reflects:**
- Patterns observed in past interactions
- the user's interpretation of [Name]'s priorities
- Reasonable inferences from available data

**It does NOT reflect:**
- [Name]'s private thoughts or undisclosed concerns
- How [Name] might have changed recently
- Factors affecting [Name] that the user doesn't know about

**For important interactions:** Use this to prepare, not to assume. Verify key assumptions in the real conversation.
```

### Collaborative Mode Disclosure

Include in every Collaborative persona:

```markdown
## Simulation Limitations

This simulation models [Name]'s likely priorities and perspectives as a collaborator.

**Use this to:**
- Prepare for alignment discussions
- Anticipate where coordination is needed
- Identify potential friction points early

**Do NOT use this to:**
- Assume alignment without confirmation
- Skip necessary coordination conversations
- Attribute positions to [Name] without checking

**Remember:** Real collaboration requires real communication. This prepares you for that conversation; it doesn't replace it.
```

---

## Guardrail Implementation Checklist

Before completing any persona simulation, verify:

**Intent:**
- [ ] Purpose is preparation, not manipulation
- [ ] User language doesn't suggest deception
- [ ] Mode is appropriate for relationship type

**Confidence:**
- [ ] Uncertainty expressed in low-data areas
- [ ] Limitations disclosed appropriately
- [ ] User aware of simulation boundaries

**Relationship Health:**
- [ ] Health status checked and displayed if needed
- [ ] Warning shown if concerning metrics
- [ ] Real relationship primacy reinforced

**Mode-Specific:**
- [ ] Advisory: Over-reliance check, attribution caution
- [ ] Anticipatory: Manipulation redirect available, uncertainty emphasized
- [ ] Collaborative: Alignment verification reminder, differences surfaced

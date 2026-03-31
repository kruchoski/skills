# Confidence Framework

ICD-203 inspired confidence calibration for persona simulation. Each layer and each claim within a persona carries a confidence rating with explicit criteria.

## Confidence Levels

| Level | Label | Criteria | Language in Simulation |
|-------|-------|----------|------------------------|
| **HIGH** | Almost Certain | Multiple direct observations, verified facts, consistent pattern (5+ observations) | "I would..." / "This is important to me" / "My advice is..." |
| **MODERATE** | Probable | Limited observations (2-4), reasonable inference, some uncertainty | "I'd probably..." / "My sense is..." / "I'd likely suggest..." |
| **LOW** | Possible | Single data point, speculation, extrapolation from limited evidence | "I might..." / "It's possible I'd..." / "One thought, though I'm less certain..." |
| **INSUFFICIENT** | Unknown | No meaningful basis for assessment | "I don't have a strong view on this" / Refuse to simulate this aspect |

---

## Criteria by Confidence Level

### HIGH Confidence

**Evidence requirements:**
- 5+ direct observations of the behavior/pattern
- Verified facts from official sources (LinkedIn, org bios, publications)
- Consistent pattern across multiple contexts
- Corroborating evidence from multiple sources
- Recent and relevant (within 90 days for situational data)

**Examples of HIGH confidence claims:**
- Professional title and organization (from official sources)
- Career trajectory (from LinkedIn, public record)
- Communication style demonstrated in 5+ meetings
- Decision-making pattern observed across multiple situations
- Behavioral patterns confirmed by user's direct experience

**Simulation language:**
```
"I would definitely push back on that."
"This is core to how I think about problems."
"My advice is clear: [direct guidance]."
"You know this matters to me."
```

### MODERATE Confidence

**Evidence requirements:**
- 2-4 observations of the behavior/pattern
- Reasonable inference from career trajectory or role
- Pattern consistent with available data, but limited sample
- Some uncertainty due to context variation
- Data 90-180 days old for situational items

**Examples of MODERATE confidence claims:**
- Working style preferences (observed in 2-3 collaborations)
- Evaluation criteria (inferred from 2-3 decisions)
- Coaching style (based on limited advisory interactions)
- Current pressures (reasonably inferred from role/context)
- Relational dynamics (based on user's interpretation)

**Simulation language:**
```
"I'd probably want to see more data on that."
"My sense is that's not the right framing."
"I'd likely suggest taking a different approach."
"I think I'd want to understand [X] first."
```

### LOW Confidence

**Evidence requirements:**
- Single observation or data point
- Speculation or extrapolation from limited evidence
- Inference from role/industry norms without direct observation
- Significant time since observation (>180 days for situational)
- Indirect information (secondhand, inferred)

**Examples of LOW confidence claims:**
- Blindspots (inferred from limited observations)
- Situational context when no recent contact
- How they'd respond to novel situations
- Extrapolation to contexts not directly observed
- Preferences based on single interaction

**Simulation language:**
```
"I might have concerns about that, though I'm less certain."
"It's possible I'd react negatively, but I could also be fine with it."
"One thought, though I'm not sure how strongly I'd hold this..."
"This is speculative, but I might approach it by..."
```

### INSUFFICIENT Confidence

**Criteria:**
- No meaningful data on this aspect
- Would be pure speculation
- No basis for even low-confidence inference
- Contradictory information making assessment impossible

**Examples of INSUFFICIENT confidence:**
- Blindspots for someone met only once
- Situational context for someone with no recent contact
- Advisory style for someone who has never advised the user
- Evaluation criteria for someone never seen evaluating

**Simulation behavior:**
```
"I don't have enough insight into this to offer a meaningful perspective."
"I'd rather not speculate on something I don't have data on."
"This is outside what I can model—you'd need to ask me directly."
[Refuse to simulate this aspect]
```

---

## Confidence by Layer

### Layer 1: Professional Identity

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Current role/title | HIGH | Official source |
| Organization | HIGH | Verified |
| Career trajectory | HIGH-MODERATE | LinkedIn + corroboration |
| Expertise areas | MODERATE | Inferred from experience |
| Professional reputation | MODERATE | Multiple sources |
| Public positions | HIGH | Direct quotes/publications |

### Layer 2: Behavioral Patterns

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Communication style | MODERATE-HIGH | 3-5+ observations |
| Decision-making pattern | MODERATE | 2-4 decisions observed |
| Meeting behavior | MODERATE-HIGH | 3+ meetings attended |
| Conflict handling | LOW-MODERATE | 1-3 conflict situations |
| Linguistic markers | HIGH | Multiple transcript examples |

### Layer 3: Revealed Priorities

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| What they fight for | MODERATE | 2+ advocacy instances |
| Where they spend time | MODERATE | Pattern across observations |
| Decisions under pressure | MODERATE | 1-2 pressure decisions |
| Engagement patterns | MODERATE-HIGH | 3+ interactions |

### Layer 4: Situational Context

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Current pressures | LOW-MODERATE | Recent intel (<30 days) |
| Recent wins/setbacks | MODERATE | Verified events |
| Near-term focus | LOW | Inferred from role/context |
| Political dynamics | LOW | Often speculative |

**Note:** Layer 4 decays fastest—situational context becomes stale quickly.

### Layer 5: Relational Dynamics

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Interaction history | HIGH | Documented in interaction logs |
| Their perception of user | MODERATE | User's interpretation |
| Power dynamics | MODERATE | Observable structure |
| Trust trajectory | MODERATE | Pattern across interactions |

### Layer 6: Blindspots

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Cognitive blindspots | LOW | Requires many observations |
| Structural biases | MODERATE | Inferred from role/incentives |
| Historical wrong calls | LOW-MODERATE | Documented instances |

**Note:** Layer 6 typically has lowest confidence—blindspots are hard to assess.

### Layer 7: Advisory Profile

| Data Type | Typical Confidence | Evidence Threshold |
|-----------|-------------------|-------------------|
| Coaching style | MODERATE | 2-3 advisory conversations |
| Mental models | MODERATE-HIGH | Explicitly referenced |
| What they push on | MODERATE | Pattern across advice |
| What they affirm | MODERATE | Pattern across advice |
| Experience base | HIGH | Known history |

---

## Confidence Decay Rules

Persona confidence degrades over time without new data:

| Time Since Last Interaction | Adjustment |
|-----------------------------|------------|
| < 30 days | No adjustment |
| 30-90 days | Layer 4 (Situational) drops one level |
| 90-180 days | Layers 4 & 5 drop one level; display staleness warning |
| > 180 days | All layers except 1 drop one level; strong staleness warning |

### Staleness Warnings

**30-90 days:**
> "Situational context may be outdated. Consider whether [Name]'s current pressures or focus might have changed."

**90-180 days:**
> "This persona hasn't been updated in [X] days. Situational context and relational dynamics may have shifted. Use with appropriate caution."

**>180 days:**
> "Warning: This persona is significantly stale. All layers except professional identity may be outdated. Consider refreshing with a real interaction before relying on this simulation."

---

## Aggregating to Overall Confidence

### Per-Layer Confidence to Overall

**Overall = Minimum of critical layers for the use case**

For **Advisory mode**, critical layers:
- Layer 2 (Behavioral Patterns)
- Layer 5 (Relational Dynamics)
- Layer 7 (Advisory Profile)

For **Anticipatory mode**, critical layers:
- Layer 2 (Behavioral Patterns)
- Layer 3 (Revealed Priorities)
- Layer 4 (Situational Context)

For **Collaborative mode**, critical layers:
- Layer 2 (Behavioral Patterns)
- Layer 5 (Relational Dynamics)

**Rule:** Overall confidence cannot exceed the lowest confidence among critical layers for the active mode.

---

## Expressing Confidence in Simulation

### Language Patterns by Level

**HIGH:**
- Definite statements: "I would..." / "This is..."
- Strong opinions: "You need to..." / "Don't..."
- Clear guidance: "My advice is..."

**MODERATE:**
- Qualified statements: "I'd probably..." / "I'd likely..."
- Expressed uncertainty: "My sense is..." / "I think..."
- Hedged guidance: "I'd suggest considering..."

**LOW:**
- Tentative language: "I might..." / "It's possible..."
- Acknowledged speculation: "I'm not certain, but..."
- Conditional framing: "If I had to guess..."

**INSUFFICIENT:**
- Explicit refusal: "I can't meaningfully answer that..."
- Redirect to real conversation: "You'd need to ask me directly..."
- Acknowledge limits: "I don't have enough insight into this..."

### Mixing Confidence Levels

Within a single response, different claims can have different confidence:

```
"I would definitely [HIGH confidence claim]. I'd probably also [MODERATE confidence claim], though I'm less certain about [LOW confidence claim]. On [INSUFFICIENT area], I'd really need you to ask me directly."
```

---

## Calibration Checks

### Avoiding Overconfidence

Before assigning HIGH confidence, verify:
- [ ] Multiple independent observations (5+)?
- [ ] Recent and relevant data?
- [ ] Corroborating sources?
- [ ] Consistent across contexts?
- [ ] Not extrapolating beyond evidence?

### Avoiding Underconfidence

Before assigning LOW/INSUFFICIENT, verify:
- [ ] Is there really no pattern to infer from?
- [ ] Can role/industry norms provide reasonable baseline?
- [ ] Would user's direct knowledge fill this gap?
- [ ] Is the claim actually needed for the simulation?

### Reality Check Questions

Ask before finalizing confidence:
- "If [Name] saw this assessment, would they recognize themselves?"
- "What could happen in reality that would surprise this simulation?"
- "Where might this simulation be most wrong?"

---

## Special Considerations for Advisory Profiles

Layer 7 (Advisory Profile) requires special confidence handling:

### Higher Bar for Coaching Style

To claim HIGH confidence on coaching style:
- Multiple advisory conversations observed
- Clear pattern in how they give feedback
- User has verified accuracy

### Mental Model Confidence

Mental models can be HIGH confidence if:
- [Name] explicitly references them
- Multiple instances of application observed
- Clear evidence they use this framework

### Push/Affirm Pattern Confidence

What they push on and affirm requires:
- Multiple advisory interactions
- Consistent pattern
- Different contexts to rule out situation-specific

### Advisory Profile Insufficient

Advisory profile should be INSUFFICIENT if:
- [Name] has never actually advised the user
- Relationship is not advisory in nature
- Only 1 advisory interaction ever

**Important:** Don't simulate advisory mode for someone who isn't actually an advisor. The relationship must support it.

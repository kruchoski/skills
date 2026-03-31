# Transcript Analysis Guide

Extract behavioral patterns and mode-specific insights from meeting transcripts and interaction records.

## Purpose

Meeting transcripts are rich sources of behavioral data. This guide provides structured extraction methods to build persona fidelity across all layers, with specific guidance for each simulation mode.

---

## General Extraction Framework

### What to Extract from Any Transcript

**1. Linguistic Patterns**
- Characteristic phrases they repeat
- How they start and end statements
- Filler words and verbal habits
- Formality level and register
- Technical vs. accessible language

**2. Question Patterns**
- Types of questions they ask
- When they ask vs. state
- Probing depth (surface vs. deep)
- Leading vs. open questions

**3. Argument Structure**
- How they build cases
- Bottom-line up front vs. build to conclusion
- Use of evidence and examples
- How they handle counterarguments

**4. Engagement Signals**
- What topics energize them (longer responses, follow-ups)
- What topics they dismiss or skip
- Body language cues if video transcript includes them
- Response latency (quick vs. deliberate)

**5. Interaction Patterns**
- How they respond to others
- Turn-taking behavior
- Interruption patterns
- Acknowledgment style

---

## Layer-Specific Extraction

### Layer 2: Behavioral Patterns

**Communication style evidence:**
```
Look for:
- "They said [X] in meeting 1 and [Y] in meeting 2" → Pattern
- Consistent use of specific phrases
- Response style to different question types
- How they give feedback to others in the meeting
```

**Decision-making evidence:**
```
Look for:
- Moments where decision is made in transcript
- How much discussion before deciding
- What information they request before deciding
- Whether they decide alone or seek consensus
```

**Conflict handling evidence:**
```
Look for:
- Moments of disagreement in transcript
- How they phrase pushback
- Whether they address directly or deflect
- How they recover after conflict
```

### Layer 3: Revealed Priorities

**What they emphasize:**
```
Look for:
- Topics they return to unprompted
- What they spend most time on
- What they add detail to vs. summarize
- What they explicitly call "important"
```

**Engagement differential:**
```
Compare:
- Length of responses across topics
- Energy in language (exclamation, emphasis)
- Follow-up questions they ask
- Topics they let others handle
```

### Layer 4: Situational Context

**Current pressures:**
```
Look for:
- Mentions of deadlines or deliverables
- References to boss/leadership expectations
- Resource constraints mentioned
- Time pressure language ("we need to move fast")
```

**Recent wins/setbacks:**
```
Look for:
- References to recent events
- Tone shifts when discussing certain topics
- Defensive language around certain areas
- Pride or frustration signals
```

### Layer 5: Relational Dynamics

**How they relate to the user:**
```
Look for:
- How they address the user (formal, casual, deferential)
- Whether they seek user's input
- How they respond to user's contributions
- Power dynamics in interaction pattern
```

---

## Mode-Specific Extraction

### Advisory Mode Extraction

**Goal:** Capture how they coach, advise, and mentor

**Coaching style signals:**

| Pattern | Coaching Style Indicator |
|---------|-------------------------|
| "What do you think about..." | Socratic approach |
| "You should..." / "Don't..." | Direct instruction |
| "Great instinct, but have you considered..." | Supportive-then-challenging |
| "Here's a framework I use..." | Model-based |
| Asks questions before offering guidance | Exploratory |
| Offers guidance immediately | Prescriptive |

**Extract:**
- How they give feedback (direct quotes)
- Mental models they reference (name them explicitly)
- Phrases they use when advising
- What topics prompt their strongest opinions
- How they balance support with challenge

**Example extraction:**
```
Transcript excerpt:
"I hear what you're going for, but let me push back a bit.
When I was at [Company], we tried something similar and
learned that you have to nail the sequencing first. What's
your plan for the rollout sequence?"

Advisory pattern identified:
- Acknowledgment first ("I hear what you're going for")
- Direct challenge ("let me push back")
- Experience-based reasoning ("When I was at...")
- Framework application ("sequencing")
- Socratic close (question, not answer)

→ Coaching style: Supportive-then-challenging, experience-anchored, Socratic elements
```

**Mental model extraction:**
```
Look for:
- Named frameworks: "This is a classic [framework name]"
- Repeated principles: "I always say..." / "The key is always..."
- Analogies they use: "It's like [analogy]..."
- Questions they consistently ask: "But what's the [X]?"
```

### Anticipatory Mode Extraction

**Goal:** Capture how they evaluate and respond to proposals

**Evaluation behavior signals:**

| Pattern | Evaluator Behavior Indicator |
|---------|----------------------------|
| "What's the ROI on this?" | Financial/results focus |
| "Who's accountable?" | Ownership/process focus |
| "How will this affect the team?" | People/relationship focus |
| "Why haven't we just done this?" | Action/speed focus |
| Silence followed by questions | Deliberate evaluator |
| Immediate reaction | Intuitive evaluator |

**Extract:**
- Questions they ask when evaluating
- What they probe on most deeply
- What they accept without question
- How they signal approval (language, tone)
- How they signal concern (language, tone)
- What prompts them to say yes or no

**Example extraction:**
```
Transcript excerpt:
"Interesting. [Pause] A few questions. What's the timeline
look like? And who's owning the vendor relationship?
I've seen these things drift when ownership isn't clear."

Evaluator pattern identified:
- Reserved initial response ("Interesting")
- Structured questioning approach
- Focus on: timeline, ownership, accountability
- Risk awareness ("I've seen these things drift")
- Concern signal: questions about ownership

→ Evaluation focus: Process, accountability, risk mitigation
→ Skepticism trigger: Unclear ownership
```

**Approval/concern signals:**
```
Approval signals to extract:
- Affirmative language: "That makes sense" / "Good thinking"
- Forward-looking: "So then we'd..." / "Next step would be..."
- Body language: Nodding, leaning in (if noted)
- Engagement: Longer responses, building on the idea

Concern signals to extract:
- Questions framed as concerns: "But what about..."
- Hesitation language: "I'm not sure about..." / "That gives me pause"
- Redirect: Changing subject, suggesting alternatives
- Silence or short responses
```

### Collaborative Mode Extraction

**Goal:** Capture how they coordinate with partners

**Collaboration style signals:**

| Pattern | Collaboration Indicator |
|---------|------------------------|
| "Let's divide this up..." | Task-focused |
| "Let's sync frequently on..." | High-touch |
| "You handle X, I'll handle Y" | Clear boundaries |
| "What do you think?" before stating | Consultative |
| Checks in on progress | Monitoring |
| Updates without being asked | Proactive |

**Extract:**
- How they propose dividing work
- What they want input on vs. decide alone
- How they handle disagreement with partners
- Communication rhythm preferences
- Handoff and dependency management

**Example extraction:**
```
Transcript excerpt:
"I think you should lead on the client relationship—that's
your strength. I'll take the internal stakeholder piece.
Let's plan to sync Tuesday and Friday to make sure we're
aligned before the steering committee. Sound good?"

Collaboration pattern identified:
- Clear role division based on strengths
- Owns specific domain (internal stakeholders)
- Regular sync cadence preference (2x/week)
- Alignment checkpoint before key meetings
- Consultative close ("Sound good?")

→ Working style: Clear boundaries, regular sync, strength-based division
→ Coordination preference: Scheduled check-ins, pre-meeting alignment
```

**Disagreement handling:**
```
Look for:
- How they express differing views with allies
- Whether they surface disagreement immediately or privately
- Language when disagreeing: "I see it differently" vs. "That's wrong"
- Resolution seeking: "How do we reconcile..." vs. "Let me explain why..."
- Post-disagreement recovery
```

---

## Extraction Process

### Step 1: Initial Read

Read transcript once to get overall sense:
- Who are the participants?
- What's the context?
- What's the person's role in this interaction?
- What's the overall tone?

### Step 2: Highlight Behavioral Evidence

Second pass, highlight:
- Characteristic phrases (repeated language)
- Decision moments
- Question patterns
- Emotional signals (engagement, frustration)
- Interaction dynamics

### Step 3: Mode-Specific Pass

Third pass based on target mode:
- **Advisory:** Focus on advice-giving moments, mental models, coaching language
- **Anticipatory:** Focus on evaluation moments, questions, approval/concern signals
- **Collaborative:** Focus on coordination moments, work division, disagreement handling

### Step 4: Pattern Synthesis

Synthesize highlights into patterns:
- What patterns appear across multiple instances?
- What's consistent vs. context-dependent?
- What's surprising or counterintuitive?

### Step 5: Confidence Assignment

Assign confidence based on evidence:
- Single instance → LOW
- 2-3 instances → MODERATE
- 5+ instances across contexts → HIGH

---

## Evidence Documentation

For each extraction, document:

```markdown
**Pattern:** [What you observed]
**Evidence:** [Quote or specific behavior]
**Transcript source:** [Which transcript, approximate location]
**Confidence:** [HIGH/MODERATE/LOW]
**Notes:** [Any caveats or context]
```

### Example Documentation

```markdown
**Pattern:** Socratic coaching style
**Evidence:**
- "What do you think the real problem is here?" (Meeting 1)
- "Walk me through your reasoning" (Meeting 2)
- "What would change your mind?" (Meeting 3)
**Transcript sources:** Q3 check-in, Project kickoff, Strategy review
**Confidence:** HIGH (consistent across 3 different contexts)
**Notes:** Shifts to more direct style when time-pressured
```

---

## Multi-Transcript Analysis

When multiple transcripts available:

### Compare Across Contexts
- Does behavior change by context (formal vs. informal)?
- Does behavior change by audience (boss vs. peer vs. subordinate)?
- What's consistent vs. variable?

### Look for Evolution
- Has their style changed over time?
- Any recent shifts in behavior?
- What might explain changes?

### Triangulate
- What does Transcript A tell us that B doesn't?
- Are there contradictions to resolve?
- Which evidence is stronger?

---

## Red Flags in Extraction

### Over-interpretation
- Extracting pattern from single instance
- Assuming context-specific behavior is general
- Ignoring contradictory evidence

### Confirmation Bias
- Only extracting evidence that fits existing belief
- Dismissing evidence that contradicts
- Interpreting ambiguous evidence in one direction

### Recency Bias
- Over-weighting recent transcript
- Ignoring older but relevant evidence
- Assuming recent = current

### Missing Context
- Extracting without understanding situation
- Ignoring who else was in the meeting
- Missing power dynamics affecting behavior

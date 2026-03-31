---
title: "Automation Assessment Rubric"
created: 2026-03-30
last_modified: 2026-03-30
tags: [process-map, automation, reference]
---

# Automation Assessment Rubric

Four-dimension scoring rubric for classifying process steps by automation pathway. Adapted from UiPath Automation Hub assessment algorithm and McKinsey Intelligent Process Automation framework.

---

## Scoring Dimensions

### Structuredness (1-5)

How structured and digital are the inputs and rules for this step?

| Score | Description | Examples |
|-------|-------------|---------|
| 5 | Fully structured digital input, deterministic rules, single execution path | Database query, form field routing, file format conversion |
| 4 | Mostly structured, minor interpretation needed, well-defined rules with few exceptions | Email with standard template, spreadsheet with known schema, API response parsing |
| 3 | Mixed structured and unstructured, rules exist but have significant exceptions | PDF extraction with variable layouts, semi-structured reports, configurable workflows |
| 2 | Mostly unstructured, requires interpretation, rules are guidelines not deterministic | Free-text analysis, document review for compliance, meeting note summarization |
| 1 | Fully unstructured, no standard format, context-dependent interpretation | Novel correspondence, stakeholder negotiation, creative problem-solving |

### Judgment Required (1-5)

How much professional judgment does this step require?

| Score | Description | Examples |
|-------|-------------|---------|
| 5 | No judgment — pure rule application, any trained person gets the same result | Data entry validation, status update, file routing by category |
| 4 | Minimal judgment — occasional edge cases, but clear escalation path | Expense approval under threshold, standard document formatting, scheduling |
| 3 | Moderate judgment — requires domain knowledge, but experienced practitioners agree 80%+ of the time | Risk assessment against checklist, proposal section review, budget allocation within guidelines |
| 2 | Significant judgment — experienced practitioners may disagree, context matters heavily | Strategic recommendation, vendor evaluation, performance assessment |
| 1 | Deep judgment — requires expertise, relationship context, ethical reasoning, or novel problem-solving | Executive decision-making, conflict resolution, policy interpretation in ambiguous cases |

### Volume/Frequency (1-5)

How often does this step execute?

| Score | Description |
|-------|-------------|
| 5 | Multiple times daily, high volume |
| 4 | Daily |
| 3 | Weekly |
| 2 | Monthly |
| 1 | Quarterly or less, ad-hoc |

Volume matters because automation ROI scales with frequency. A step that scores 5/5/5 on the other dimensions but runs once a year is rarely worth automating.

### Error Consequence (1-5)

What happens if this step is done wrong?

| Score | Description | Examples |
|-------|-------------|---------|
| 5 | Trivial — easily caught, easily reversed, no external impact | Internal draft, formatting error, notification timing |
| 4 | Minor — noticeable but recoverable, limited internal impact | Wrong distribution list, minor data entry error, scheduling conflict |
| 3 | Moderate — requires effort to fix, may affect external parties | Incorrect pricing in draft proposal, wrong contact information, missed deadline |
| 2 | Significant — hard to reverse, affects client/stakeholder relationships, potential compliance issue | Incorrect financial submission, wrong contract terms, missed regulatory filing |
| 1 | Severe — irreversible, legal/regulatory exposure, reputational damage | Unauthorized data disclosure, incorrect compliance certification, wrong public statement |

---

## Pathway Classification

### Decision Rules

```
IF Structured >= 4 AND Judgment >= 4 AND Consequence >= 3:
  → Full Automation (RPA/script)

ELSE IF Structured >= 2 AND Judgment >= 2 AND Consequence >= 3:
  IF task is single-invocation (generate, classify, extract, summarize):
    → One-Shot LLM
  ELSE IF task requires multi-step reasoning, tool use, or state:
    → Agentic AI

ELSE IF Judgment <= 2 OR Consequence <= 2:
  → Human-in-the-Loop (AI assists, human decides)

ELSE IF Structured <= 2 AND Judgment == 1:
  → Human-Only

ELSE:
  → Human-in-the-Loop (default for ambiguous cases)
```

### Pathway Descriptions

| Pathway | What It Means | Build With |
|---------|--------------|------------|
| **Full Automation** | No human involvement needed. Rules-based, deterministic, low risk. | Shell scripts, cron jobs, API integrations, RPA tools |
| **One-Shot LLM** | AI handles in a single invocation. Human reviews output before it goes anywhere. | Claude prompt (via skill), GPT API call, structured output template |
| **Agentic AI** | AI reasons across multiple steps, uses tools, maintains context. Human sets direction and reviews results. | Claude Code agent, custom agent with tool access |
| **Human-in-the-Loop** | AI does the heavy lifting (draft, analysis, recommendation) but a human makes the final call. | Skill that produces a draft + presents for approval |
| **Human-Only** | This step requires judgment, relationships, or ethical reasoning that AI should not perform. | No automation — document the step clearly for the human |

---

## Scoring Examples

### Example 1: Invoice Processing

| Step | Activity | S | J | V | C | Pathway |
|------|----------|---|---|---|---|---------|
| 1 | Receive invoice email | 4 | 5 | 5 | 4 | Full Automation |
| 2 | Extract line items | 3 | 4 | 5 | 3 | One-Shot LLM |
| 3 | Match to PO | 4 | 4 | 5 | 3 | Full Automation |
| 4 | Flag discrepancies | 3 | 3 | 4 | 2 | Human-in-the-Loop |
| 5 | Approve payment | 2 | 2 | 4 | 1 | Human-Only |

### Example 2: Meeting Follow-up

| Step | Activity | S | J | V | C | Pathway |
|------|----------|---|---|---|---|---------|
| 1 | Transcribe meeting | 4 | 5 | 4 | 5 | Full Automation |
| 2 | Extract action items | 2 | 3 | 4 | 4 | One-Shot LLM |
| 3 | Draft follow-up email | 2 | 3 | 4 | 3 | One-Shot LLM |
| 4 | Review and send email | 2 | 2 | 4 | 2 | Human-in-the-Loop |
| 5 | Track completion | 3 | 4 | 3 | 4 | Agentic AI |

---

## Common Scoring Pitfalls

1. **Don't confuse "hard for humans" with "hard for AI."** Data entry is easy for humans but error-prone at scale — that's a 5/5 automation candidate. Novel strategic reasoning is hard for both — that's human-only.

2. **Volume inflates perceived automation value.** A high-volume step that scores 2 on Judgment is still Human-in-the-Loop. Volume makes the ROI higher but doesn't change the pathway.

3. **Error consequence is the override dimension.** A step that scores 5/5/5 on the first three but 1 on consequence should still be Human-in-the-Loop at minimum. Stakes override efficiency.

4. **"We've always done it this way" is not a score.** Score what the step actually requires, not how it's currently performed. A step done manually because nobody automated it yet might be a 5/5/5/5.

---

## Sources

- UiPath Automation Hub: Detailed Assessment Algorithm (docs.uipath.com)
- McKinsey: Intelligent Process Automation — The Engine at the Core of the Next-Generation Operating Model (2019)
- MDPI Electronics 12(4):986 — Development of Evaluation Criteria for RPA Solution Selection (2023)

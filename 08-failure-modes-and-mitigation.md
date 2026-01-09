# Failure Modes & Mitigations

This document outlines known failure modes in AI-assisted CRM systems and the design choices used to mitigate them.

The goal is not to eliminate failure, but to ensure failures are:
- Detectable
- Contained
- Non-destructive

---

## 1. Hallucinated Insights

### Description
The AI produces conclusions or signals that are not directly supported by the provided data.

### Example
- Inferring churn risk without explicit evidence
- Assuming dissatisfaction based on neutral interaction logs

### Mitigation
- Strict input-bound reasoning rules
- Mandatory `missing_information` field in outputs
- Conservative language enforced in prompt contracts
- Human review gate for all outputs

---

## 2. Overconfidence Bias

### Description
The AI assigns high confidence levels to outputs despite limited or ambiguous data.

### Example
- Marking confidence as `high` when historical data is incomplete
- Presenting speculative risks as definitive conclusions

### Mitigation
- Explicit confidence calibration rules in the prompt
- SOP-enforced rejection of unjustified `high` confidence
- Human escalation for low or ambiguous confidence scenarios

---

## 3. Schema Drift

### Description
Model outputs deviate from the expected JSON schema over time or across model versions.

### Example
- Missing required fields
- Introducing unexpected keys
- Switching to free-form text

### Mitigation
- Output schema validation layer
- Automatic rejection on schema mismatch
- Versioned prompt contracts
- Controlled model upgrades in sandbox environments

---

## 4. Model Volatility

### Description
Model behavior changes due to updates, deprecations, or provider-side modifications.

### Example
- Increased verbosity
- Changed reasoning style
- Different risk interpretation

### Mitigation
- Model tiering strategy
- Prompt version pinning
- Periodic regression testing using synthetic examples
- Fallback to alternate models or manual workflows

---

## 5. Misaligned Business Interpretation

### Description
The AI interprets signals without sufficient business context.

### Example
- Treating budget sensitivity as churn intent
- Flagging operational delays as contractual risk

### Mitigation
- AI restricted to signal surfacing, not interpretation
- Business logic remains outside AI scope
- Human validation required before action

---

## 6. Silent Failure

### Description
The system produces outputs that appear valid but are misleading or incomplete.

### Example
- No error thrown, but critical data omitted
- Outputs accepted without scrutiny

### Mitigation
- Mandatory logging of confidence and missing information
- SOP-driven review requirements
- Audit trail with prompt version and model metadata

---

## 7. Over-Automation Risk

### Description
Pressure to automate decisions leads to erosion of human oversight.

### Example
- AI outputs directly triggering operational actions
- Reduced review due to trust creep

### Mitigation
- Explicit prohibition of autonomous decision execution
- Human-in-the-loop as a system invariant
- SOP-enforced accountability boundaries

---

## Design Philosophy

Failures are expected in AI systems.

This system is designed so that:
- AI failures do not cascade
- Humans remain accountable
- Trust is earned gradually, not assumed

AI is treated as a probabilistic assistant, not a deterministic authority.

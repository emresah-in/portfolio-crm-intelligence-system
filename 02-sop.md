# SOP: CRM Intelligence Agent Usage & Governance

## Purpose
This SOP defines how the CRM Intelligence Agent is used, monitored, and governed within internal operations.
The agent is designed to support human decision-making, not replace operational or legal responsibility.

---

## Scope
This SOP applies to:
- Internal operations teams
- Account managers
- Analysts querying CRM data
- AI-assisted reporting workflows

It does NOT apply to:
- Automated decision execution
- Legal, financial, or compliance approvals
- Client-facing autonomous responses

---

## Role of AI in This System
AI is used for:
- Structuring unstructured CRM data
- Summarizing historical interactions
- Highlighting potential risks or signals
- Identifying missing or incomplete information

AI is explicitly NOT used for:
- Making binding decisions
- Modifying workflows or processes
- Creating or altering CRM records
- Interpreting legal or regulatory implications

---

## Input Requirements
Before invoking the AI agent, the following must be provided:
- Valid CRM record ID
- Relevant interaction logs and documents
- Clear user question or intent

If any of the above is missing, the agent must return a `missing_information` response.

---

## Output Interpretation Guidelines
AI output must always be reviewed by a human.

Key rules:
- `summary` is informational, not authoritative
- `risk_flags` are signals, not conclusions
- `confidence_level = low` requires manual verification
- Any recommendation must be validated against source data

---

## Escalation Rules
Escalate to a human reviewer when:
- Confidence level is low
- Risk flags include compliance, legal, or financial indicators
- Output references missing or outdated data
- AI response contradicts known business context

---

## Change Management
- Prompt changes must be versioned
- Any change to output schema requires SOP review
- Model changes must be tested in a sandbox environment
- All updates must be documented in `/docs/system-evolution.md`

---

## Audit & Accountability
- All AI interactions must be logged
- Prompt version used must be traceable
- Outputs must be reproducible when possible
- Final responsibility always remains with the human operator

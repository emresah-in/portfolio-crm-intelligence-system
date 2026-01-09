# CRM Intelligence System  
AI-Assisted, System-First, Production-Oriented

This repository demonstrates how I design and reason about AI systems in real business environments.

It is not a demo of the latest models.  
It is a representation of how AI should behave **inside a reliable system**.

---

## Why This Exists

Most AI initiatives fail not because models are weak,  
but because systems are built around hype instead of operations.

Common failure patterns I’ve seen repeatedly:
- AI added before workflows are clarified
- Over-automation without human accountability
- Model selection driven by trends, not constraints
- Impressive outputs that cannot be trusted in production

This project exists to show a different approach.

---

## Core Philosophy

AI is a **probabilistic component**, not a system.

In this project:
- AI is deliberately limited to a supporting role
- Human judgment remains the final authority
- Structure, data flow, and governance come before automation
- Failure is expected and explicitly designed for

In practice, this means:
- ~20% AI
- ~80% system design

---

## What This System Does

- Provides AI-assisted insights over CRM data
- Helps humans reason over historical records
- Surfaces signals, risks, and missing information
- Preserves auditability, traceability, and control

## What This System Does NOT Do

- It does not automate decisions
- It does not modify business logic
- It does not chase the “best” or newest model
- It does not replace human responsibility

---

## Design Highlights

- **JSON-based prompt contracts**  
  Prompts are treated as structured interfaces, not free-form text.

- **Model tiering over model hype**  
  Smaller, stable models are the default unless complexity truly demands more.

- **Human-in-the-loop by design**  
  Review gates are not optional or cosmetic.

- **Explicit SOPs and workflows**  
  AI behavior is constrained by operating rules, not assumptions.

- **Failure-first thinking**  
  Known failure modes are documented and mitigated at system level.

---

## Repository Contents

All artifacts live in a single context to reflect how systems are actually reasoned about.

- `prompt.json`  
  Structured prompt contract defining AI behavior and boundaries

- `sop.md`  
  Human + AI operating rules and governance

- `workflow.md`  
  End-to-end request flow with p latform-agnostic system diagram, validation, review, and logging

- `example-input.md`  
  Synthetic but realistic CRM input example

- `example-output-good.md`  
  Accepted AI output demonstrating conservative, safe behavior

- `example-output-bad.md`  
  Rejected AI output showing common failure patterns

- `example-output-bad-decision-log.md`  
  Human decision analysis explaining why the output was rejected

- `failure-modes-and-mitigation.md`  
  Known risks and the design choices used to contain them

---

## How to Read This Repo

If you want to understand how I think:
1. Start with this README
2. Review the prompt contract
3. Look at the SOP and workflow
4. Compare good vs bad outputs
5. Read the failure modes document

The value is not in any single file,  
but in how they reinforce each other.

---

## Final Note

This repository intentionally avoids unnecessary complexity.

Every design choice favors:
- Adoption over novelty
- Reliability over impressiveness
- Systems thinking over tool stacking

AI should not be impressive.  
It should be safe to rely on.

# Workflow: CRM Intelligence Request Flow

## Objective
Provide AI-assisted insights over CRM data while preserving system stability, auditability, and human control.

## Pseudo Diagram

This diagram represents the logical flow of the CRM Intelligence system.
It is platform-agnostic but maps directly to tools like n8n or Make.

---

[ User / Internal Tool ]
        |
        v
[ Request Trigger ]
(User submits CRM question)
        |
        v
[ Permission & Input Validation ]
- CRM record exists?
- Required fields present?
- User authorized?
        |
   ┌────┴────┐
   |         |
  FAIL      PASS
   |         |
[ Stop ]    v
        [ Context Assembly ]
        - Interaction logs
        - Documents
        - Metadata
        - User question
                |
                v
        [ Model Selection Logic ]
        - Task criticality
        - Cost threshold
        - Latency tolerance
        (Default: small / efficient model)
                |
                v
        [ AI Invocation ]
        - JSON prompt contract
        - Strict output schema
        - No free-form responses
                |
                v
        [ Output Validation ]
        - JSON schema check
        - Hallucination signals?
        - Restricted actions?
                |
        ┌───────┴────────┐
        |                |
      FAIL              PASS
        |                |
[ Fallback / Alert ]    v
                 [ Human Review Gate ]
                 - Confidence level
                 - Risk flags
                 - Missing info
                        |
                        v
                 [ Human Decision ]
                 - Accept
                 - Clarify
                 - Escalate
                 - Ignore
                        |
                        v
                 [ Logging & Audit ]
                 - Prompt version
                 - Model used
                 - Input reference
                 - Output JSON
                 - Human action


---

## Trigger
- User submits a CRM intelligence request
- Triggered via internal dashboard or CRM interface

---

## Step 1: Input Validation
System checks:
- CRM record exists
- Required fields are present
- User has permission to access the data

If validation fails → return error and stop workflow.

---

## Step 2: Context Assembly
System aggregates:
- Interaction logs
- Related documents
- Metadata
- User question

No transformation or enrichment is applied at this stage.

---

## Step 3: AI Invocation
- Selected model based on task criticality
- Default to small / cost-efficient model
- JSON-based prompt contract is applied
  (`/prompts/crm-intelligence-agent.json`)

---

## Step 4: Response Validation
System validates:
- Output matches expected JSON schema
- No restricted actions are suggested
- No hallucinated entities are present

If validation fails → route to fallback.

---

## Step 5: Human Review Gate
AI response is presented with:
- Confidence level
- Risk flags
- Missing information indicators

Human decides to:
- Accept
- Request clarification
- Escalate
- Ignore output

---

## Step 6: Logging & Traceability
System logs:
- Prompt version
- Model used
- Input reference
- Output JSON
- Human action taken

---

## Fallback Scenarios
- Invalid output → notify system owner
- Low confidence → manual analysis
- Model failure → retry with alternate model or stop

---

## Outcome
AI insights are delivered without:
- Changing workflows
- Creating hidden dependencies
- Introducing irreversible automation

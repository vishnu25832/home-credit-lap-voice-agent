# Architecture and Workflow — Home Credit LAP Voice Agent

## 1. Project Overview

The Home Credit Loan Against Property (LAP) Voice Agent is a conversational AI agent configured in Retell AI. The agent, Asha, interacts with customers, gathers preliminary loan eligibility information, evaluates the configured eligibility conditions, and provides the appropriate response.

The project demonstrates voice-agent configuration, prompt-based conversation control, eligibility validation, disqualification handling, and preliminary customer routing.

## 2. System Architecture

The system is organized into the following logical components:

1. **Customer:** Responds to the agent's questions during a voice conversation.
2. **Retell AI Voice Interface:** Handles the voice conversation between the customer and the agent.
3. **Agent Instructions:** Define Asha's role, question sequence, eligibility rules, response constraints, and termination behavior.
4. **Eligibility Evaluation:** Determines whether the customer's answers satisfy the configured preliminary criteria.
5. **Call Actions and Routing:** Uses configured tools or workflows, where available, to terminate calls or route customers appropriately.
6. **Test Evidence and Documentation:** Stores selected recordings, matching transcripts, and test outcomes.

### Architecture Flow

Customer
→ Retell AI Voice Interface
→ Asha — LAP Voice Agent
→ Collect Customer Information
→ Evaluate Eligibility
→ Eligible: Preliminary Handoff Message
→ Ineligible: Disqualification Message and Call Termination

Special cases, such as busy customers and existing LAP transfer requests, follow their dedicated conversation paths.

## 3. Customer Information Collection

The agent gathers the following information during the preliminary qualification process:

| Field | Purpose |
|---|---|
| Property type | Identifies whether the property falls within the supported categories |
| Ownership | Determines whether the property is solely or jointly owned |
| Original property documents | Checks whether the documents are available for verification |
| Requested loan amount | Checks the requested amount against the ₹75 lakh offer cap |
| Occupation | Captures whether the customer is salaried or self-employed |
| Income mode | Determines whether income is received through a bank or in cash |
| Property market value | Records the property's stated market value |
| Loan tenure | Checks whether the requested tenure is between 3 and 15 years, inclusive |

The market value is collected as information. No additional market-value threshold is assumed in this project.

## 4. Eligibility Decision Rules

The configured preliminary rules are:

- Residential, commercial, and industrial properties are eligible property categories; agricultural property is disqualified.
- Sole and joint ownership are both accepted.
- Original property documents must be available for verification.
- The maximum offer amount is ₹75 lakh. If a customer requests more, the agent explains the cap and asks whether the customer accepts it.
- The customer must have a salaried or self-employed occupation and receive income through a bank. Cash-based income is disqualified.
- The customer's stated market value is collected without applying an unspecified minimum threshold.
- Loan tenure must be between 3 and 15 years, inclusive.

A customer who fails a mandatory criterion follows the configured disqualification path.

## 5. Conversation Workflow

### 5.1 Eligible Customer

1. The agent introduces itself and identifies the purpose of the call.
2. It collects the required customer information.
3. It evaluates the answers against the configured criteria.
4. If the customer satisfies all criteria, it provides the approved preliminary handoff message.
5. The configured call-ending or handoff action should execute as required by the implementation.

### 5.2 Ineligible Customer

1. The agent identifies a disqualifying answer.
2. It delivers the prescribed disqualification message.
3. It terminates the call using the configured `end_call` action, where that action is available and verified.
4. It does not continue with additional loan suggestions after immediate disqualification.

### 5.3 Requested Amount Exceeds the Offer Cap

1. The agent identifies that the requested amount exceeds ₹75 lakh.
2. It explains that the offer is capped at ₹75 lakh.
3. If the customer accepts the cap, qualification continues using the accepted amount.
4. If the customer declines the cap, the agent follows the disqualification path.

### 5.4 Busy Customer

1. The agent asks the customer for a suitable callback time.
2. It ends the current conversation.
3. A callback is described as scheduled only if the configured callback workflow confirms successful scheduling.

### 5.5 Existing LAP Transfer or EMI Reduction

1. The agent identifies the customer's request as an existing-loan transfer or EMI-reduction enquiry.
2. It follows the configured specialist-contact response.
3. It ends the current conversation without conducting a new eligibility checklist.
4. Actual specialist routing or contact is claimed only when confirmed by the configured workflow.

## 6. Tools and External Actions

The agent's instructions define the desired conversational behavior. Actual call termination, callback scheduling, or specialist routing depends on the tools and workflows configured in Retell AI.

The `end_call` action must be configured and its execution verified through call logs or tool results before the project claims that it executed successfully.

A spoken statement about a callback or specialist contact is not, by itself, proof that the corresponding action occurred.

## 7. Testing and Evidence

Three representative scenarios are selected for audio demonstration:

- Eligible customer
- Agricultural property
- Customer declines the ₹75 lakh offer cap

The associated audio recordings and transcripts are stored in the `evidence/` directory.

Other eligibility and special-case scenarios are documented in `docs/test-report.md`. Their results are reported according to the available test evidence; audio recordings are not claimed for scenarios without published recordings.

## 8. Limitations

- The agent performs a preliminary conversational eligibility check, not a final loan approval.
- Final eligibility, loan terms, and interest rates are subject to the lender's actual evaluation and applicable processes.
- Callback scheduling and specialist contact depend on the availability and successful execution of configured workflows.
- The architecture described here represents the project's logical workflow. It does not imply that unconfigured external integrations exist.

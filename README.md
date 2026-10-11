# Home Credit Loan Against Property Voice Agent

## Overview

This project implements an AI voice agent for preliminary qualification of customers interested in a Home Credit Loan Against Property (LAP) offer.

The agent is configured using Retell AI and is designed to conduct natural conversations, collect eligibility information, identify disqualifying conditions, and provide the appropriate next-step message.

## Objectives

- Automate preliminary LAP eligibility conversations.
- Collect and retain customer eligibility information.
- Enforce the maximum offer amount of ₹75 lakh.
- Identify eligible and ineligible property types.
- Verify ownership, original property documents, occupation, income mode, market value, and requested tenure.
- Handle customer interruptions and out-of-order answers.
- Route qualifying customers toward a senior loan expert.
- End calls appropriately when a terminal condition is reached.

## Technology

- Retell AI — voice agent configuration and conversational testing.
- System prompting — qualification logic, state management, and conversation flow.
- GitHub — source documentation and test evidence.

## Eligibility Rules

| Criterion | Requirement |
|---|---|
| Property type | Residential, commercial, or industrial |
| Ownership | Sole or joint |
| Original documents | Available for verification |
| Maximum loan amount | ₹75,00,000 |
| Occupation | Salaried or self-employed |
| Income mode | Bank income |
| Property market value | Recorded; no threshold defined in this project |
| Tenure | 3–15 years, inclusive |

Agricultural property, unavailable original documents, cash income, tenure outside the permitted range, and refusal of the ₹75 lakh cap trigger disqualification under the configured prompt.

## Project Documentation

- `docs/system-prompt.md` — final system prompt.
- `docs/test-report.md` — test scenarios and observed outcomes.
- `docs/architecture-and-workflow.md` — agent workflow and decision logic.
- `evidence/recording-links.md` — verified recording and transcript links.

## Testing

The agent was tested using Retell AI's Test LLM and Test Audio interfaces.

Test scenarios included:
- Eligible customer qualification.
- Agricultural-property disqualification.
- Original documents unavailable.
- Cash-income disqualification.
- Customer accepts the ₹75 lakh cap.
- Customer refuses the ₹75 lakh cap.
- Ownership verification.
- Retention of previously supplied answers.

Test outcomes are documented separately. Spoken-response results are not treated as proof of tool execution unless confirmed by the corresponding logs.

## Limitations

This agent performs preliminary qualification only. It does not approve or disburse loans, guarantee eligibility for final approval, or invent interest rates or charges.

Actual callbacks, specialist handoffs, and call termination depend on the available Retell configuration and successful execution of the corresponding actions.

## Evidence

Verified audio recordings, transcripts, and relevant call details are listed in `evidence/recording-links.md` when available.

## Disclaimer

This is a conversational AI project demonstrating a configured preliminary qualification workflow. It is not a loan approval system and does not replace Home Credit's formal lending assessment.
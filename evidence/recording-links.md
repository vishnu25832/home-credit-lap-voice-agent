# Recording Links — Home Credit LAP Voice Agent

## 1. Overview

This document provides the audio evidence and corresponding transcripts for three representative test scenarios conducted for the Home Credit Loan Against Property (LAP) voice agent built using Retell AI.

The selected recordings demonstrate the agent's eligibility-checking behavior, disqualification handling, and response to a customer declining the maximum offer amount.

Only the three selected recordings are included as audio evidence. Other test scenarios and their observed outcomes are documented separately in [`../docs/test-report.md`](../docs/test-report.md).

## 2. Recording Index

| Test ID | Test Scenario | Audio Recording | Transcript | Expected Behavior |
|---|---|---|---|---|
| T01 | Eligible customer | `recordings/eligible-customer.wav` | `transcripts/eligible-customer.txt` | Collect the required details and provide the approved preliminary handoff message |
| T02 | Agricultural property | `recordings/agricultural-property.wav` | `transcripts/agricultural-property.txt` | Deliver the prescribed disqualification message and terminate the call through the configured action |
| T03 | Customer declines ₹75 lakh cap | `recordings/loan-cap-refusal.wav` | `transcripts/loan-cap-refusal.txt` | Explain the offer cap, handle the customer's refusal, and follow the disqualification flow |

**Note:** The filenames above are examples. Update them to match your actual files and extensions.

## 3. T01 — Eligible Customer

**Purpose:** Demonstrate the successful preliminary qualification flow.

**Expected behavior:**
- The agent collects the required customer information.
- The agent checks the answers against the configured eligibility criteria.
- The agent provides the approved preliminary handoff message after all required details have been collected and the criteria are satisfied.

**Evidence files:**
- Audio: `recordings/eligible-customer.wav`
- Transcript: `transcripts/eligible-customer.txt`

**Observed result:** [Enter the verified outcome.]

## 4. T02 — Agricultural Property

**Purpose:** Demonstrate immediate disqualification when the customer's property is agricultural.

**Expected behavior:**
- The agent identifies agricultural property as ineligible for this offer.
- The agent delivers the prescribed disqualification message.
- The agent does not continue with additional loan suggestions after disqualification.
- The configured call-ending action is verified separately through tool results or call logs.

**Evidence files:**
- Audio: `recordings/agricultural-property.wav`
- Transcript: `transcripts/agricultural-property.txt`

**Observed result:** [Enter the verified outcome.]

## 5. T03 — Customer Declines the ₹75 Lakh Cap

**Purpose:** Demonstrate handling of a requested loan amount above the offer limit.

**Expected behavior:**
- The agent explains that the maximum offer amount is ₹75 lakh.
- The agent asks whether the customer accepts the capped amount.
- When the customer declines, the agent delivers the prescribed disqualification message.
- The configured call-ending action is verified separately through tool results or call logs.

**Evidence files:**
- Audio: `recordings/loan-cap-refusal.wav`
- Transcript: `transcripts/loan-cap-refusal.txt`

**Observed result:** [Enter the verified outcome.]

## 6. Additional Test Scenarios

Other test scenarios are documented in [`../docs/test-report.md`](../docs/test-report.md). These include document availability, income mode, tenure, acceptance of the offer cap, busy-customer handling, ownership, and existing LAP transfer or EMI-reduction enquiries.

No additional audio recordings are claimed for these scenarios in this evidence index.

## 7. Audio Quality and Integrity

- Original recordings should be retained unchanged where possible.
- If noise reduction is applied, the enhanced version should be identified separately from the original.
- The corresponding transcript should be checked against the available audio.
- Any unintelligible sections should be disclosed rather than guessed or reconstructed.
- Recordings and transcripts should not expose private customer information, credentials, or other sensitive data.

## 8. Tool Execution Verification

A transcript or spoken statement alone does not prove that a Retell AI tool executed successfully.

| Action | Verification Status | Evidence Reference |
|---|---|---|
| Call termination after disqualification | [Verified / Not verified] | [Call log or tool result] |
| Call termination after final handoff | [Verified / Not verified] | [Call log or tool result] |

Update these fields only after checking the corresponding Retell AI call logs or tool results.

## 9. Repository Notes

The three selected recordings and their matching transcripts are intended to serve as representative demonstrations of the voice agent.

The test report documents the broader test coverage. The recordings demonstrate selected conversational outcomes and do not, by themselves, establish that every configured external action executed successfully.

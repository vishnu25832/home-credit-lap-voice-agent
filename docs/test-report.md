# Test Report — Home Credit LAP Voice Agent

## 1. Overview

- **Platform:** Retell AI
- **Agent:** Asha — Home Credit Loan Against Property
- **Testing method:** Conversational test calls and transcript review
- **Purpose:** Validate eligibility handling, disqualification rules, and customer routing.

## 2. Recorded Demonstrations

| Test ID | Scenario | Evidence | Result |
|---|---|---|---|
| T01 | Eligible customer | Audio recording and transcript | Passed — conversational flow verified |
| T02 | Agricultural property | Audio recording and transcript | Passed — disqualification response verified |
| T03 | Customer declines ₹75 lakh cap | Audio recording and transcript | Passed — refusal handled correctly |

## 3. Additional Test Results

The following scenarios were tested separately. Their results are documented without publishing additional audio recordings.

| Test ID | Scenario | Result |
|---|---|---|
| T04 | Original property documents unavailable | Passed — based on observed test result |
| T05 | Cash-based income | Passed — based on observed test result |
| T06 | Tenure outside the 3–15-year range | Passed — based on observed test result |
| T07 | Customer accepts the ₹75 lakh cap | Passed — based on observed test result |
| T08 | Busy customer requests a callback | [Enter verified result] |
| T09 | Existing LAP transfer or EMI reduction | Passed — based on observed test result |
| T10 | Sole or joint ownership | Passed — based on observed test result |

Only retain a “Passed” status for scenarios that were actually tested and behaved as expected. Change any unverified result to “Not verified” or “Not tested,” as appropriate.

## 4. Tool Execution Verification

Conversational behavior and actual tool execution are evaluated separately.

| Action | Status |
|---|---|
| Call termination after disqualification | [Verified / Not verified] |
| Call termination after final handoff | [Verified / Not verified] |
| Callback scheduling | [Verified / Not applicable / Not verified] |
| Specialist handoff | [Verified / Not applicable / Not verified] |

## 5. Evidence Location

The three selected audio recordings and their corresponding transcripts are stored in `evidence/recordings/` and `evidence/transcripts/`.

Additional test outcomes are recorded in this report. No additional audio recordings are claimed for those scenarios.

## 6. Limitations

- Only three representative recordings are included in the repository.
- Other scenarios are documented using their observed test results.
- A successful spoken response does not independently prove that a configured tool executed.
- No actual callback or specialist contact is claimed unless confirmed by workflow logs.

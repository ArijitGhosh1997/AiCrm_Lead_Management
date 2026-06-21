# CRM Integration – Lead Sync and Follow-Up Validation

## Module
AI CRM System – CRM Integration (External CRM → AI CRM Lead Sync)

---

## Overview
This test suite validates the lead synchronization flow between an external CRM platform and the AI CRM System. It covers both synced and non-synced lead scenarios, including lead creation, import into the AI system, representative assignment, follow-up timing, and lead status management.

---

## Pre-Conditions
- CRM integration is configured and active between the external CRM and the AI CRM System.
- A representative account exists in the AI CRM System.
- Test lead records are available in the external CRM.
- Follow-up scheduling is enabled in the AI CRM System.

---

## Test Scenarios

---

### Scenario A – Synced Lead Flow

#### TC_003_A01 – Lead Created in External CRM → Appears in AI CRM System

| Field | Detail |
|-------|--------|
| **Action** | Create a new lead in the external CRM |
| **Expected Result** | Lead is automatically imported and visible in the AI CRM System |
| **Validation** | Verify lead details (name, email, source) are correctly mapped |
| **Status** | Completed |

#### TC_003_A02 – Representative Meeting Creation from AI CRM System

| Field | Detail |
|-------|--------|
| **Action** | Representative creates a meeting/appointment for the synced lead |
| **Expected Result** | Meeting is created and associated with the correct lead record |
| **Validation** | Confirm meeting appears in the representative's schedule and in lead activity |
| **Status** | Completed |

#### TC_003_A03 – Attendee Email List Verification via Database

| Field | Detail |
|-------|--------|
| **Action** | After meeting creation, verify attendee email list in the backend |
| **Expected Result** | All invited attendees (lead + rep) are correctly stored in the meeting record |
| **Validation** | Query database to confirm attendee list matches the booking inputs |
| **Status** | Completed |

#### TC_003_A04 – Representative Follow-Up Time Validation

| Field | Detail |
|-------|--------|
| **Action** | Verify the follow-up time assigned to the representative after lead import |
| **Expected Result** | Follow-up time is correctly set based on system configuration and lead timezone |
| **Validation** | Check `repFollowupTime` value in the database; cross-check with representative's local time display |
| **Status** | Completed |

#### TC_003_A05 – Local Time Conversion Accuracy

| Field | Detail |
|-------|--------|
| **Action** | Verify that follow-up times are correctly converted to the representative's local timezone |
| **Expected Result** | Follow-up time shown in the UI matches the expected local conversion of the stored UTC/system time |
| **Status** | Completed |

#### TC_003_A06 – Lead Status Change by Representative

| Field | Detail |
|-------|--------|
| **Action** | Representative attempts to update the lead's status from their dashboard |
| **Expected Result** | Status change is accepted and reflected immediately in both the rep view and the admin/system view |
| **Status** | Completed – Status change successful |

---

### Scenario B – Non-Synced Lead Flow

#### TC_003_B01 – Non-Synced Lead Created in External CRM → Behaviour in AI CRM

| Field | Detail |
|-------|--------|
| **Action** | Create a lead in the external CRM that is not set to sync |
| **Expected Result** | Lead does not appear in the AI CRM System's main lead list |
| **Validation** | Confirm no import record exists for this lead |
| **Status** | Completed |

#### TC_003_B02 – Representative Follow-Up Time for Non-Synced Lead

| Field | Detail |
|-------|--------|
| **Action** | Observe follow-up time assignment behaviour for a non-synced lead |
| **Expected Result** | No automated follow-up is triggered for non-synced leads |
| **Validation** | Confirm `repFollowupTime` is null or absent in the database for this lead |
| **Status** | Completed |

#### TC_003_B03 – Representative Attempts Status Change on Non-Synced Lead

| Field | Detail |
|-------|--------|
| **Action** | Representative tries to change status of a lead that is not synced |
| **Expected Result** | System should restrict or handle the status change appropriately |
| **Validation** | Observe system response and check if any unintended state changes occur |
| **Status** | Completed |

---

## Post-Conditions
- All synced lead records are correctly stored with accurate field mapping.
- Follow-up times reflect the correct timezone conversion for each representative.
- Lead status changes are logged in the activity/audit trail.
- Non-synced leads do not trigger any automated follow-up workflows.

---

## Notes
- CRM integration testing should be performed after any changes to the lead import pipeline or representative assignment logic.
- Always verify both the UI display and the backend database value for time-sensitive fields like follow-up timestamps.
- Regression test both Scenario A and Scenario B when the integration configuration is modified.

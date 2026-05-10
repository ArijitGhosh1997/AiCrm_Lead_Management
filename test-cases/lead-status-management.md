# Test Cases: Lead Status Management

---

## TC_001: Status Update via Email (Valid Case)

**Condition:**
Status = Meeting Completed

**Expected Result:**
- Rep can update status via email
- Status changes successfully

---

## TC_002: Status Update Restriction

**Condition:**
Status ≠ Meeting Completed

**Expected Result:**
- System should return error
- Status should not update

---

## TC_003: Single Update Restriction

**Expected Result:**
- Rep can update status only once
- Second attempt should fail

---

## TC_004: Meeting Booking Status Transition

**Condition:**
Status = Initial Engagement / Dormant / Meeting Completed

**Expected Result:**
- Status → Meeting Scheduled

---

## TC_005: Invalid Status Booking

**Condition:**
Other statuses

**Expected Result:**
- Status should NOT change

---

## TC_006: Not Interested Behavior

**Expected Result:**
- Status updated to "Not Interested"
- AI stops communication
- No further updates allowed

---

## TC_007: Rep Handover Behavior

**Expected Result:**
- No automatic status update
- AI actions do not affect status

---

## TC_008: UI Override

**Expected Result:**
- Rep can change status manually
- Workflow continues from new state

---

## TC_009: Deal Closed / Not Closed

**Expected Result:**
- Status updated correctly
- AI may still respond
- No further status changes

---

## TC_010: Opt-Out Handling

**Expected Result:**
- Status → Opt-out
- Follow-ups stop
- AI stops communication

---

## TC_011: Opt-Out Re-engagement

**Expected Result:**
- Status resets to Initial Engagement

---

## TC_012: Meeting Cancellation (Edge Case)

**Expected Result:**
- Current behavior: no status revert
- Future logic:
  - revert to previous state OR
  - update based on rep input

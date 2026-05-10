# BUG: Lead Status Update Issues

---

## BUG_001: Opt-Out Status Not Updating

## Summary
Lead sends opt-out message but status does not update.

---

## Expected Result
- Status should update to "Opt-out"

---

## Actual Result
- Status remains unchanged
- Follow-ups stop correctly

---

## Impact
- Incorrect lead classification

---

## Status
Fixed

---

## BUG_002: Incorrect Status After Opt-Out

## Summary
After opt-out, status changes to incorrect value.

---

## Expected Result
- Status should remain "Opt-out"

---

## Actual Result
- Status changed to unrelated state

---

## Impact
- Workflow inconsistency

---

## BUG_003: Bot Not Stopping After Deal Closed

## Expected Result
- Bot should stop after deal closure

---

## Actual Result
- Bot continues messaging

---

## Severity
High

---

## BUG_004: Status Not Updating After Follow-Up

## Summary
Lead completes meeting but status does not update correctly.

---

## Impact
- Breaks workflow logic

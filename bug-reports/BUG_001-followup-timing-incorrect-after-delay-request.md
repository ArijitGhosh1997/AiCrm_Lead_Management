# BUG_001: Follow-Up Timing Incorrect After Lead Requests a Delay

## Module
AI CRM System – Automated Follow-Up Engine

---

## Summary
When a lead requests a specific delay before the next follow-up (e.g., "contact me in 20 minutes"), the system does not honour the requested time window. Instead, it sends the follow-up earlier than expected and incorrectly increments the follow-up counter, resulting in more follow-ups being triggered than intended.

---

## Steps to Reproduce
1. Create a lead and initiate an automated follow-up conversation via the AI chatbot.
2. Allow the system to send the first and second follow-up messages.
3. After the second follow-up, respond as the lead with a delay request (e.g., "contact me in 20 minutes").
4. Observe when the next follow-up message is sent.
5. Check the database for the follow-up count value associated with the lead.

---

## Expected Result
- The system should wait the exact duration requested by the lead (20 minutes) before sending the next follow-up.
- Only one additional follow-up should be triggered after the requested delay.
- The follow-up counter in the database should increment by 1 correctly.

---

## Actual Result
- The follow-up was sent significantly earlier than the requested delay (approximately 10 minutes instead of 20).
- The system sent two follow-up messages when only one was expected.
- The follow-up counter in the database was recorded as 2 instead of 1, indicating an incorrect increment.

---

## Database Verification
- Queried the lead record after the issue occurred.
- Confirmed the `followUpCount` field was incorrectly incremented, reflecting the duplicate follow-up send.
- The `nextFollowupTime` value did not match the lead-requested delay time.

---

## Impact
- Leads receive multiple unsolicited follow-up messages within a short window, creating a poor user experience.
- Trust in the AI communication system is degraded when it ignores an explicit delay request.
- Follow-up count data becomes unreliable, affecting downstream reporting and workflow logic.

---

## Severity
High

## Priority
High

## Type
AI Behavior Issue / Functional Bug / Backend Bug

---

## Suggested Fix
- Validate and parse the lead's delay request within the AI response handler before setting the next follow-up timestamp.
- Ensure the follow-up scheduling logic locks the timer to the lead-requested delay and does not allow overlapping triggers.
- Add a guard condition to prevent double-increment of the follow-up counter when a time-change request is active.
- Write a unit test covering the scenario: "follow-up time change requested by lead → verify exact one follow-up sent after requested delay."

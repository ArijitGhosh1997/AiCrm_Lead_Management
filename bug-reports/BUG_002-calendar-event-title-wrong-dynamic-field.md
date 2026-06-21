# BUG_002: Calendar Event Title Displaying Incorrect Dynamic Field Value

## Module
AI CRM System – Appointment Booking / Calendar Integration

---

## Summary
When an appointment is booked through the AI chatbot and calendar invitations are sent to both the lead and the representative, the event title incorrectly displays the `{friendly name}` value instead of the actual `{Company Name}` in the parenthetical portion of the title. This issue persists across multiple email platform combinations (Gmail and Outlook).

---

## Steps to Reproduce
1. Set up an appointment booking flow through the AI chatbot with a lead.
2. Configure the calendar event title template to include `{Company Name}` inside parentheses.
3. Book an appointment — the system sends calendar invitations to both the lead and the representative.
4. Open the calendar invitation from both the lead's and the representative's perspective.
5. Inspect the event title in the parenthetical section.

---

## Expected Result
- The event title should display the actual company name of the lead inside the parentheses.
- Example: `Meeting with [Lead Name] and [Rep Name] (Acme Corp)`

---

## Actual Result
- The event title displays the `{friendly name}` field value instead of the `{Company Name}` field value.
- Example: `Meeting with [Lead Name] and [Rep Name] (John)` — where "John" is the friendly name, not the company.
- This issue is consistent across all tested combinations:
  - Outlook (bot) → Gmail (lead) → Gmail (rep)
  - Outlook (bot) → Outlook (lead) → Gmail (rep)
  - Outlook (bot) → Gmail (lead) → Outlook (rep)

---

## Cross-Platform Testing Results
| Bot Email Platform | Lead Email Platform | Rep Email Platform | Issue Present |
|--------------------|---------------------|--------------------|---------------|
| Outlook | Gmail | Gmail | ✅ Yes |
| Outlook | Outlook | Gmail | ✅ Yes |
| Outlook | Gmail | Outlook | ✅ Yes |

**Note:** All other dynamic fields (meeting link, meeting ID, passcode, event body, description) populate correctly across all platforms. Only the `{Company Name}` field inside the event title parentheses is affected.

---

## Impact
- Calendar events display misleading or unprofessional information to both leads and representatives.
- Client-facing communications appear unpolished, reducing confidence in the platform.
- Representatives cannot quickly identify the company from calendar event titles alone.

---

## Severity
Medium

## Priority
High

## Type
AI Behavior Issue / Functional Bug / Integration Bug

---

## Suggested Fix
- Review the dynamic field mapping logic in the calendar event title builder.
- Confirm that the `{Company Name}` variable correctly maps to the `companyName` field from the lead record — not the `friendlyName` field.
- Add a dedicated test case for each dynamic field in the event title template to validate correct population.
- Perform regression testing across Outlook and Gmail combinations after the fix is applied.

# FEATURE : Full Global Timezone Support in User Management Form

## Module
AI CRM System – User Management / Add User Form

---

## Feature Type
Functional Enhancement – Timezone Configuration

---

## Summary
The Add User form in the system currently has limited or incomplete timezone support. This feature request covers the implementation of full global timezone coverage, ensuring that when a new user (representative, admin, or BDC) is created, their timezone can be accurately set from a comprehensive list of worldwide timezones — not just a subset.

---

## Business Context
The AI CRM System serves clients operating across multiple countries and time zones (North America, South Asia, Europe, etc.). Representatives and leads interact across timezone boundaries. If a user's timezone is not correctly set at account creation, all time-sensitive features — including follow-up scheduling, appointment booking, and calendar sync — are affected.

---

## Current Behaviour
- The Add User form provides a timezone selection field.
- The available timezone options are limited — not all global timezones are present.
- Users in certain regions cannot find or set their correct timezone.
- This causes downstream issues in follow-up timing and calendar event scheduling.

---

## Expected Behaviour
- The timezone selector in the Add User form should include all standard global timezones (IANA timezone database format recommended).
- Timezones should be searchable and grouped by region (Americas, Europe, Asia, etc.) for ease of selection.
- The selected timezone should correctly propagate to all time-based features: follow-up scheduling, appointment display, and email notification timing.

---

## Acceptance Criteria
- [ ] All global timezones from the IANA tz database are available in the Add User form dropdown.
- [ ] Timezone field is searchable by city name, offset, or timezone code.
- [ ] On user creation, the selected timezone is stored correctly in the user record.
- [ ] Follow-up times for the user are calculated and displayed based on the stored timezone.
- [ ] Appointment calendar times reflect the user's configured timezone.
- [ ] Changing a user's timezone updates all associated time-based displays accordingly.
- [ ] Tested across at least 3 major timezone regions (e.g., Eastern US, IST, GMT).

---

## Impact if Not Implemented
- Representatives receive follow-up assignments or calendar events at incorrect local times.
- Leads may receive communications outside of their expected timezone window.
- International clients face degraded scheduling experience.

---

## Priority
High

## Effort Estimate
Medium

## Dependencies
- Timezone data source (IANA or equivalent)
- Follow-up scheduling engine (must consume the user timezone field)
- Calendar integration module

---

## Notes
- Consider displaying the current UTC offset alongside the timezone name for clarity (e.g., "IST – UTC+5:30").
- Timezone selection UX should be consistent with the appointment booking form, which already requires timezone input.

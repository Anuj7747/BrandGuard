# Round 3 Submission Notes — CodeNova / BrandGuard

## Project summary
BrandGuard is a brand-governance review workspace that flags potential campaign-copy risks, allows teams to configure brand guidelines, and records reviewer decisions. This build continues the existing Round 2 prototype rather than changing the project direction.

## Features in this build
1. Rule-based checks for superiority claims, guarantees, discounts, urgency, generic calls to action, and accessibility reminders.
2. Brand Guidelines Manager for brand name, tone, approved terms, restricted terms, and additional notes.
3. Browser-local review history with open/delete/export controls.
4. JSON review records and standalone HTML reports.
5. Empty-input validation, repeated-review handling, responsive layout, and API error messaging.
6. Optional Gemini API review requiring the user's own API key.

## Technical implementation
- Frontend: HTML5, CSS3, vanilla JavaScript.
- Persistence: browser localStorage; data is local to the device/browser.
- Reports: JSON and standalone HTML generated client-side.
- Optional AI: Gemini `generateContent` API called from the browser after the user supplies a key.
- Hosting: static hosting such as Vercel; no build command needed.

## Testing status
The included README contains a manual end-to-end checklist. The team must execute and record actual test results before submission. In particular, test Gemini integration using a valid API key; do not report this as passed without running it. Check the final deployed URL and repository after publishing the ZIP contents.

## Known limitations
- No authentication or shared backend/database; guidelines and history remain in the current browser.
- Browser-based API-key use is suitable only as a prototype demonstration. A production deployment should use a server-side API and protected environment secret.
- Keyword rules and AI suggestions are advisory, not verified facts or legal advice.

## Team
Team CodeNova. Team leader: Anuj Kushwaha. Members: Akash Chourasia, Aryan Chaurasiya, Sushant Singh.

## Before submitting
- Deploy and test the final build at the working project URL.
- Push the final source to the existing GitHub repository.
- Run every test in README.md and document actual pass/fail results.
- Update the product PDF with screenshots and only verified features/results.
- Submit one final form for the team before the organizer's deadline.


AI model patch note: Gemini selector updated to default to `gemini-3.8-flash`; alternatives are `gemini-3.6-flash` and `gemini-3.5-flash-lite`. End-to-end Gemini response still requires testing with the team’s own API key and network. Do not claim that live API success is verified until this test passes.

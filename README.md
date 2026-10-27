# BrandGuard — Round 3 Prototype

A responsive HTML/CSS/JavaScript brand-governance prototype for CodeNova. It continues the Round 2 BrandGuard direction and includes local rule checks, configurable brand guidelines, browser-local review history, JSON exports, readable HTML reports, and optional Gemini API review.

## Run locally
1. Extract the ZIP.
2. Open `index.html` in a modern browser.
3. Use **Content review** to check campaign copy.
4. Use **Brand guidelines** to configure the brand name, tone, approved terms, restricted terms, and notes.
5. Save a review to keep it in this browser's local storage; download JSON or HTML reports for portable records.

No build command or package installation is required for the local rule-based features.

## Optional Gemini AI review
1. Open **AI settings**.
2. Obtain your own Gemini API key from Google AI Studio and paste it into the key field.
3. Enable the checkbox and choose a model, then run AI review.
4. The key remains in page memory only and is not written to this project's files. Clear it when finished.

**Important security note:** this is a static prototype. A browser-based API key can be inspected while used and should not be used for a production public deployment. For a production system, proxy requests through a backend/serverless function and store the key in a server-side secret/environment variable. AI output can be inaccurate and requires human verification. Network/API access is required for AI review; local rule checks work without it.

## Features
- Rule-based checks for superiority claims, guarantees, discount wording, urgency, generic calls to action, and image accessibility reminders.
- Configurable restricted terms and brand tone/guidelines.
- Empty-input validation and safe DOM text rendering for findings.
- Review decisions, reviewer name, and notes.
- Browser-local review history (up to 100 entries), open/delete records, and export history.
- JSON review records and readable HTML reports.
- Optional Gemini AI review with API error handling.
- Responsive layout for desktop and mobile.

## Architecture
- Single-page static app: `index.html` contains the interface, CSS, and JavaScript.
- Local analysis: deterministic regular-expression rules and custom restricted terms.
- Persistence: `localStorage` on the current browser/device; not a shared server database.
- Report generation: JSON data export and standalone HTML report generated in the browser.
- Optional AI: browser `fetch` to Google's Gemini `generateContent` endpoint. This is a prototype integration, not a secure production architecture.

## Testing checklist
- [ ] Empty content: clicking Review shows a validation message and does not report zero findings.
- [ ] Risky sample copy: findings appear for superiority, guarantee, discount, urgency, and CTA phrases.
- [ ] Repeated review: findings do not duplicate across clicks.
- [ ] Guidelines: save a custom restricted term and confirm it is detected.
- [ ] History: save a review, refresh, reopen it, delete an entry, and export history.
- [ ] Reports: download JSON and HTML reports and open them locally.
- [ ] AI: with a valid API key and network access, confirm output appears; with no key or invalid key, confirm a clear error appears.
- [ ] Responsive UI: check narrow/mobile browser width.

## Known limitations / roadmap
- No user authentication or shared team database; history and guidelines are browser-local.
- Optional AI key is used in the browser; move AI calls to a server-side API before public production use.
- Rule checks and AI suggestions are not legal advice or proof of factual accuracy.
- Future work: secure backend, team accounts/roles, shared guideline storage, audit logs, and source-backed claim verification.

## Honest implementation note
This version includes an optional Gemini API integration, but AI review only works after a user supplies a valid key and has network/API access. Do not claim that AI results were tested unless you run the test with a valid key.


## Gemini API model update

The optional AI review defaults to `gemini-3.8-flash`. Alternative current model IDs are `gemini-3.6-flash` and `gemini-3.5-flash-lite`. The request intentionally omits legacy temperature settings for compatibility with newer Gemini 3 models. Availability still depends on your API key, project, quota, and network. Never commit or share your API key.

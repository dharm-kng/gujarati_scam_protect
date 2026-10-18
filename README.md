# સુરક્ષા સાથી (Suraksha Saathi) — PS000196

Gujarati AI Assistant for Cyber-Fraud Awareness. This beginner-friendly static website checks suspicious messages locally using a rule-based JavaScript engine. It includes a checker, scam learning library, quiz, risk score, link heuristics, speech playback, copy/share controls and a privacy-first offline design.

## Run locally
1. Extract the ZIP.
2. Open `suraksha-saathi/index.html` in Chrome, Edge, Firefox or another modern browser.
3. Paste a sample message or click one of the demo buttons, then choose **મેસેજ તપાસો**.
4. `learn.html` contains the scam library; `quiz.html` contains the quiz.

No Node.js, package installation, build step, API key or server is required. The Google Font needs internet; system fonts are used as fallback. Browser clipboard and speech features may require permission and browser support.

## Files
- `index.html` — message scanner and results
- `learn.html` — searchable 30-category safety library
- `quiz.html` — 10-question quiz
- `css/style.css` — responsive, accessible visual design
- `js/scamData.js` — data-driven category catalogue
- `js/scamEngine.js` — offline risk rules and URL checks
- `js/app.js` — UI, language labels, result rendering and actions
- `js/quiz.js` — quiz logic
- `js/aiExplain.js` — optional protected-backend extension point
- `tests/test-checklist.md` — manual test checklist

## Add a scam category
Open `js/scamData.js`. Add an object to `window.SCAM_CATEGORIES` with a unique `id`, `nameGu`, `nameEn`, `weight`, `keywords`, `explainGu`, `signsGu`, `doGu`, and `dontGu`. Keep keyword phrases short and include common Gujarati, Hindi, English and transliterated variants. Test both scam messages and legitimate messages that contain similar words. The current interface uses general safe-step templates for result lists; category-specific steps can be wired into `js/app.js` as a future enhancement.

## Optional AI mode
AI mode is **disabled by default**. Never place a private LLM API key in JavaScript delivered to the public browser. To enable an AI explanation safely:
1. Build a small backend/serverless function that stores the API key in environment variables.
2. Make that backend validate input size, rate-limit requests and avoid logging sensitive messages.
3. Set `window.AI_EXPLAIN_CONFIG.enabled = true` and `endpoint` to your protected backend endpoint in `js/aiExplain.js`.
4. Integrate the returned explanation into the UI and test failures. The app must retain the offline rule-based result if AI is unavailable.
The included extension point does not call an LLM until configured and does not contain a working provider API integration.

## Free hosting
### GitHub Pages
1. Create a GitHub repository and upload the contents of this folder (so `index.html` is at the repository root).
2. Open **Settings → Pages**.
3. Select the main branch and root folder, then save.
4. Wait for the deployment link shown by GitHub Pages.
### Netlify
1. Sign in to Netlify and choose **Add new site → Deploy manually**.
2. Drag the extracted project folder into the deployment area, or connect the Git repository.
3. Use the provided Netlify URL; connect a custom domain from site settings if desired.

## Safety and limitations
- This is a cyber-awareness aid, not a security scanner, bank verification tool or law-enforcement service.
- The score is heuristic. Scammers change wording, and legitimate messages can contain suspicious terms. Never rely only on the score.
- URL checks are based on visible text and simple patterns; they do not visit links, verify ownership, or guarantee a site is malicious/safe.
- The app does not send messages to a server. Do not add a backend without a clear privacy notice.
- If money is lost, call India's cyber-fraud helpline **1930** promptly and report at https://cybercrime.gov.in/. Also notify your bank through an official channel.

## 1-minute demo script
“Hello judges, this is Suraksha Saathi, our Gujarati cyber-fraud awareness assistant for problem statement PS000196. Many people receive scam messages but struggle to understand the warning signs. Our website lets users paste a suspicious SMS or WhatsApp message and get a simple risk score, possible scam categories, suspicious-link notes and safe next steps. The core detection runs offline in the browser, so the message is not sent to a server. Users can learn about common scams, take a quiz, listen to the result and share a warning with family. This is an awareness tool, not a guarantee, and we direct people who lose money to call 1930 and report at cybercrime.gov.in. Our next steps are Gujarati voice input, a verified scam-number database, a browser extension, an SMS safety app and a WhatsApp bot.”

## Future improvements
1. Gujarati speech-to-text input.
2. WhatsApp bot with clear privacy protections.
3. Browser extension that warns before opening suspicious links.
4. SMS auto-scan companion app with explicit permissions.
5. Community-reported scam numbers with moderation and official verification.

## Screenshots
Add screenshots of the checker, result card, learning library and quiz here after running the project.

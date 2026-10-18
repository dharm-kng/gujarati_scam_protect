# સુરક્ષા સાથી (CyberSaathi Gujarati) — PS000196

A beginner-friendly Gujarati cyber-fraud awareness website. People can paste suspicious SMS, WhatsApp, job, KYC, or payment messages and receive a simple explanation, warning signs, a risk estimate, and safer next steps.

## What works now

- Responsive Gujarati-first website with sample messages and a live character counter.
- Rule-based analysis runs in the browser without a server or API key.
- Risk score, warning indicators, safe next steps, copy-report action, and privacy/safety reminder.
- Optional AI analysis through a protected serverless endpoint. The API key stays on the server and is never sent to browser JavaScript.
- Automatic local-analysis fallback when AI is not configured or the API is unavailable.

## Run the offline demo

1. Download the repository ZIP or clone the repository.
2. Open `index.html` in a modern browser.
3. Paste a message or select one of the example buttons and press **મેસેજ તપાસો**.

The offline checker does not require Node.js, an API key, or a backend. When opened directly as a file, AI mode is not called.

## Enable AI analysis locally

Requirements: Node.js 20 or newer and a private OpenAI API key.

1. Copy `.env.example` to `.env` and put your key in `.env`. Never commit the real `.env` file.
2. Install Vercel CLI if needed, then run `npx vercel dev` from the repository root.
3. Add `OPENAI_API_KEY` and optionally `OPENAI_MODEL` to the local environment used by Vercel.
4. Open the local URL printed by Vercel and test a sample message.

The server endpoint is `POST /api/analyze`. It accepts JSON such as `{"message":"..."}` and returns `{"report":{"score":0,"level":"low","summary":"...","signals":[],"steps":[],"source":"ai"}}`.

## Deploy to Vercel

1. Push this repository/branch to GitHub.
2. Sign in to Vercel and import `dharm-kng/gujarati_scam_protect`.
3. In **Project Settings → Environment Variables**, add:
   - `OPENAI_API_KEY` — your secret API key
   - `OPENAI_MODEL` — optional; defaults to `gpt-4o-mini`
4. Deploy the branch `prototype/ai-backend` to preview it, or merge it into `main` when you're ready.
5. Open the deployment URL and test both a scam-like sample and an ordinary message.

The static website can also be hosted on GitHub Pages, but the AI endpoint requires a serverless host such as Vercel. GitHub Pages alone cannot securely store a private API key or run this API route. A custom domain is optional and can be connected in the hosting provider's domain settings.

## Privacy and safety

- The offline checker processes text in the browser.
- When AI mode is enabled, the submitted message is sent to the configured AI provider through the serverless endpoint to generate a report. Do not paste OTPs, passwords, UPI PINs, full card numbers, or other sensitive details.
- The endpoint does not intentionally log the message body. Hosting providers and AI providers may process technical request data under their own policies.
- A small in-memory rate limit is included as a best-effort guard; configure stronger rate limiting at the hosting/WAF layer before high-traffic public launch.
- The score is an estimate, not proof that a message is safe or fraudulent. URL checks do not verify the real ownership or safety of a website.
- Never share an OTP, password, or UPI PIN or pay a fee to receive a supposed refund/prize.
- If money has been lost to cyber fraud in India, call **1930** promptly and report at https://cybercrime.gov.in/. Contact the bank using an official channel too.

## Project structure

- `index.html` — complete responsive frontend and offline rules engine
- `api/analyze.js` — protected AI serverless endpoint
- `package.json` — Node project metadata and local development command
- `vercel.json` — serverless endpoint configuration
- `.env.example` — names of server-side environment variables (no secrets)

## Demo presentation

“Hello judges, this is CyberSaathi Gujarati for problem statement PS000196. People often receive suspicious messages but may not understand the warning signs. Our website provides a Gujarati risk estimate, explains suspicious patterns, and suggests safer next steps. The basic checker runs locally in the browser. When a private server-side key is configured, the optional AI endpoint can provide a more natural explanation. This is an awareness aid, not a guarantee. Anyone who loses money should contact 1930 and report at cybercrime.gov.in.”

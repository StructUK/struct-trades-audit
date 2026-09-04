# Trades Admin & Automation Audit

A single-page, interactive lead-generation quiz for [Struct Solutions](https://www.struct.solutions). Visitors answer 5 quick questions about how they handle enquiries, quoting, follow-up, and invoicing, then get an instant, personalised "admin leakage" report — estimated lost hours per month, estimated revenue leak in £, and an automation-potential score — plus three tailored automation recommendations and a call-to-action to book a strategy call.

Live concept: **"How much is admin costing your trades business?"**

## How it works

- A 5-step quiz (`.question-step` panels) with a progress bar; each answer carries a `hours` and `risk` weighting.
- A lead-capture form (name, email, optional business name) gates the results.
- On submit, the weighted answers are turned into three headline numbers — monthly hours lost, estimated £ leak, and an automation-potential percentage — and a results dashboard is revealed with a severity badge (Critical / Moderate / Healthy) and three recommended automations.
- The lead's answers and results are sent via [EmailJS](https://www.emailjs.com/) directly from the browser to Struct Solutions, with no backend required.

## Stack

Plain HTML/CSS/JS, no build step. Fonts via Google Fonts, email delivery via the EmailJS browser SDK (loaded from a CDN). The EmailJS **public key** embedded in the script is a client-side identifier by design (not a secret) — see EmailJS's docs on [public vs private keys](https://www.emailjs.com/docs/sdk/installation/).

## Running it

There's nothing to build. Open `index.html` directly, or serve the folder with any static file host (GitHub Pages, Netlify, S3, etc.) — `imgs/` holds the logo asset referenced by the page.

## Customising

- Quiz copy, scoring weights, and recommendations live inline in `index.html` (`selectOption(step, hours, risk)` calls and the `<div class="rec-item">` blocks).
- Swap the EmailJS `service_id` / `template_id` / public key in the `emailjs.send(...)` call to point at your own EmailJS account.
- The CTA links to `struct.solutions/contact` — update for a different destination.

## Related

Part of the Struct Solutions marketing/lead-gen suite alongside [struct-automation-blueprint](https://github.com/StructUK/struct-automation-blueprint), [struct-roi-calculator](https://github.com/StructUK/struct-roi-calculator), and [struct-web](https://github.com/StructUK/struct-web).

# Fan Diagnostic Assistant

A browser-based industrial fan troubleshooting assistant containing 5,000 seed cases. Results separate the broad diagnostic pattern from ranked, specific cause hypotheses, with practical field checks for every cause.

## Run locally

Open `index.html` in a modern browser. No server, API, or internet connection is required.

## Current dataset

- 3,000 centrifugal-fan cases
- 1,300 axial-fan cases
- 700 common cases
- 25 specific diagnostic cause categories

## Diagnostic workflow

- **Diagnostic Pattern** describes the broad direction of the evidence and is not presented as a root cause.
- **Likely Specific Causes** ranks concrete hypotheses with stronger penalties for contradictory evidence.
- **Recommended Checks** expand beneath each cause and help technicians confirm or rule it out. Checks are guidance only and do not trigger re-ranking in this version.

## Local learning

Confirmed causes and adaptive weights are stored in the browser's `localStorage`. Use **Export learned cases JSON** in the application to back up learned feedback before clearing browser data or moving to another computer.

## Repository structure

- `index.html` — complete application, styling, diagnostic logic, and seed dataset
- `README.md` — project information

## Publishing

The application is compatible with GitHub Pages because it is a static, client-side site.

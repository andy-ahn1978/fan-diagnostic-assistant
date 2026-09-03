# Fan Diagnostic Assistant

A browser-based industrial fan troubleshooting assistant containing 5,000 seed cases.

## Run locally

Open `index.html` in a modern browser. No server, API, or internet connection is required.

## Current dataset

- 3,000 centrifugal-fan cases
- 1,300 axial-fan cases
- 700 common cases
- 24 diagnostic cause categories

## Local learning

Confirmed causes and adaptive weights are stored in the browser's `localStorage`. Use **Export learned cases JSON** in the application to back up learned feedback before clearing browser data or moving to another computer.

## Repository structure

- `index.html` — complete application, styling, diagnostic logic, and seed dataset
- `README.md` — project information

## Publishing

The application is compatible with GitHub Pages because it is a static, client-side site.

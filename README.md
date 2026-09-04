# Fan Diagnostic Assistant

A browser-based industrial fan troubleshooting assistant containing 5,000 seed cases. Results separate the broad diagnostic pattern from ranked, specific cause hypotheses, with practical field checks for every cause.

## Run locally

Open `index.html` in a modern browser. No server, API, or internet connection is required.

## Current dataset

- 3,000 centrifugal-fan cases
- 1,300 axial-fan cases
- 700 common cases
- 24 non-overlapping specific diagnostic cause categories

The 5,000 records are synthetic examples rather than field failure records. Their original contents are retained as a fixed baseline; cases that violate hard Rule Matrix compatibility constraints are quarantined from ranking.

## Engineering Rule Matrix

All 24 specific causes now have an embedded, machine-readable rule entry exposed as `window.FAN_DIAGNOSTIC_RULE_MATRIX`. Each entry records its diagnostic family, supporting measurements, contradictions, fan-design/service/subtype constraints, evidence level, and source metadata.

Evidence levels are intentionally conservative:

- **Supporting** — the relationship is supported by the stated AMCA scope publication or the U.S. DOE fan-systems sourcebook.
- **Engineering** — a reviewable fan/rotating-equipment engineering rule that has not yet been traced to a licensed publication edition and page.

No entry is labelled as a direct AMCA transcription or AMCA-validated rule. Licensed AMCA editions must be reviewed and page/section references added before promoting relationships to that status.

The same matrix controls seed admission, service/design compatibility, structured evidence weighting, and contradiction penalties. Runtime audit totals are exposed as `window.FAN_SEED_AUDIT`.

## Diagnostic workflow

- **Diagnostic Pattern** describes the broad direction of the evidence and is not presented as a root cause.
- Up to three patterns are shown in confidence order with blue priority emphasis.
- **Likely Specific Causes** shows the top five concrete hypotheses with stronger penalties for contradictory evidence.
- Each cause explains the supporting evidence and any contradictory evidence actually used by the scoring rules.
- **Recommended Checks** expand beneath each cause and help technicians confirm or rule it out. Checks are guidance only and do not trigger re-ranking in this version.

## Observation intelligence

The free-text **Observations / keywords** field contributes structured diagnostic evidence in addition to text similarity. The local parser recognizes bearing temperature and location, gradual development, shutdown or maintenance timing, impeller cleaning, production increases, full-speed operation, inlet geometry, and duct-change statements. Recognized signals affect scoring and appear in **Why it matches** or **Against**. Negated statements such as `No recent duct modification` are not treated as positive duct-change evidence.

## Ranking safeguards

The final ranking combines seed-case similarity with direct diagnostic evidence, equipment/service compatibility, adaptive learning, and contradiction penalties. Physical and service constraints can override misleading synthetic-seed matches—for example, a PA fan strongly suppresses a plugged-baghouse hypothesis, while baghouse service supports it.

Known synthetic-seed contamination such as non-baghouse services paired with `plugged baghouse` is excluded from cause aggregation while preserving the full 5,000-case dataset for auditability. Displayed percentages are diagnostic confidence scores, not statistical failure probabilities.

Overlapping outlet and downstream obstruction categories are combined as **Downstream / fan discharge restriction**.

## Regression checks

Ten built-in checks run when the page loads and are available from `runFanRegressionTests()` in the browser console:

- low flow + high pressure + normal RPM → restriction family;
- low flow + low pressure + low RPM → speed/drive;
- normal flow and pressure + high vibration → imbalance/bearing;
- adjustable-pitch axial + low flow + normal RPM → blade pitch/control;
- dirty ID service + gradually increasing vibration → buildup/imbalance;
- otherwise healthy fan + elbow immediately at inlet → system effect.
- rising bearing temperature + DE-bearing vibration → bearing/alignment;
- issue immediately after shutdown maintenance + impeller cleaning → installation/imbalance;
- increased production + fan already at full speed → insufficient capacity.
- axial adjustable-pitch PA fan with low flow, high pressure, low RPM, high current/vibration, and an open damper → speed/drive, restriction, or pitch/control; plugged filter is forbidden from the top three.

## Technical basis and limitations

Diagnostic rules were developed with reference to established fan-system troubleshooting principles, including AMCA Publications 201 and 202 and the U.S. DOE fan-systems sourcebook. Synthetic cases are generated examples and are not actual field case records. The application is not AMCA-certified and does not replace qualified engineering assessment.

## Local learning

Confirmed causes and adaptive weights are stored in the browser's `localStorage`. Use **Export learned cases JSON** in the application to back up learned feedback before clearing browser data or moving to another computer.

## Repository structure

- `index.html` — complete application, styling, diagnostic logic, and seed dataset
- `README.md` — project information

## Publishing

The application is compatible with GitHub Pages because it is a static, client-side site.

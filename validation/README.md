# Fan Diagnostic Validation Matrix v1

This directory separates reference validation from software validation. It is deliberately independent of the application's synthetic seed count.

## Evidence grades

- **A — Directly supported:** the cited public authoritative text directly states the relevant relationship.
- **B — Engineering derived:** the relationship follows from a cited physical principle, fan law, system curve, or closely related authoritative guidance.
- **C — Heuristic:** reasonable troubleshooting practice, but the exact relationship has not been directly located in an authoritative source.
- **D — Unverified:** do not use as authoritative evidence; a licensed/current publication section and page or another authoritative source is still required.

Grades apply to a particular rule, not to an entire cause category. A cause may ultimately require several narrower rules with different grades.

## Status policy

- Synthetic generation should prioritize A/B rules.
- C rules may contribute only at reduced weight and must remain visible as heuristic evidence.
- D rules must not independently create or promote a diagnosis.
- Rejected combinations must be blocked during generation and ranking. `PA + plugged_filter` without an explicitly connected filter is the primary regression guard.
- Pressure direction must not be asserted without considering pressure-tap location and whether the restriction is upstream or downstream of that tap.

## Files

- `fan-diagnostic-validation-matrix-v1.csv` contains one baseline rule for each of the 24 current cause IDs.
- `software-validation-tests-v1.csv` contains 30 independent behavior tests. `Ready` means the test specification is ready to automate; it does not mean the current app has passed it.

## Source register

1. AMCA International, *Publication 202-17 | Troubleshooting*. The public page confirms coverage of new/existing installations and aerodynamic performance, noise, vibration, and mechanical issues. It does not expose detailed cause tables; scope alone cannot justify grade A.
   https://www.amca.org/publish/publications-and-standards/amca-publications/amca-publication-202-17-troubleshooting.html
2. AMCA International, *Mitigating System Effect to Optimize Fan Performance and Efficiency*. Public technical article describing inlet/outlet obstructions, nonuniform flow, swirl, duct geometry, dampers, noise, vibration, and performance loss.
   https://www.amca.org/educate/articles-and-technical-papers/amca-inmotion-articles/mitigating-system-effect-to-optimize-fan-performance-efficiency.html
3. U.S. Department of Energy and AMCA International, *Improving Fan System Performance: A Sourcebook for Industry*. Public sourcebook covering fan laws, maintenance, common problems, oversized fans, system leaks, drives, and multiple-fan arrangements.
   https://www.energy.gov/sites/default/files/2014/05/f16/fan_sourcebook.pdf

## Required review before v2

Obtain licensed/current editions of AMCA 201, 202, and 204. Add edition, section, table/figure, and page for every promoted rule. Preserve excerpts only within copyright limits. Record reviewer, review date, and disposition. Do not describe the application as AMCA-certified or AMCA-validated.


# Skill — OAS Diff Analyzer

Objective:
Compare OpenAPI contracts between systems, versions, or environments and produce a structured divergence report.

---

# WHEN TO ACTIVATE

* contract migrations (e.g. v2 → v3, REST → OpenAPI 3.1)
* drift analysis between declared spec and observed traffic
* compatibility validation before publishing a new contract
* cross-system integration audits

---

# DETECTION SCOPE

The skill must detect at minimum:

| Category | Examples |
|---|---|
| Endpoints | added, removed, renamed paths or methods |
| Request shape | added/removed fields, type changes, required-flag changes |
| Response shape | schema divergence, status code coverage, missing examples |
| Status codes | added, removed, semantically changed |
| Semantics | description drift, enum value changes, format changes |
| Security | scheme changes, scope changes, auth requirement changes |

---

# OPERATIONAL FLOW

1. **Load.** Parse both OpenAPI documents (source and target).
2. **Normalize.** Resolve `$ref`s, expand inheritance, canonicalize ordering.
3. **Diff.** Walk the normalized trees and emit findings per category.
4. **Classify.** Tag each finding as `breaking`, `non-breaking`, or `cosmetic`.
5. **Report.** Produce a structured markdown report with summary table and per-finding detail.
6. **Decision.** If breaking changes exist, invoke `adr-writer` to capture the decision (accept, mitigate, abort).

---

# REPORT FORMAT

```markdown
# OAS Diff — <source> vs <target>

## Summary

| Category | Breaking | Non-breaking | Cosmetic |
|---|---|---|---|
| Endpoints | N | N | N |
| Request shape | N | N | N |
| Response shape | N | N | N |
| Status codes | N | N | N |
| Semantics | N | N | N |
| Security | N | N | N |

## Findings

### <finding-id> — <short title>

- **Category:** ...
- **Severity:** breaking | non-breaking | cosmetic
- **Source:** <path/method/field>
- **Target:** <path/method/field>
- **Detail:** ...
- **Recommendation:** ...
```

---

# RULES

* Never silently drop differences: every divergence must appear in the report
* Severity classification must follow OpenAPI compatibility rules, not subjective judgement
* If both inputs are not valid OpenAPI, stop and request fixes
* Cosmetic-only diffs still produce a report (with summary only) for traceability

---

# OUTPUT

`docs/analysis/oas-diff.md` (or a versioned variant: `docs/analysis/oas-diff-<source>-vs-<target>.md`)

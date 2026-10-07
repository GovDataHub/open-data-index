# GovDataHub — Open Dataset Catalogs

Curated, living catalogs of open government datasets, refreshed daily by an
automated pipeline polling **data.gov (US)** and **data.gov.uk (UK)**.

## Files

| File | Contents |
|---|---|
| `climate-energy.csv` / `.json` | 182 datasets: climate, energy, emissions, weather |
| `economy-small-business.csv` / `.json` | 464 datasets: economy, business, employment, trade |
| `general.csv` / `.json` | 267 datasets that didn't match a vertical |
| `LICENSES.md` | License & attribution register — read before republishing |

## Columns

`title, description, landing_url, portal_id, license, license_source, publisher, tags, vertical_suggested, last_seen_at`

- `license_source` is `explicit` (portal stated it) or `inferred-federal`
  (US federal authorship inferred under 17 U.S.C. 105 — see LICENSES.md).
- `vertical_suggested` is a heuristic label, not a manual curation decision.

## Freshness

Regenerated from the pipeline database. This export was generated
2026-10-07. The pipeline re-polls sources daily and
re-audits resource links on a rotating sample.

## License policy

Only datasets with allowlisted licenses are included here:
**US public domain, public domain, CC0, CC-BY, OGL 3.0.**
Datasets with unresolved or non-open licenses are excluded by design.
See `LICENSES.md` for attribution requirements.

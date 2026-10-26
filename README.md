# GovDataHub — Open Government Dataset Catalogs

Curated, living catalogs of **open government datasets** across climate & energy and economy & small business, harvested from **data.gov (US)**, **data.gov.uk**, Socrata portals (US & EU), Zenodo, Hugging Face, the U.S. Energy Information Administration (EIA), Federal Reserve Economic Data (FRED), and national open-data portals in Canada, Australia, Argentina, and Mexico.

Every entry is license-verified before publication — no fragmented portals, no license guesswork.

[![Subscribe to the GovDataHub digest](https://img.shields.io/badge/Subscribe-GovDataHub_Digest-orange)](https://govdatahub.substack.com)

[![DOI](https://zenodo.org/badge/1409425269.svg)](https://doi.org/10.5281/zenodo.23308617)

## 📬 Get dataset alerts

New datasets land regularly. Get the notable ones in your inbox instead of checking back here:

- **[Free weekly digest](https://govdatahub.substack.com)** — the week's most notable new datasets, every Monday

## What's here

**4,894 license-cleared datasets**, one row per dataset, in both CSV and JSON.

| File | Datasets | Covers |
|---|---|---|
| `climate-energy.csv` / `.json` | 1,831 | Climate, energy, emissions, weather |
| `economy-small-business.csv` / `.json` | 1,299 | Economy, business, employment, trade |
| `general.csv` / `.json` | 1,764 | Harvested datasets outside the two verticals |
| `LICENSES.md` | — | License & attribution register — read before republishing |
| `export-manifest.json` | — | Generation metadata and counts |

## Hugging Face mirrors

The catalogs are also mirrored as Hugging Face datasets, with tabular preview and Hub search:

- [GovDataHub/climate-energy-open-datasets](https://huggingface.co/datasets/GovDataHub/climate-energy-open-datasets) — 1,831 datasets
- [GovDataHub/economy-small-business-open-datasets](https://huggingface.co/datasets/GovDataHub/economy-small-business-open-datasets) — 1,299 datasets
- [GovDataHub/general-open-datasets](https://huggingface.co/datasets/GovDataHub/general-open-datasets) — 1,764 datasets

## Quick start

```python
import pandas as pd

climate = pd.read_csv("climate-energy.csv")
climate[["title", "publisher", "license", "landing_url"]].head()
```

```bash
# All CC-BY datasets in the economy vertical
csvkit climate-energy.csv 2>/dev/null || \
python3 -c "
import csv
for r in csv.DictReader(open('economy-small-business.csv')):
    if r['license'] == 'cc-by':
        print(r['title'], '|', r['landing_url'])
"
```

## License policy

Only datasets with allowlisted licenses are published: **US public domain, public domain, CC0, CC-BY, Open Government Licence v3.0, and the Open Government Licence – Canada family (federal and provincial).**

Datasets whose license could not be verified are **excluded, never guessed** — 2,239 harvested datasets are currently quarantined until their licensing checks out.

Some US rows carry `license_source: inferred-federal`: data.gov's API omits license fields, so these were classified by unambiguous federal authorship under **17 U.S.C. 105** (works of US federal employees). Contractor-produced data is excluded from this inference by design. See `LICENSES.md` for the full method and attribution requirements.

**Attribution — OGL v3.0 datasets (most UK rows):**

> Contains public sector information licensed under the Open Government Licence v3.0.

Include the statement above (or a link to https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) wherever you republish these catalogs.

**Attribution — OGL – Canada datasets:**

> Contains information licensed under the Open Government Licence – Canada.

For federal Canadian datasets include the statement above (or a link to https://open.canada.ca/en/open-government-licence-canada) wherever you republish these catalogs; provincial datasets carry the equivalent provincial licence — attribute the province named in each row's `publisher` column.

## For teams that ship on this data — Team Watch

The catalog above is free and stays free. **Team Watch** is the monitoring service built on the same pipeline, for teams whose products depend on specific datasets:

- **Daily monitoring of your watchlist** — new, changed, removed, or unreachable datasets flagged within 24 hours of detection, with provenance and timestamps.
- **License-change alerts** — a distinct alert class, because the license you cleared at integration time is not guaranteed to be the license in force today.
- **Monthly license-clearance report** — every dataset on your watchlist with its license, license basis, source record, and last check date.
- **CSV/JSON change feed** drawn from a timestamped change archive running since October 2026.

**Pilot pricing: $99/month** (launch $199/month; annual $1,990). Alert precision is measured and reported to pilot customers monthly; our operating standard is ≥90% of alerts rated relevant. Quality rules — allow-listed licenses only, zero license false positives, every claim traceable to a source record — are published in full at [govdatahub.com](https://govdatahub.com), along with a public corrections log that includes our own errors.

### Start free: Dataset Risk Check

Send up to 20 datasets your product depends on and receive a written report within 5 days: license status and basis, freshness, and link health for each. Free, no obligation.

**[Request a Dataset Risk Check](mailto:support@govdatahub.com?subject=Dataset%20Risk%20Check%20request)** — support@govdatahub.com

### License Audit — $750–$2,500

A fixed-scope audit of the dataset set you intend to ship commercially: provenance, license basis, and risk flags per dataset, in a written report. Quoted before work starts. A data-provenance audit, not legal advice.

### Additional services

- **Custom dataset sourcing — $500–$2,500 per project.** Tell us the dataset you need; we find it, verify the license, and deliver it normalized, with the license basis traced to the source record. Fixed quote before work starts.
- **Point-in-time archive access — quoted per request.** Dataset versions as published in prior periods, drawn from our timestamped change archive (running since October 2026).
- **Due-diligence audits — $2,000–$5,000 fixed scope.** For investors and acquirers: an audit of a target's open-data dependencies — provenance, license basis, and risk flags per dataset, in a written report. A data-provenance audit, not legal advice.

Details and pilot terms: [govdatahub.com](https://govdatahub.com)

## Freshness

This export was generated **2026-10-26**. The pipeline re-polls its sources daily and audits resource links on a rotating sample; the catalogs on GitHub update with each automatic weekly release. Each row carries `last_seen_at` so you can check how fresh any entry is.

## Columns

`title, description, landing_url, portal_id, license, license_source, publisher, tags, vertical_suggested, last_seen_at`

- `license_source` — `explicit` (the portal stated the license) or `inferred-federal` (classified by federal authorship under 17 U.S.C. 105 — see License policy).
- `vertical_suggested` — a heuristic classifier label, not a human curation decision. Treat it as a starting point, not gospel.

## Cite this repository

```
GovDataHub (2026). GovDataHub — Open Government Dataset Catalogs.
Harvested from data.gov, data.gov.uk, Socrata, Zenodo, Hugging Face, EIA, FRED, and national CKAN portals.
https://github.com/GovDataHub/open-data-index
```

Machine-readable citation metadata lives in `CITATION.cff`. DOI (all versions): https://doi.org/10.5281/zenodo.23308617

## FAQ

**Is this affiliated with data.gov or data.gov.uk?**
No. GovDataHub is an independent curation project. Always verify current terms and availability at each dataset's `landing_url`.

**Can I use these catalogs commercially?**
The catalogs are a metadata index. Underlying datasets carry their own licenses (see `LICENSES.md`) — US public domain rows have no restriction; OGL and CC-BY rows require attribution as described above.

**How is licensing verified?**
Explicit license fields from the portals where present; for US federal records where the API omits the license, classification by unambiguous federal authorship under 17 U.S.C. 105, with contractor-produced data excluded. Anything unverifiable is quarantined, never published.

**How do I get notified of new datasets?**
[Subscribe to the free weekly digest](https://govdatahub.substack.com) — the most notable additions, every Monday.

## Contributing

Suggestions, bug reports, and dataset requests are welcome.

- To report broken URLs or incorrect classification, [open an issue](../../issues).
- To suggest new portals or tags, submit a pull request.

## Notes & caveats

- These catalogs are a **metadata index**, not a data mirror.
- **Data-quality correction (2026-10-12):** 205 datasets previously catalogued under the UK Open Government Licence v3.0 were found, on re-verification against the source APIs, to carry Canadian provincial open-government licences (Alberta, British Columbia, Nova Scotia, and others) or the federal Open Government Licence – Canada. They were removed from these catalogs pending licence allow-list review. UK OGL 3.0 entries are now sourced only from UK portals. **Resolved later on 2026-10-12:** the Open Government Licence – Canada family (federal and provincial) was allow-list approved, and those datasets are published again under their correct Canadian licences — 529 datasets in this release.
- Vertical labels are heuristic; license labels are the one field we never approximate without provenance.

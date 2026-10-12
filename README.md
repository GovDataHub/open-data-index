# GovDataHub — Open Government Dataset Catalogs

Curated, living catalogs of **open government datasets** across climate & energy and economy & small business, harvested from **data.gov (US)**, **data.gov.uk**, Socrata portals (US & EU), Zenodo, Hugging Face, and national open-data portals in Canada, Australia, Argentina, and Mexico.

Every entry is license-verified before publication — no fragmented portals, no license guesswork.

[![Subscribe to the GovDataHub digest](https://img.shields.io/badge/Subscribe-GovDataHub_Digest-orange)](https://govdatahub.substack.com)

## 📬 Get dataset alerts

New datasets land regularly. Get the notable ones in your inbox instead of checking back here:

- **[Free weekly digest](https://govdatahub.substack.com)** — the week's most notable new datasets, every Monday

## What's here

**2,913 license-cleared datasets**, one row per dataset, in both CSV and JSON.

| File | Datasets | Covers |
|---|---|---|
| `climate-energy.csv` / `.json` | 704 | Climate, energy, emissions, weather |
| `economy-small-business.csv` / `.json` | 807 | Economy, business, employment, trade |
| `general.csv` / `.json` | 1,402 | Harvested datasets outside the two verticals |
| `LICENSES.md` | — | License & attribution register — read before republishing |
| `export-manifest.json` | — | Generation metadata and counts |

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

Only datasets with allowlisted licenses are published: **US public domain, public domain, CC0, CC-BY, Open Government Licence v3.0.**

Datasets whose license could not be verified are **excluded, never guessed** — 2,663 harvested datasets are currently quarantined until their licensing checks out.

Some US rows carry `license_source: inferred-federal`: data.gov's API omits license fields, so these were classified by unambiguous federal authorship under **17 U.S.C. 105** (works of US federal employees). Contractor-produced data is excluded from this inference by design. See `LICENSES.md` for the full method and attribution requirements.

**Attribution — OGL v3.0 datasets (most UK rows):**

> Contains public sector information licensed under the Open Government Licence v3.0.

Include the statement above (or a link to https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) wherever you republish these catalogs.

## Freshness

This export was generated **2026-10-12**. The pipeline re-polls its sources daily and audits resource links on a rotating sample; the catalogs on GitHub update with each published release (every release is human-reviewed before going out). Each row carries `last_seen_at` so you can check how fresh any entry is.

## Columns

`title, description, landing_url, portal_id, license, license_source, publisher, tags, vertical_suggested, last_seen_at`

- `license_source` — `explicit` (the portal stated the license) or `inferred-federal` (classified by federal authorship under 17 U.S.C. 105 — see License policy).
- `vertical_suggested` — a heuristic classifier label, not a human curation decision. Treat it as a starting point, not gospel.

## Cite this repository

```
GovDataHub (2026). GovDataHub — Open Government Dataset Catalogs.
Harvested from data.gov, data.gov.uk, Socrata, Zenodo, Hugging Face, and national CKAN portals.
https://github.com/GovDataHub/open-data-index
```

Machine-readable citation metadata lives in `CITATION.cff`. A Zenodo DOI will be added here once the archive integration is enabled.

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
- **Data-quality correction (2026-10-12):** 205 datasets previously catalogued under the UK Open Government Licence v3.0 were found, on re-verification against the source APIs, to carry Canadian provincial open-government licences (Alberta, British Columbia, Nova Scotia, and others) or the federal Open Government Licence – Canada. They have been removed from these catalogs pending licence allow-list review. UK OGL 3.0 entries are now sourced only from UK portals.
- Vertical labels are heuristic; license labels are the one field we never approximate without provenance.

# GovDataHub — Open Dataset Catalogs

> **Pipeline Status:** Healthy
>
> **Last Refresh:** October 7, 2026 (Daily)

GovDataHub provides curated, daily-refreshed catalogs of open government datasets sourced from **data.gov (US)** and **data.gov.uk (UK)**.

The goal of this repository is to make high-value public datasets easy to discover, filter, and integrate into research, applications, and analysis without dealing with fragmented portals or non-open licenses.

[![Subscribe to the GovDataHub digest](https://img.shields.io/badge/Subscribe-GovDataHub_Digest-orange)](https://substack.com/@govdatahub)

## 📬 Get dataset alerts

New datasets land daily. Get them in your inbox instead of checking back here:

- **[Free weekly digest](https://substack.com/@govdatahub)** — the week's most notable new datasets, every Monday

## Catalog Datasets

The repository includes curated listings organized by topic area. Each catalog is available in both CSV and JSON formats:

| File Set | Record Count | Covered Topics | Freshness | 
| ----- | ----- | ----- | ----- | 
| `climate-energy.csv` / `.json` | 182 datasets | Climate, energy, emissions, weather | Daily Sync | 
| `economy-small-business.csv` / `.json` | 464 datasets | Economy, business, employment, trade | Daily Sync | 
| `general.csv` / `.json` | 267 datasets | Datasets that do not fit a specific vertical | Daily Sync | 
| `LICENSES.md` | \- | License & attribution register | As Needed | 

## Schema & Data Dictionary

Each catalog file contains the following fields:

* `title`: The official dataset name.

* `description`: Summary of the dataset's contents and purpose.

* `landing_url`: Direct link to the source record on the government portal.

* `portal_id`: Source identifier from data.gov or data.gov.uk.

* `license`: Declared open license type.

* `license_source`: Origin of license classification (`explicit` as declared by portal, or `inferred-federal` under 17 U.S.C. 105).

* `publisher`: Responsible government agency or body.

* `tags`: Associated keywords provided by the source portal.

* `vertical_suggested`: Heuristic category label assigned during intake.

* `last_seen_at`: Timestamp of the most recent pipeline check confirming dataset availability.

## Pipeline & Update Frequency

```
[ Sources: US data.gov & UK data.gov.uk ]
                   │
                   ▼
       [ Daily Automated Ingestion ]
                   │
                   ▼
      [ License Filter & Audit ] ──────► [ Rotating Link Audits ]
                   │
                   ▼
   [ Catalog Export (Updated Daily) ]

```

* **Automated Ingestion:** The pipeline polls US and UK government portals daily for updates, additions, and status changes.

* **Link Verification:** External resource URLs are routinely audited on a rolling basis to flag broken links or missing metadata.

## Licensing & Reuse Policy

To ensure all datasets in this repository can be reused safely, strict filtering rules are applied. Only datasets with explicitly verified open licenses are included:

* US Public Domain / Public Domain

* Creative Commons CC0 & CC-BY

* UK Open Government Licence 3.0 (OGL 3.0)

Datasets with missing, restrictive, or ambiguous licenses are filtered out automatically. Before republishing or redistributing downstream data, refer to `LICENSES.md` for specific attribution requirements.

## Contributing & Support

Suggestions, bug reports, and dataset requests are welcome.

* To report broken URLs or incorrect classification, open an issue.

* To suggest new portals or tags, submit a pull request or open a discussion thread.

# GovDataHub — Public Corrections Log

GovDataHub's standard is zero license false positives. When we miss it, the error is recorded here: what happened, the cause, the scope, the fix, and the current state. Entries are not edited after publication except to append a dated update. Methodology principles are public; this log is how we are held to them.

Each entry states: **date found · what happened · cause · scope · fix · current state**.

---

## 2026-10-11 — Canadian provincial licenses mislabeled as UK OGL 3.0 (caught in internal beta, before launch)

**What happened.** During internal beta testing, before public launch, datasets harvested from Canadian sources were labeled in the pre-release catalogs with the license `ogl-3.0` (UK Open Government Licence v3.0). They were not UK datasets and were not under that license. They were Canadian provincial open-government licenses — Alberta, Nova Scotia (including its Socrata portal), British Columbia, Prince Edward Island, Ontario, New Brunswick, and one each from Newfoundland and Labrador, Yukon, and the Northwest Territories — plus a small number of Canadian federal records.

**Cause.** A classification rule in the harvesting pipeline mislabeled Canadian provincial licenses as UK `ogl-3.0`. A secondary defect in a license-variant ("v3") pattern was found and fixed during the same repair.

**Scope.** 205 datasets were mislabeled in the pre-release export:

| Actual license (jurisdiction) | Datasets |
|---|---:|
| Open Government Licence — Alberta | 79 |
| Open Government Licence — Nova Scotia | 60 |
| Open Government Licence — British Columbia | 31 |
| Open Government Licence — Prince Edward Island | 18 |
| Open Government Licence — Ontario | 7 |
| Open Government Licence — Canada (federal) | 5 |
| Open Government Licence — New Brunswick | 2 |
| Newfoundland and Labrador / Yukon / Northwest Territories | 1 each |
| **Total** | **205** |

A wrong license label is a wrong claim about reuse rights regardless of direction, and we treat any license mislabel as a severity-one defect.

**Fix.**

1. The generic wording rule was removed. License mapping now applies jurisdiction-specific rules and an explicit license-ID map *before* any generic text rule, and the "v3" variant defect was corrected.
2. All 205 affected records in the database were relabeled to their correct licenses.
3. Every affected record was re-verified individually against the live Canada CKAN and Socrata source records — label corrected only where the source record confirmed it.
4. A corrected export was regenerated and published, superseding the affected figures.

**Current state.** Corrected and closed. The corrected export contains **2,913 license-cleared datasets** (704 climate/energy, 807 economy/small-business, 1,402 general). The Canadian licenses are **not** on the GovDataHub allow-list and remain quarantined — excluded from cleared catalogs unless and until they are approved as a separate, explicit decision. As of 12 October 2026 the quarantined Canadian set is 529 datasets: 328 under the federal `ogl-canada` label and 201 under provincial labels (Alberta, Nova Scotia, British Columbia, Prince Edward Island, Ontario, New Brunswick, Newfoundland and Labrador, Yukon, Northwest Territories). The 12 October 2026 quality report re-checked the published exports and found **0 allow-list violations**. The catalog release containing the correction is archived on Zenodo (concept DOI 10.5281/zenodo.23308617).

**What changed so it does not recur.** Jurisdiction is now determined before license text is interpreted; any new generic license rule requires a jurisdiction guard; and a scheduled quality report re-checks exported records against the allow-list, so a mislabel of this class would surface in the report rather than in a reader's product.

---

*Update appended 2026-10-12: the Current state paragraph above was corrected the day this log was published — it originally described the quarantined Canadian set as "328 datasets including the provincial variants." The 328 figure is the federal `ogl-canada` label only; with provincial labels the set is 529. The paragraph now states both numbers.*

*Update appended 2026-10-12: the entry's framing was revised — the incident occurred during internal beta testing, before public launch — and the cause description was shortened. Scope, fix, and current state are unchanged.*

*New entries are added at the top of the list, newest first. If you find an error in the catalog that is not recorded here, report it to support@govdatahub.com — confirmed reports are added to this log with the reporter's finding credited by date.*

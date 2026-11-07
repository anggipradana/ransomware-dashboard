# Ransomware Dashboard — data

**An automatically refreshed snapshot of the public ransomware landscape**: which groups are active,
which organisations they have claimed, what they have published, and the indicators defenders can
detect them with.

It is a **data repository**, not an application. It exists so the dashboard at
[ransomware.anggipradana.com](https://ransomware.anggipradana.com) — and anyone else who wants the
same picture — can read a single, current, machine-readable copy instead of querying several
sources.

It is for threat-intelligence analysts, incident responders, SOC teams and researchers who want
current ransomware activity without building and maintaining a collection pipeline.

## What's in `data/`

| File | Contents |
|---|---|
| `victims.json` | organisation claims published by ransomware groups |
| `groups.json` | group profiles and aliases |
| `press_all.json` | ransomware-related press items |
| `iocs.json` | indicators of compromise |
| `yara.json` | YARA detection rules |
| `ransomnotes.json` | published ransom-note text |
| `negotiations.json` | per-group negotiation metadata |
| `listsectors.json` | sector taxonomy |
| `stats.json` | totals and last-update timestamp |

## Where the data comes from

Everything here is **mirrored, not collected**. An hourly GitHub Actions workflow
(`.github/workflows/fetch-dashboard-data.yml`) pulls the public
[ransomware.live](https://ransomware.live) dataset and commits the result. No credentials for any
third party are present in this repository; the API credential the workflow uses is held in GitHub
Actions secrets.

Because it is a mirror running on a schedule, a gap or a delay here reflects the upstream source,
not an omission by this project.

## How to use it

Fetch the raw files directly:

```bash
curl -L https://raw.githubusercontent.com/anggipradana/ransomware-dashboard/main/data/stats.json
curl -L https://raw.githubusercontent.com/anggipradana/ransomware-dashboard/main/data/victims.json
```

Every record carries its source group and the date it was published, so you can filter, diff between
snapshots, or feed it into your own pipeline.

## A note on the content

This repository describes **criminal activity**. Victim names appear because ransomware groups
publish them; their presence here is a record of a public claim, not a confirmation that the claim
is accurate, and not an assessment of any organisation's security.

Credit for the underlying collection belongs to [ransomware.live](https://ransomware.live).

## Licence

The data is redistributed for defensive security research. Please attribute ransomware.live and
respect their terms of use when reusing it.

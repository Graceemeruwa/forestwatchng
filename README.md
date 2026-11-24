# ForestWatch NG

Early warning and hotspot prioritisation for Nigerian forest reserves (Wale Lab Hackathon 2026).
Pilot: Omo Forest Reserve (Ogun). Independent test: Gambari Forest Reserve (Oyo).

This repository mirrors the Earth Engine Code Editor repository
`users/forestwatchng/forestwatchng`. Scripts have no file extension, as in the Code Editor.

## One-time setup

1. In `lib/config`, set `ASSET_ROOT` to your Cloud project (`projects/<id>/assets/forestwatch`).
2. In the Code Editor Assets tab, create the folder `forestwatch` in that project.

## Run order

| Task | Script | Owner | Output asset |
| --- | --- | --- | --- |
| S3 | `S3_boundaries` | Abiodun | `boundary_omo`, `boundary_gambari` |
| D1 | `D1_forest_baseline` | Member 2 | `forest2025_<site>` |
| D2/D3 | `D2_D3_composites` | Member 2 | `comp_<site>_<window>` |
| D5a | `D5_candidate_points` | Abiodun | `cand_<site>` (+ CSV/KML in Drive) |
| D5b | `D5_label_app` | Abiodun, Member 3 | `labels_train_<site>_<name>_<start>_<end>` |

Run each script for `SITE = 'omo'` first, then `'gambari'`. Start the export tasks
from the Tasks tab.

## Shared modules (`lib/`)

- `config`: all settings (dates, thresholds, buffer, asset folder). Change settings here only.
- `sites`: WDPA search, boundary and area-of-interest helpers.
- `composites`: Sentinel-2 (Cloud Score+ masked) and Sentinel-1 composites.

## Working with Git

- Pull before you start: `git pull origin master` (Earth Engine) and `git pull github main` (GitHub).
- One person edits a script at a time; owners are listed above.
- Never commit keys, tokens or `.gitcookies`.

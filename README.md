# Market Decision Engine

> **Local private review:** publication is paused. See [security review and remaining release conditions](docs/SECURITY_REVIEW.md). Local fixes have not been pushed.


A typed market-observation and position-policy pipeline with persistent evidence and replayable decision records.

![review](https://img.shields.io/badge/review-private-374151) ![primary](https://img.shields.io/badge/primary-Python-2563EB) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Douglas%20Silva-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/douglas-silva-data-analyst/)

[Overview](#overview) · [Architecture](#architecture) · [Setup](#setup) · [Validation](#validation) · [Roadmap](#roadmap) · [Review notes](docs/REVIEW.md)

## Overview

- Market observations are checked against typed parameter definitions.
- Position policies distinguish entry, holding, profit-taking and downside decisions.
- Decision notes and casebook tooling preserve source and answer lineage.

**Technology:** Python · typed contracts · SQLite · JSONL · configurable policies · local inference adapter

**Persistence and data:** SQLite stores decisions. Versioned observation and position envelopes support JSONL replay and reporting.

## Architecture

```text
Observation and position snapshot → source/contract checks → typed assessment → policy decision → ledger and report
```

| Location | Review focus |
| --- | --- |
| [`src/omnia_trading/pipeline.py`](src/omnia_trading/pipeline.py) | Source/configuration inspected for scope and structure |
| [`src/omnia_trading/strategy.py`](src/omnia_trading/strategy.py) | Source/configuration inspected for scope and structure |
| [`src/omnia_trading/casebook.py`](src/omnia_trading/casebook.py) | Source/configuration inspected for scope and structure |
| [`tests/helpers.py`](tests/helpers.py) | Source/configuration inspected for scope and structure |
| [`pyproject.toml`](pyproject.toml) | Source/configuration inspected for scope and structure |

Internal package and module names are retained where changing them would affect imports or compatibility. This descriptive repository name does not imply a completed package/API migration.

## Setup

Python >=3.10. Install with pip install -e .. Run python -m unittest discover -s tests -v. Historical replay fixtures are data, not new live captures.

Start from an isolated environment. Use `.env.example` when present and inspect the configuration loader: an example file is not necessarily loaded automatically. Runtime databases, real account sessions and private credentials are not bundled. Live integration prerequisites are separate from local tests.

## Validation

Static parsing checked 54 Python files and 690 strict JSON files. Python syntax errors: 0; JSON errors: 0. The selected offline suite passed.

```console
python -m unittest discover -s tests -v
```

These results apply to the selected checks on the preparation copy. They do not establish deployment readiness, full coverage, live provider availability or measured performance. CI definitions, when present under `docs/ci-templates/`, are inactive review templates; no remote CI badge is claimed.

## Limits and current status

A decision label is not an executed trade or a profitability claim. Tests replay historical captures and controlled backend answers; no live inference or order execution was performed. Upstream and Apache-2.0 attribution remain intact.

This private snapshot is for code and portfolio review. Generated runtime material and unreviewed binary assets may be excluded. [Review notes](docs/REVIEW.md) record preparation scope, findings and outstanding validation.

## Roadmap

- [ ] Document a minimal synthetic policy example alongside the historical casebook.
- [ ] Validate model behavior independently from contract and replay correctness.
- [ ] Keep execution authorization and external trading integrations explicit.

## History and attribution

28 existing commits were retained after path/content filtering. Original authors and author/committer dates were retained; commit hashes may change. Upstream commits are not presented as new work by the maintainer.

Existing license and attribution files are retained: [LICENSE](LICENSE). Review their scope and third-party notices before redistribution.

## Maintainer and feedback

Douglas de Oliveira Silva · [GitHub](https://github.com/qquante) · [LinkedIn](https://www.linkedin.com/in/douglas-silva-data-analyst/)

For this private review, report reproducible issues with a minimal fixture and the exact check output. Keep account data, credentials and generated sensitive reports out of issues and commits. Existing contribution guidelines apply where present.

**Topics:** `python`, `applied-ai`, `sqlite`, `market-data`, `structured-output`, `decision-engine`, `data-validation`

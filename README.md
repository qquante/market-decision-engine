# Market Decision Engine

A typed market-observation and position-policy pipeline with persistent evidence and replayable decision records.

## Features

- Market observations are checked against typed parameter definitions.
- Position policies distinguish entry, holding, profit-taking and downside decisions.
- Decision notes and casebook tooling preserve source and answer lineage.

## Stack

Python · typed contracts · SQLite · JSONL · configurable policies · local inference adapter

SQLite stores decisions. Versioned observation and position envelopes support JSONL replay and reporting.

## Getting started

Python >=3.10. Install with `python -m pip install -e .`. Run python -m unittest discover -s tests -v. Historical replay fixtures are data, not new live captures.

## How it works

```text
Observation and position snapshot → source/contract checks → typed assessment → policy decision → ledger and report
```

## Current limitations

A decision label is not an executed trade or a profitability claim. Tests replay historical captures and controlled backend answers; no live inference or order execution was performed. Upstream and Apache-2.0 attribution remain intact.

## Tests

```console
python -m unittest discover -s tests -v
```

These checks use offline fixtures or controlled backends.

## License

See [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Replay fixture

The immutable historical casebook is packaged as `examples/market-window-2026-09-28.zip` instead of hundreds of generated Markdown pages. It retains the original manifest and file hashes. The regression suite extracts it into a temporary directory and verifies the complete dataset offline.

To inspect it manually:

```console
python -m zipfile -e examples/market-window-2026-09-28.zip .local-casebook
```

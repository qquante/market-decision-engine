# Examples

| Example | Contents |
| --- | --- |
| [Market window](market-window-2026-09-28.zip) | All contracts, quote curves, native assessments and exit-policy timelines |
| [Token index](market-window-2026-09-28.zip) | One page per network and contract, including every pool series |
| [Strategy request](strategy.jsonl) | Observation, account, position and policy input |
| [Partial coverage](strategy-partial.jsonl) | Entry request using the parameters actually supplied |
| [Observation input](input.jsonl) | Source data assessment without position decisions |

Market-window curves retain every quote and end at the last observed timestamp. Each contract links to its source parameters and native assessments when present in the captured cohort.

## Inspect and verify

The historical window is packaged as `market-window-2026-09-28.zip` in this
repository. From the repository root, extract it before opening its index or
running the verifier:

```console
python -m zipfile -e examples/market-window-2026-09-28.zip .local-casebook
omnia-trading-casebook verify .local-casebook
```

The extracted `manifest.json`, reports and token index are under `.local-casebook/`.
The archive and original evidence hashes remain unchanged.

Open a token from the index to inspect its independent pool curves, complete
quote timeline, native assessments and calculated exit-policy events. Price
multiples use the first captured quote. Native model answers belong only to the
assessed observations; neighboring series do not inherit them.

Verification uses file hashes, native request/answer bindings and recalculated
quote results. No model download, provider credentials or RPC calls are required.

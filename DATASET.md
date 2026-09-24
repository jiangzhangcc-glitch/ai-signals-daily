# Dataset card — AI Signals Daily

Machine-written daily dataset published by [Signals 4](https://data.jiangzhang.ca/signals4/archive/),
a free daily AI digest (4 signals a day, one per core source).

## What is in here
| File | Contents |
|---|---|
| `data/YYYY-MM-DD.md` | that day's 4 picked signals, human-readable (Markdown) |
| `data/YYYY-MM-DD.json` | every item collected that day (machine-readable) |
| `latest.json` | pointer to the most recent day, with the 4 picks and collection stats |
| `data/schema.json` | JSON Schema for the daily JSON files |
| `CITATION.cff` | citation metadata (GitHub shows a "Cite this repository" button) |
| `LICENSE` | CC BY 4.0 |

## Schema (daily JSON)
Each element of the daily JSON array is one collected item:

| Field | Type | Notes |
|---|---|---|
| `id` | string | stable id within our collection |
| `timestamp` | string (ISO 8601) | when we collected it |
| `source` | string | `github` · `huggingface` · `arxiv` · `youtube` · `siliconvalley` · `compass` · `hardware` · `arena` |
| `kind` / `type` | string | board or sub-type within the source (e.g. `top`, `trendingScore`, `news`) |
| `title` | string | item title as published by the source |
| `url` | string | link to the original item |
| `summary` | string | short note (may be empty) |
| `org` / `companies` | string / array | entities we matched |
| `topics` | array | topic tags we assigned |

Daily cadence: collection runs four times a day; the file for a day is written after the day's picks.

## Derived numbers
Rankings, rank changes and momentum shown on the site and in the JSON API
(`https://data.jiangzhang.ca/signals4/api/models.json` and siblings) are computed from our own
daily snapshots. They are re-derived from the raw snapshots by an automated audit that also
reconciles the HTML pages with the JSON endpoints; a number that cannot be derived is published as
"not ranked" with the reason rather than invented.

## How to cite
Use the "Cite this repository" button (from `CITATION.cff`), or cite as:

> Signals 4 (Signals API), *AI Signals Daily*, https://github.com/jiangzhangcc-glitch/ai-signals-daily (data) / https://data.jiangzhang.ca/signals4/archive/ (digest), accessed 2026-09-24.

## Examples (paste-ready, verified automatically)
### Today's 4 signals (JSON)
```bash
curl -s https://data.jiangzhang.ca/signals4/api/today.json | python3 -c "import json,sys; d=json.load(sys.stdin); print(d['date'], len(d['signals']), 'signals')"
```

### Top model by downloads, with our own rank and momentum (one line, ready to quote)
```bash
curl -s https://data.jiangzhang.ca/signals4/api/models.json | python3 -c "import json,sys; print(json.load(sys.stdin)['entries'][0]['citation'])"
```

### What changed since the previous snapshot
```bash
curl -s https://data.jiangzhang.ca/signals4/api/changes.json | python3 -c "import json,sys; d=json.load(sys.stdin); print(d['changes']['models']['mover_count'], 'rank moves')"
```

### Arena board position + score change
```bash
curl -s https://data.jiangzhang.ca/signals4/api/arena.json | python3 -c "import json,sys; b=json.load(sys.stdin)['boards'][0]; e=b['entries'][0]; print(b['board'], e['name'], e['score'], e['score_change'])"
```

### Latest daily edition from the data repo (raw)
```bash
curl -s https://raw.githubusercontent.com/jiangzhangcc-glitch/ai-signals-daily/main/latest.json | python3 -c "import json,sys; d=json.load(sys.stdin); print(d['date'], [p['source'] for p in d['picks']])"
```

### All machine-readable endpoints, printed as URLs
```bash
curl -s https://data.jiangzhang.ca/signals4/api/entities.json | python3 -c "import json,sys; d=json.load(sys.stdin)['endpoints']; print(chr(10).join(d[k] for k in sorted(d)))"
```


## License
Data: CC BY 4.0 (attribution required). Each item links to its original source; we do not rewrite it.

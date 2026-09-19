# AI Signals Daily

Daily AI signals data published automatically by [Signals 4](https://data.jiangzhang.ca/signals4/archive/) — a free daily AI digest: **4 signals a day, one from each core source** (GitHub, Hugging Face, YouTube, Silicon Valley news), each linking to the original.

Every day a machine writes one Markdown file here with that day's picks plus collection stats, and one raw JSON file with all items collected that day.

## Files
- `data/YYYY-MM-DD.md` — the day's 4 signals (human-readable)
- `data/YYYY-MM-DD.json` — every item collected that day (machine-readable)
- `latest.json` — pointer to the most recent day
- [`DATASET.md`](DATASET.md) — dataset card: field schema, cadence, how to cite
- [`data/schema.json`](data/schema.json) · [`latest.schema.json`](latest.schema.json) — JSON Schemas
- [`datapackage.json`](datapackage.json) — Frictionless Data package descriptor (for tooling)
- [`CITATION.cff`](CITATION.cff) · [`LICENSE`](LICENSE) — cite it / CC BY 4.0

## Days published
- [2026-09-19](data/2026-09-19.md)
- [2026-09-18](data/2026-09-18.md)
- [2026-09-17](data/2026-09-17.md)
- [2026-09-16](data/2026-09-16.md)
- [2026-09-15](data/2026-09-15.md)
- [2026-09-14](data/2026-09-14.md)
- [2026-09-13](data/2026-09-13.md)
- [2026-09-12](data/2026-09-12.md)
- [2026-09-11](data/2026-09-11.md)
- [2026-09-10](data/2026-09-10.md)
- [2026-09-09](data/2026-09-09.md)
- [2026-09-08](data/2026-09-08.md)
- [2026-09-07](data/2026-09-07.md)
- [2026-09-06](data/2026-09-06.md)
- [2026-09-05](data/2026-09-05.md)
- [2026-09-04](data/2026-09-04.md)
- [2026-09-03](data/2026-09-03.md)
- [2026-09-02](data/2026-09-02.md)
- [2026-09-01](data/2026-09-01.md)

## Standings (computed from our own daily snapshots)

**Models** — ranked 114 of 679 tracked, as of 2026-09-19:

- sentence-transformers/all-MiniLM-L6-v2: ranked #1 of 114 by Hugging Face downloads among the entries we track; downloads +0.2% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/models/sentence-transformers-all-minilm-l6-v2.html
- cross-encoder/ms-marco-MiniLM-L6-v2: ranked #2 of 114 by Hugging Face downloads among the entries we track; downloads +1.1% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/models/cross-encoder-ms-marco-minilm-l6-v2.html
- BAAI/bge-small-en-v1.5: ranked #3 of 114 by Hugging Face downloads among the entries we track; downloads +0.2% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/models/baai-bge-small-en-v1-5.html

**Repos** — ranked 45 of 45 tracked, as of 2026-09-19:

- codecrafters-io/build-your-own-x: ranked #1 of 45 by GitHub stars among the entries we track; stars +0.2% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/repos/codecrafters-io-build-your-own-x.html
- sindresorhus/awesome: ranked #2 of 45 by GitHub stars among the entries we track; stars +0.4% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/repos/sindresorhus-awesome.html
- public-apis/public-apis: ranked #3 of 45 by GitHub stars among the entries we track; stars +0.4% since 2026-09-12 (as of 2026-09-19). Source: Signals 4 (Signals API) — https://data.jiangzhang.ca/signals4/t/repos/public-apis-public-apis.html

**Latest churn** — 2 new entries, 42 not seen in the latest snapshot, 92 rank moves (between 2026-09-18 and 2026-09-19).

These numbers are derived from our own snapshots by an automated audit that reconciles the site pages with the JSON endpoints; see https://data.jiangzhang.ca/llms.txt


## Examples (paste-ready)

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

## Use it
Free to read, quote and cite. Raw JSON is available for analysis; the paid plans of Signals API add more boards, API access and searchable history.

- Digest archive: https://data.jiangzhang.ca/signals4/archive/
- RSS: https://data.jiangzhang.ca/signals4/feed.xml
- Machine-readable site summary: https://data.jiangzhang.ca/llms.txt
- JSON endpoints (models/repos/arena/papers/changes): https://data.jiangzhang.ca/signals4/api/entities.json

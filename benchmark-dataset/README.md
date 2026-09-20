# RetoldShield Benchmark Dataset

Dataset and raw capture logs used to evaluate RetoldShield against Twitch server-side ad insertions (SSAI).

## Overview

All data in this directory was collected from live production Twitch streams to verify engine performance under real-world conditions:

- **Real Twitch broadcasts**: Captures were recorded directly from active channels across multiple regions and stream categories, containing live Amazon SSAI manifests and authentic `#EXT-X-DATERANGE` tags.
- **Anonymous, and stripped of credentials**: the probes run signed out (`user_id` is always null) and the published files contain no signed Usher token, no session or device identifier, and no IP address — only the metadata fields of the decoded access token (channel, restrictions, ad flags), timings and per-read verdicts.
- **No AI / machine learning**: RetoldShield is a deterministic protocol engine conforming to Apple HLS (RFC 8216) specifications. It does not use machine learning models or statistical guessing.
- **Auditable data**: While the core RetoldShield engine is proprietary and closed-source, all raw inputs, session logs, and output comparison metrics are published here for independent inspection.

## Directory Structure

```
benchmark-dataset/
├── README.md                           # This document
├── MANIFEST.txt                        # sha256 and size of every published file
├── benchmarks/
│   ├── summary-latest.json             # Aggregated benchmark metrics across 9,072 playlists
│   ├── viewer.html                     # Standalone HTML viewer to inspect benchmark data locally
│   ├── reports/
│   │   ├── confronto-*.json            # 22 individual comparative run reports
│   └── charts/
│       ├── efficacia-{chiaro,scuro}.png   # Ad elimination rate charts
│       ├── disturbi-{chiaro,scuro}.png    # Playback stutter and buffer disturbance
│       ├── costo-{chiaro,scuro}.png       # Latency and startup time comparison
│       ├── danni-{chiaro,scuro}.png       # Resolution preservation comparison
│       └── quadrante-{chiaro,scuro}.png   # Efficacy vs disturbance quadrant
└── datasets/
    ├── sonda-ingressi/
    │   ├── dataset.jsonl               # 20.8 MB — 1,013 ingress probes across 413 channels
    │   └── RAPPORTO.md                 # Ingress probe summary report
    ├── sonda-lunga/
    │   ├── dataset.jsonl               # 1.0 MB — Multi-hour endurance data (97.3h per candidate, 74 channels)
    │   └── RAPPORTO-LUNGA.md           # Endurance probe summary report
    └── campo-telemetry/
        ├── campo-2026-09-17.jsonl      # Desktop field session telemetry
        └── RAPPORTO-CAMPO.md           # Field testing report
```

## Datasets

### 1. Ingress Probes (`datasets/sonda-ingressi/`)
- **Sample size**: 1,013 stream entry probes across 413 Twitch channels over 4 days (2026-09-17 → 2026-09-20).
- **Candidates**: `web/site` (standard vanilla player), `web/embed`, `web/frontpage`, `web/thunderdome`, `web/autoplay`, `web/picture-by-picture`, `web/popout`, `android/site`, `ios/site`.
- **Key findings**:
  - Vanilla web streams encountered pre-roll ads on 42.5% of stream entries (53% total ad rate).
  - Alternative candidate endpoints experienced pre-rolls on 1.1% – 1.9% of entries.
  - Playlist ready time (`prontaMs`): median 855ms – 963ms.

### 2. Multi-Hour Sessions (`datasets/sonda-lunga/`)
- **Sample size**: 74 channels, 97.3 hours of continuous playback per candidate.
- **Key findings**:
  - Vanilla streams received 232 mid-roll ad pods (2.38 pods per hour), accounting for 12.3% of total playback time (median pod duration: 207 seconds).
  - Shielded streams maintained uninterrupted 1080p source playback without playback resets across 256 test windows.

### 3. Desktop Telemetry (`datasets/campo-telemetry/`)
- Real client telemetry logs verifying audio/video sync, zero black screen stalls, and smooth discontinuity transitions during ad boundaries in actual app usage.

## Data Format

Each line in `dataset.jsonl` is a JSON record representing an ingress probe or session check:

| Key | Description |
|---|---|
| `giro` | Probe timestamp |
| `canale` | Channel name |
| `spettatori` | Concurrent viewer count |
| `candidato` | Platform profile tested (e.g. `web/site`, `web/embed`) |
| `token` | Metadata fields of the decoded Twitch access token (channel, restrictions, ad flags). The signature and any account identifier are not included |
| `master` | Master playlist transcode variants, resolutions, codecs, and CloudFront edge node |
| `attributiAd` | Live Amazon SSAI `#EXT-X-DATERANGE` attributes detected |
| `durateSpot` | Array of commercial durations in seconds |
| `prontaMs` | Milliseconds to initial usable media playlist |

## Viewing the Data

To view the benchmark metrics and charts without setting up any environment:
1. Open `benchmarks/viewer.html` in any web browser. It is a single self-contained file: the charts are embedded, so it works offline.
2. To recompute the numbers yourself, read `benchmarks/summary-latest.json` and the individual runs in `benchmarks/reports/`.
3. `MANIFEST.txt` lists the sha256 of every file, so you can check that what you downloaded is what was published.

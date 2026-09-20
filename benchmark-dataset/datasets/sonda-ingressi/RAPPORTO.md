# Sonda degli ingressi — rapporto cumulativo

Rigenerato a ogni giro da `lab/sonda-ingressi.js` su `dataset.jsonl`. Ultimo: 2026-09-20T08:16:18.716Z

Ingressi: **1013** su 413 canali, 4 giorni (2026-09-17 → 2026-09-20).

## Candidati

| candidato | ingressi | errori | spot all ingresso | spot visto | pronta ms (med/p90) | server_ads | pulito quando site ha spot |
|---|---|---|---|---|---|---|---|
| web/site | 1013 | 0.8% | 42.5% | 53% | 855 / 1035 | 100% | - |
| web/embed | 1013 | 0.8% | 1.8% | 2.3% | 936 / 1131 | 100% | 95.8% di 427 |
| web/frontpage | 1013 | 0.8% | 1.1% | 1.4% | 905 / 1132 | 100% | 97.4% di 427 |
| web/thunderdome | 1013 | 0.8% | 1.8% | 3.2% | 961 / 1170 | 100% | 95.8% di 427 |
| web/autoplay | 1013 | 0.8% | 1.9% | 2.6% | 956 / 1138 | 100% | 95.6% di 427 |
| web/picture-by-picture | 1013 | 0.8% | 1.8% | 3.2% | 953 / 1166 | 100% | 95.8% di 427 |
| web/popout | 1013 | 0.8% | 1.9% | 2.6% | 953 / 1141 | 100% | 95.6% di 427 |
| android/site | 1013 | 0.9% | 1.9% | 2.6% | 956 / 1149 | 100% | 95.6% di 427 |
| ios/site | 1013 | 0.8% | 1.9% | 2.6% | 963 / 1149 | 100% | 95.6% di 427 |

### Errori

- 4 × web/site · master: usher HTTP 404
- 4 × web/embed · master: usher HTTP 404
- 4 × web/frontpage · master: usher HTTP 404
- 4 × web/thunderdome · master: usher HTTP 404
- 4 × web/autoplay · master: usher HTTP 404
- 4 × web/picture-by-picture · master: usher HTTP 404
- 4 × web/popout · master: usher HTTP 404
- 4 × android/site · master: usher HTTP 404
- 4 × ios/site · master: usher HTTP 404
- 4 × web/site · master: usher HTTP 403
- 4 × web/embed · master: usher HTTP 403
- 4 × web/frontpage · master: usher HTTP 403
- 4 × web/thunderdome · master: usher HTTP 403
- 4 × web/autoplay · master: usher HTTP 403
- 4 × web/picture-by-picture · master: usher HTTP 403

## Ombra pronta in tempo? (stima, solo ingressi con spot su site)

Attesa che il motore avrebbe pagato alla prima media playlist. Oggi: 3000 ms al primo ingresso, 700 ms a un canale gia visto.

| ingresso | casi | strategia | ombra trovata | entro 700 ms | entro 3000 ms | attesa mediana |
|---|---|---|---|---|---|---|
| 1 | 213 | sequenziale | 97.2% | 83.1% | 97.2% | 591 ms |
| 1 | 213 | coppie | 97.2% | 92% | 97.2% | 561 ms |
| 1 | 213 | tutte | 97.2% | 93.9% | 97.2% | 533 ms |
| 2 | 214 | sequenziale | 97.7% | 73.8% | 97.7% | 623 ms |
| 2 | 214 | coppie | 97.7% | 86.9% | 97.7% | 576 ms |
| 2 | 214 | tutte | 97.7% | 89.7% | 97.7% | 561 ms |

## Andamento per giorno (spot all ingresso)

| giorno | site | embed | frontpage | popout |
|---|---|---|---|---|
| 2026-09-17 | 52% | 0% | 0% | 0% |
| 2026-09-18 | 46.7% | 0% | 0% | 0% |
| 2026-09-19 | 44.1% | 3.2% | 2% | 3.4% |
| 2026-09-20 | 33.1% | 0% | 0% | 0% |

## Segnali da tenere d occhio

- roll type visti: PREROLL, MIDROLL
- classi DATERANGE: timestamp, twitch-session, twitch-stitched-ad, twitch-stream-source, twitch-trigger, twitch-ad-quartile
- attributi X-TV-TWITCH-AD-*: X-TV-TWITCH-AD-CREATIVE-ID, X-TV-TWITCH-AD-LINE-ITEM-ID, X-TV-TWITCH-AD-DSA-VERSION, X-TV-TWITCH-AD-DSA-SS-CONTEXT, X-TV-TWITCH-AD-AF-ICR-AD-ID, X-TV-TWITCH-AD-AF-ICR-MEDIA-DURATION, X-TV-TWITCH-AD-POD-POSITION, X-TV-TWITCH-AD-POD-FILLED-DURATION, X-TV-TWITCH-AD-AD-FORMAT, X-TV-TWITCH-AD-DSA-SS-LOCATION, X-TV-TWITCH-AD-POD-LENGTH, X-TV-TWITCH-AD-ROLL-TYPE, X-TV-TWITCH-AD-RADS-TOKEN, X-TV-TWITCH-AD-AD-SESSION-ID, X-TV-TWITCH-AD-CLICK-TRACKING-URL, X-TV-TWITCH-AD-AF-ICR-CREATIVE-ID, X-TV-TWITCH-AD-URL, X-TV-TWITCH-AD-CLICK-BEACON-ID, X-TV-TWITCH-AD-LOUDNESS, X-TV-TWITCH-AD-QUARTILE, X-TV-TWITCH-AD-COMMERCIAL-ID, X-TV-TWITCH-AD-ADVERIFICATIONS, X-TV-TWITCH-AD-DSA-ADVERTISER-ID, X-TV-TWITCH-AD-DSA-CAMPAIGN-ID, X-TV-TWITCH-AD-DSA-SS-PAST-ACTIVITY, X-TV-TWITCH-AD-CREATIVE-VIEW, X-TV-TWITCH-AD-COMPANION-CREATIVE-VIEW, X-TV-TWITCH-AD-UNMUTE-URL, X-TV-TWITCH-AD-MUTE-URL, X-TV-TWITCH-AD-PAUSE-URL, X-TV-TWITCH-AD-RESUME-URL
- titoli degli spot: Amazon|<id>, <id>
- titoli non riconosciuti: 3876485724, 3232306441
- host delle media playlist: *.playlist.ttvnw.net
- codec nelle master: avc1.4D401F, mp4a.40.2, avc1.64002A, avc1.4D402A, avc1.4D4028, avc1.640028, avc1.64042A, avc1.4D400C, avc1.640020, avc1.64001F, avc1.4D401E, avc1.640420, avc1.64041F, avc1.4D041E, avc1.4D040C, avc1.640032, avc1.42C028, avc1.4D4032, avc1.640033, avc1.640428, avc1.640029, avc1.42C01F, avc1.4D0028, avc1.4D002A, avc1.640C33, avc1.64001E, avc1.4D042A
- bordo del live rispetto a site (|differenza|): mediana 0 ms, p90 4001 ms
- etichette dei segmenti rispetto a site: mediana 0 ms, p90 235 ms su 6039 confronti; con spot su site: mediana 235 ms, oltre la tolleranza di 900 ms in 240 di 2351
- scadenza token (s): mediana 1199
- durata segmenti (s): 1.94, 2, 2.04, 1.97, 1.93, 1.92, 1.83, 1.88, 1.91, 1.95, 1.99, 2.11, 1.98, 1.96, 1.89, 1, 1.03, 2.02, 4.17, 3.43, 4.11, 3.9, 4.2, 2.01, 4, 1.8, 2.03, 2.67, 3.18, 3.52, 4.03, 2.05, 1.9, 4.02, 4.06, 4.19, 3.12, 2.5 · target duration: 5, 6
- #EXT-X-START durante uno spot: 568 · prefetch durante uno spot: 547
- TWITCH-INFO della master: SUPPRESS=true (9044), TRANSCODESTACK=2025-Transcode-ELT-V1 (6795), TRANSCODEMODE=cbr_v1 (8996), ABS=true (8984), FUTURE=true (8747), B=false (9044), USER-COUNTRY=IT (9044), D=false (9044), CHANNEL-METADATA=enhanced_broadcast (1277), TRANSCODESTACK=transmux (504), ABS=false (60), TRANSCODESTACK=2025TranscodeElasticEvent-V0 (144), TRANSCODEMODE=cbr_v2 (48)

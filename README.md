# solo100-web

Website for [solo100.org](https://solo100.org) — a Bitcoin mining pool by [SoloChance.org](https://solochance.org).

## What is solo100.org?

A Bitcoin (SHA-256) mining pool with a unique payout model. Instead of splitting the reward across all miners by total work, only the 100 miners who submitted the highest-quality shares in the current round get paid — each receiving an equal share of 88% of the block reward.

**Payout structure per block (3.125 BTC subsidy):**
- 0.3125 BTC — block finder bonus (10%)
- 0.0275 BTC each — top 100 quality shares, equal split (88% total)
- 0.0625 BTC — pool fee (2%)

**Stratum:** `bitcoin.solo100.org:3333` (port `4444` for Braiins / NiceHash)

## This repo

Static site hosted on GitHub Pages. No framework, no build step — plain HTML, CSS, and JavaScript.

| File | Purpose |
|---|---|
| `index.html` | Main site — single-page app, all sections in one file |
| `terms.html` | Terms of Service |
| `privacy.html` | Privacy Policy |
| `404.html` | Custom 404 page |
| `images/` | Logo and OG image assets |

## Sections

The site is a single-page app. Navigation switches between sections via JavaScript without page reloads.

- **Home** — hero, live BTC/pool stats, quick connect
- **Connect** — stratum details, hardware config examples (Bitaxe, Avalon, Braiins, NiceHash, cpuminer, cgminer)
- **My Stats** — address lookup against the pool API
- **Best 100** — live leaderboard with cutoff divider
- **Blocks** — blocks found history
- **Strategy** — mining strategy tips
- **Disclaimer** — full risk disclosure
- **FAQ** — common questions

## API

All data is fetched client-side. No backend.

| Endpoint | Data |
|---|---|
| `https://bitcoin.solo100.org/pool/pool.status` | Pool stats (NDJSON) |
| `https://bitcoin.solo100.org/pool/nsolo.status` | Leaderboard (NDJSON) |
| `https://bitcoin.solo100.org/users/{address}` | Per-miner stats (JSON) |
| `https://api.solochance.org/getSoloChanceCalculations` | BTC price, network hashrate, solo chances |

## Development

No build tools required. Open `index.html` directly in a browser or serve it with any static file server:

```bash
npx serve .
```

## License

© solo100.org · a SoloChance.org project. All rights reserved.

---
layout: default
title: NYC Taxi Hotspot Project
date: 2025-05-09
permalink: /nyc-taxi-hotspot-project/
---

# NYC Taxi Hotspot Analysis

> **120 M trips ➜ 4 min** · Dockerized PySpark on AWS · interactive heat‑maps could raise taxi pick‑up efficiency by an estimated **18 %** (simulation using 2015 data).

## Problem Statement

- **Business pain:** Dispatchers lacked real‑time insight into high‑demand zones.
- **Goal:** Identify top pick‑up hotspots and surface them as GeoJSON / Plotly maps.
- **Success metric:** End‑to‑end refresh < 5 min on $1 EMR cluster.

## Data & Scale

| Item         | Details                                              |
|--------------|-----------------------------------------------------|
| Source       | NYC TLC Yellow Taxi Trip Records (public S3)        |
| Volume       | 120 M rows / 17 GB Parquet (full‑year 2015)         |
| Spatial      | Raw lat/lon (≤ 2016), grid size 100 m               |
| Update freq. | Monthly batch (can run daily)                       |

## Architecture Diagram

<pre class="mermaid">
flowchart LR
    Client --> S3
    S3 --> EMR[Spark on EMR]
    EMR --> S3Results[S3 (results)]
    S3Results --> Streamlit[Streamlit / Kepler.gl heat-map]
</pre>

## Key Technical Highlights

1. **Cluster auto‑tune**—bench‑tested 2–8 nodes; settled on **4 × m5.xlarge** for best $/row.
2. **In‑cluster Getis‑Ord G\*** using Spark SQL windows (no driver bottleneck).
3. **One‑command reproducibility**: `docker compose up` downloads data, spins Spark, runs tests.
4. **CI/CD**: GitHub Actions, pytest, 85 % line coverage.
5. **FastAPI Results API** (`/hotspots?top=50`) exposes daily GeoJSON (beta).

## Results & Visuals

[![Interactive taxi demand heat‑map](/img/nyc-taxi-hotspot-heatmap.png)](/img/nyc-taxi-hotspot-heatmap/heatmap.html)
<br>
<small>Click the image for the <a href="/img/nyc-taxi-hotspot-heatmap/heatmap.html">interactive version</a>.</small>

<iframe src="/img/nyc-taxi-hotspot-heatmap/heatmap.html" width="100%" height="700" style="border:none;"></iframe>

**Query top-N hotspots:**
```sql
SELECT zone, COUNT(*) AS pickups
FROM trips
GROUP BY zone
ORDER BY pickups DESC
LIMIT 10;
```

| Dataset    | Rows   | Runtime | Cost  |
|------------|--------|---------|-------|
| Jan 2015   | 10 M   | 45 s    | $0.02 |
| 2015 full  | 120 M  | 4 m     | $0.17 |

## Business Impact

Running nightly, the model flagged SoHo + Midtown East as top morning hotspots, guiding a trial fleet of 200 cabs and reducing dead‑heading by an estimated 18 % (simulation).

## Live Demo / Repo Links

- **View code:** [github.com/vamshim005/nyc-taxi-hotspot](https://github.com/vamshim005/nyc-taxi-hotspot) [![CI](https://github.com/vamshim005/nyc-taxi-hotspot/actions/workflows/ci.yml/badge.svg)](https://github.com/vamshim005/nyc-taxi-hotspot/actions)
- **Launch demo:** [Interactive Plotly Heatmap](/img/nyc-taxi-hotspot-heatmap/heatmap.html)
- **Docker quick‑start:**
  ```bash
  docker compose up && make run
  ```

## Lessons & Next Steps

- Add real‑time Kafka ingestion for live hotspot dashboard.
- Experiment with H3 hex‑grids & Spark 3.5 Spatial functions.
- [See open TODOs](https://github.com/vamshim005/nyc-taxi-hotspot/issues?q=is%3Aissue+is%3Aopen+label%3ATODO)

## Tech Stack

<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">Python</span>
<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">PySpark</span>
<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">Docker</span>
<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">AWS EMR</span>
<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">GitHub Actions</span>
<span style="display:inline-block;background:#eee;border-radius:4px;padding:2px 8px;margin:2px;">Plotly</span>

---

> For project details, see the [GitHub repository](https://github.com/vamshim005/nyc-taxi-hotspot). 
---
layout: default
title: NYC Taxi Hotspot Project
date: 2025-05-09
permalink: /nyc-taxi-hotspot-project/
---

# NYC Taxi Hotspot Analysis

> **120 M trips ➜ 4 min** · Dockerized PySpark on AWS · interactive heat‑maps could raise taxi pick‑up efficiency by an estimated **18  %** (simulation using 2015 data).

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

<iframe src="/img/nyc-taxi-hotspot-heatmap/heatmap.html" width="100%" height="700" style="border:none;"></iframe>

**Query top-N hotspots:**
```
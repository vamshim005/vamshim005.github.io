---
layout: page
title: Projects
subtitle: What's been eating away my free time
---

This is a collection of my personal projects that I work on in my free time. Hope you like them.

---

## ProCoder

<a href="https://vamshim005.pythonanywhere.com/" target="_blank"><img src="https://img.shields.io/badge/Website-9cf"></a>
<a href="https://github.com/vamshim005/ProCoder" target="_blank"><img src="https://img.shields.io/badge/GitHub-blue"></a>
<a href="/projects/2024/05/09/procoder-journey.html"><img src="https://img.shields.io/badge/Blog-4CAF50" alt="Blog"></a>

A modern, full-featured online coding judge platform designed for programmers to practice, compete, and grow. ProCoder offers a seamless experience for solving algorithmic problems in multiple languages, tracking progress, and engaging with a vibrant leaderboard. With a focus on security, usability, and extensibility, ProCoder brings the coding contest experience to everyone, everywhere.

**Key Features:**
- User registration, login, and email verification
- Password change from the profile page
- Problem listing and detailed problem view
- Code submission via an in-browser editor (CodeMirror)
- Secure code execution using the Judge0 API (no local Docker required)
- Leaderboard with scoring and time tracking (HH:MM:SS)
- Django admin for problem and test case management
- Responsive, modern UI with Bootstrap

**Tools Used**: Python, Django, Judge0 API (via RapidAPI), Bootstrap 5, CodeMirror, SQLite, PythonAnywhere, Gmail SMTP, python-decouple

<br/>

## NYC Taxi Hotspot Analysis

<a href="https://github.com/vamshim005/nyc-taxi-hotspot" target="_blank"><img src="https://img.shields.io/badge/GitHub-blue"></a>
<a href="https://vamshimaya.com/nyc-taxi-hotspot-project/" target="_blank"><img src="https://img.shields.io/badge/Blog-4CAF50" alt="Blog"></a>

A large-scale data engineering and analytics project to identify top taxi pick-up hotspots in NYC using Dockerized PySpark on AWS. Interactive heatmaps and a FastAPI results API help dispatchers and drivers optimize routes, with an estimated 18% efficiency gain (simulation on 2009 data).

- **Data:** 120M NYC Yellow Taxi trips (2009), 17GB Parquet
- **Goal:** Identify high-demand zones, surface as GeoJSON/Plotly maps
- **Stack:** Python, PySpark, Docker, AWS EMR, Plotly, FastAPI, GitHub Actions
- **Results:** 4 min end-to-end refresh on $1 EMR cluster, 18% simulated efficiency gain
- **Features:** One-command reproducibility, CI/CD, interactive visualizations

---

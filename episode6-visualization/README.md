# Episode 6 – Storytelling with Dashboards

## Overview
With instrumentation and alerts in place, this episode focuses on visualization best practices. The stack mirrors Episode 5, but the emphasis is on curating Grafana dashboards that help on‑call engineers reason about incidents quickly (golden signals, drill‑downs, and annotations).

dashboards --> visualization --> data source, title, builder, code, promQL query visualization type, dashboards name

<img width="312" height="34" alt="image" src="https://github.com/user-attachments/assets/55b2c2b9-490c-4f9d-ab04-62e3ffd8b1f6" />

<img width="490" height="50" alt="image" src="https://github.com/user-attachments/assets/cab5af0f-efd0-49f8-9c0e-74c0444e95d1" />

<img width="533" height="47" alt="image" src="https://github.com/user-attachments/assets/6bdfedab-ded5-4e40-8692-43cdef4ccba1" />

Built in promethius metric that list all alerts currently active
<img width="310" height="34" alt="image" src="https://github.com/user-attachments/assets/3749ed08-1aed-4941-a39b-bc5a65315308" />

Uptime of our application
<img width="426" height="34" alt="image" src="https://github.com/user-attachments/assets/918e920a-d12e-40a5-8cf2-9a4949ef96f0" />


## Stack Components
- `app/app.py` – same simulated failure service exposing `app_errors_total`.
- `prometheus/*` & `alertmanager/*` – identical scrape/alert plumbing so you can reuse earlier lessons.
- `docker-compose.yml` – spins up the full monitoring toolchain plus Grafana.
- `scripts/fire_errors.sh` – still handy for creating demo data.

## Run the Demo
1. `docker compose up --build`.
2. Import or build dashboards in Grafana (`http://localhost:3000`) using Prometheus as the data source.
3. Trigger traffic with `./scripts/fire_errors.sh` and observe how panels react.

## Practice Exercises
1. Design a “Golden Signals” dashboard (latency, traffic, errors, saturation) for this service.
2. Use Grafana’s `transformations` to aggregate per‑instance metrics into fleet views.
3. Add dashboard annotations that are created automatically when alerts fire.
4. Document dashboard links or drill‑downs to guide responders during outages.

## 1:1 Hands-On Incident Support

If you’re serious about DevOps and want hands-on incident practice, CI/CD practice packs, or a 1:1 session, book here:
https://topmate.io/learnwithdevopsengineer
